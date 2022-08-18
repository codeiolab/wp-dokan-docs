# Start
- Autoload vendor files.
- [Define Constants](#define-constants)
- [Register Plugin Activation hook](#activation-hook)
- [Register Plugin Deactivation hook](#deactivation-hook)
- [Add action for](#wc-loaded-hook) `woocommerce_loaded`]
- [Add action for](#flush-rewrite-rules)`woocommerce_flush_rewrite_rules`
- Register Admin notice manager to dokan container
- Init appserro tracker
- [Add action for](#plugin-loaded-action) `plugin_loaded`

### Define Constants

    $this->define( 'DOKAN_PLUGIN_VERSION', $this->version );
    $this->define( 'DOKAN_FILE', __FILE__ );
    $this->define( 'DOKAN_DIR', __DIR__ );
    $this->define( 'DOKAN_INC_DIR', __DIR__ . '/includes' );
    $this->define( 'DOKAN_LIB_DIR', __DIR__ . '/lib' );
    $this->define( 'DOKAN_PLUGIN_ASSEST', plugins_url( 'assets', __FILE__ ) );

    // give a way to turn off loading styles and scripts from parent theme
    $this->define( 'DOKAN_LOAD_STYLE', true );
    $this->define( 'DOKAN_LOAD_SCRIPTS', true );

### Activation hook
**Dokan installer** is run if the woocommerce is exists and also loads the common helper functions.

    /**
     * Placeholder for activation function
     *
     * Nothing being called here yet.
     */
    public function activate() {
        if ( ! $this->has_woocommerce() ) { //class_exists( 'WooCommerce' );
            set_transient( 'dokan_wc_missing_notice', true );
        }

        if ( ! $this->is_supported_php() ) {
            require_once WC_ABSPATH . 'includes/wc-notice-functions.php';

            /* translators: 1: Required PHP Version 2: Running php version */
            wc_print_notice( sprintf( __( 'The Minimum PHP Version Requirement for <b>Dokan</b> is %1$s. You are Running PHP %2$s', 'dokan-lite' ), $this->min_php, phpversion() ), 'error' );
            exit;
        }

        require_once __DIR__ . '/includes/functions.php';
        require_once __DIR__ . '/includes/functions-compatibility.php';

        $this->container['upgrades'] = new \WeDevs\Dokan\Upgrade\Manager();
        $installer                   = new \WeDevs\Dokan\Install\Installer();
        $installer->do_install();

        // rewrite rules during dokan activation
        if ( $this->has_woocommerce() ) {
            $this->flush_rewrite_rules();
        }
    }

### Deactivation hook

    /**
     * Placeholder for deactivation function
     *
     * Nothing being called here yet.
     */
    public function deactivate() {
        delete_transient( 'dokan_wc_missing_notice', true );
    }

### WC loaded hook
All helper methods and dokan container is loaded as well as `dokan_loaded` action is triggered.

    /**
     * Load the plugin after WP User Frontend is loaded
     *
     * @return void
     */
    public function init_plugin() {
        $this->includes();
        $this->init_hooks();

        do_action( 'dokan_loaded' );
    }


**includes** method load all helper [dokan functions](/helper-functions.md).

**init_hooks** method loads the container classes

    /**
     * Initialize the actions
     *
     * @return void
     */
    public function init_hooks() {
        // Localize our plugin
        add_action( 'init', [ $this, 'localization_setup' ] );

        // initialize the classes
        add_action( 'init', [ $this, 'init_classes' ], 4 );
        add_action( 'init', [ $this, 'wpdb_table_shortcuts' ] );

        add_action( 'plugins_loaded', [ $this, 'after_plugins_loaded' ] );

        add_filter( 'plugin_action_links_' . plugin_basename( __FILE__ ), [ $this, 'plugin_action_links' ] );
        add_action( 'in_plugin_update_message-dokan-lite/dokan.php', [ \WeDevs\Dokan\Install\Installer::class, 'in_plugin_update_message' ] );

        add_action( 'widgets_init', [ $this, 'register_widgets' ] );
    }

**dokan-pro** plugin is loaded for `add_action( 'plugins_loaded', [ $this, 'after_plugins_loaded' ] )` and dokan container is loaded for ` add_action( 'init', [ $this, 'init_classes' ], 4 )`.

    /**
     * Init all the classes
     *
     * @return void
     */
    public function init_classes() {
        new \WeDevs\Dokan\Withdraw\Hooks();
        new \WeDevs\Dokan\Order\Hooks();
        new \WeDevs\Dokan\Product\Hooks();
        new \WeDevs\Dokan\ProductCategory\Hooks();
        new \WeDevs\Dokan\Vendor\Hooks();
        new \WeDevs\Dokan\Upgrade\Hooks();
        new \WeDevs\Dokan\Vendor\UserSwitch();
        new \WeDevs\Dokan\CacheInvalidate();

        if ( is_admin() ) {
            new \WeDevs\Dokan\Admin\Hooks();
            new \WeDevs\Dokan\Admin\Menu();
            new \WeDevs\Dokan\Admin\AdminBar();
            new \WeDevs\Dokan\Admin\Pointers();
            new \WeDevs\Dokan\Admin\Settings();
            new \WeDevs\Dokan\Admin\UserProfile();
            new \WeDevs\Dokan\Admin\SetupWizard();
        } else {
            new \WeDevs\Dokan\Vendor\StoreListsFilter();
            new \WeDevs\Dokan\ThemeSupport\Manager();
        }

        $this->container['pageview']            = new \WeDevs\Dokan\PageViews();
        $this->container['seller_wizard']       = new \WeDevs\Dokan\Vendor\SetupWizard();
        $this->container['core']                = new \WeDevs\Dokan\Core();
        $this->container['scripts']             = new \WeDevs\Dokan\Assets();
        $this->container['email']               = new \WeDevs\Dokan\Emails\Manager();
        $this->container['vendor']              = new \WeDevs\Dokan\Vendor\Manager();
        $this->container['product']             = new \WeDevs\Dokan\Product\Manager();
        $this->container['shortcodes']          = new \WeDevs\Dokan\Shortcodes\Shortcodes();
        $this->container['registration']        = new \WeDevs\Dokan\Registration();
        $this->container['order']               = new \WeDevs\Dokan\Order\Manager();
        $this->container['api']                 = new \WeDevs\Dokan\REST\Manager();
        $this->container['withdraw']            = new \WeDevs\Dokan\Withdraw\Manager();
        $this->container['dashboard']           = new \WeDevs\Dokan\Dashboard\Manager();
        $this->container['commission']          = new \WeDevs\Dokan\Commission();
        $this->container['customizer']          = new \WeDevs\Dokan\Customizer();
        $this->container['upgrades']            = new \WeDevs\Dokan\Upgrade\Manager();
        $this->container['product_sections']    = new \WeDevs\Dokan\ProductSections\Manager();
        $this->container['reverse_withdrawal']  = new \WeDevs\Dokan\ReverseWithdrawal\ReverseWithdrawal();
        $this->container['dummy_data_importer'] = new \WeDevs\Dokan\DummyData\Importer();
        $this->container['catalog_mode']        = new \WeDevs\Dokan\CatalogMode\Controller();

        //fix rewrite rules
        if ( ! isset( $this->container['rewrite'] ) ) {
            $this->container['rewrite'] = new \WeDevs\Dokan\Rewrites();
        }

        $this->container = apply_filters( 'dokan_get_class_container', $this->container );

        if ( defined( 'DOING_AJAX' ) && DOING_AJAX ) {
            new \WeDevs\Dokan\Ajax();
        }

        new \WeDevs\Dokan\Privacy();
    }
### Flush rewrite rules 

    /**
     * Handles scenerios when WooCommerce is not active
     *
     * @since 2.9.27
     *
     * @return void
     */
    public function woocommerce_not_loaded() {
        if ( did_action( 'woocommerce_loaded' ) || ! is_admin() ) {
            return;
        }

        require_once DOKAN_INC_DIR . '/functions.php';

        if ( get_transient( '_dokan_setup_page_redirect' ) ) {
            dokan_redirect_to_admin_setup_wizard();
        }

        new \WeDevs\Dokan\Admin\SetupWizardNoWC();
    }

### Plugin loaded action

    /**
     * Handles scenerios when WooCommerce is not active
     *
     * @since 2.9.27
     *
     * @return void
     */
    public function woocommerce_not_loaded() {
        if ( did_action( 'woocommerce_loaded' ) || ! is_admin() ) {
            return;
        }

        require_once DOKAN_INC_DIR . '/functions.php';

        if ( get_transient( '_dokan_setup_page_redirect' ) ) {
            dokan_redirect_to_admin_setup_wizard();
        }

        new \WeDevs\Dokan\Admin\SetupWizardNoWC();
    }

