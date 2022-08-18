## Hooks
- do_action( 'dokan_loaded' );


### Filters

- apply_filters( 'dokan_template_path', 'dokan/' )
- $this->container = apply_filters( 'dokan_get_class_container', $this->container );
-
```
apply_filters(
        'dokan_admin_settings_rearrange_map', [
            'shipping_fee_recipient_dokan_general'     => [ 'shipping_fee_recipient', 'dokan_selling' ],
            'tax_fee_recipient_dokan_general'          => [ 'tax_fee_recipient', 'dokan_selling' ],
            'store_open_close_dokan_general'           => [ 'store_open_close', 'dokan_appearance' ],
            'store_map_dokan_general'                  => [ 'store_map', 'dokan_appearance' ],
            'gmap_api_key_dokan_general'               => [ 'gmap_api_key', 'dokan_appearance' ],
            'contact_seller_dokan_general'             => [ 'contact_seller', 'dokan_appearance' ],
            'enable_theme_store_sidebar_dokan_general' => [ 'enable_theme_store_sidebar', 'dokan_appearance' ],
            'setup_wizard_logo_url_dokan_appearance'   => [ 'setup_wizard_logo_url', 'dokan_general' ],
            'disable_welcome_wizard_dokan_selling'     => [ 'disable_welcome_wizard', 'dokan_general' ],
        ]```

### Transient
- set_transient( 'dokan_wc_missing_notice', true );
- delete_transient( 'dokan_wc_missing_notice', true );
- 

### Dokan Container

```
    $this->container['admin_notices']       = new \WeDevs\Dokan\Admin\Notices\Manager();
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
    $this->container['rewrite']             = new \WeDevs\Dokan\Rewrites();

```
### Others
- $processes = get_option( 'dokan_background_processes', [] );

### Wp function

- wp_safe_remote_get
- is_wp_error
- get_transient
- set_transient
- wp_kses_post
- register_activation_hook
- register_deactivation_hook
- do_action
- add_action
- did_action
- flush_rewrite_rules
- load_plugin_textdomain
- wc_print_notice
- untrailingslashit
### WC Action
- woocommerce_loaded
- woocommerce_flush_rewrite_rules
- wp_safe_redirect