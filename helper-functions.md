
<style>
td, th {
   border: none!important;
}
</style>

## Helper Functions

- [Common functions](#common-functions)
- [Order functions](#order-functions)
- [Product functions](#product-function)
- [Withdrawal functions](#withdraw-functions)
- [Compatibility functions](#compatibility-functions)
- [Dokan WC functions](#dokan-woocommerce-functions)
- [Admin functions](#admin-functions)
- [Store function](#dokan-store-function)

### Common Functions

| | |
| --- | ---|
|`dokan_admin_menu_position()` |`dokana_admin_menu_capability()`|
|`dokan_get_current_user_id()` |`dokan_is_user_seller( $user_id )`|
|`dokan_is_user_customer( $user_id )` |`dokan_is_product_author( $product_id = 0 )`|
|`dokan_is_store_page()` |`dokan_is_product_edit_page()`|
|`dokan_is_seller_dashboard()` |`dokan_redirect_login()`|
|`dokan_redirect_if_not_seller( $redirect = '' )` |`dokan_count_posts( $post_type, $user_id, $exclude_product_types = array('booking' ) )`|
|`arguments as key => value pai` |`dokan_count_stock_posts( $post_type, $user_id, $stock_type )`|
|`dokan_count_comments( $post_type, $user_id )` |`dokan_author_pageviews( $seller_id )`|
|`dokan_author_total_sales( $seller_id )` |`dokan_generate_sync_table()`|
|`dokan_get_seller_earnings_by_order( $order, $seller_id )` |`dokan_get_seller_percentage( $seller_id = 0, $product_id = 0, $category_id = 0 )`|
|`dokan_get_commission_type( $seller_id = 0, $product_id = 0, $category_id = 0 )` |`dokan_get_new_post_status()`|
|`to get the client ip addre` |`dokan_get_client_ip()`|
|`dokan_post_input_box( $post_id, $meta_key, $attr = [], $type = 'text' )` |`dokan_get_post_status( $status = '' )`|
|`dokan_get_post_status_label_class( $status = '' )` |`dokan_get_product_types( $status = '' )`|
|`for input text fie` |`dokan_posted_input( $key, $array = false )`|
|`for input textar` |`dokan_posted_textarea( $key )`|
|`dokan_get_template_part( $slug, $name = '', $args = [] )` |`dokan_get_template( $template_name, $args = [], $template_path = '',$default_path = '' )`|
|`dokan_locate_template( $template_name, $template_path = '', $default_path = '', $pro = false )` |`dokan_get_page_url( $page, $context = 'dokan', $subpage = '' )`|
|`dokan_add_subpage_to_url( $url, $subpage )` |`dokan_edit_product_url( $product )`|
|`dokan_admin_product_columns( $columns )` |`dokan_get_option( $option, $section, $default = '' )`|
|`dokan_redirect_to_register()` |`dokan_is_seller_enabled( $user_id )`|
|`dokan_is_seller_trusted( $user_id )` |`dokan_get_store_url( $user_id )`|
|`dokan_is_store_review_page()` |`for loggi`|
|`dokan_log( $message, $level = 'debug' )` |`dokan_media_uploader_restrict( $args )`|
|`dokan_get_store_info( $seller_id )` |`dokan_get_store_tabs( $store_id )`|
|`dokan_get_seller_withdraw_mail( $seller_id, $type = 'paypal' )` |`dokan_get_seller_bank_details( $seller_id )`|
|`dokan_get_sellers( $args = [] )` |`dokan_prepare_chart_data( $data, $date_key, $data_key, $interval, $start_date, $group_by )`|
|`dokan_admin_user_register( $user_id )` |`dokan_get_percentage_of( $this_period = 0, $last_period = 0 )`|
|`dokan_get_seller_count( $from = null, $to = null )` |`dokan_get_product_count( $from = null, $to = null, $seller_id = null )`|
|`dokan_prepare_date_query( $from, $to )` |`dokan_get_sales_count( $from = null, $to = null, $seller_id = 0 )`|
|`dokan_disable_admin_bar( $show_admin_bar )` |`dokan_filter_product_for_current_vendor( $query )`|
|`dokan_filter_orders_for_current_vendor( $args, $query )` |`dokan_map_meta_caps( $caps, $cap, $user_id, $args )`|
|`dokan_remove_sellerdiv_metabox()` |`dokan_number_format( $number )`|
|`dokan_get_coupon_edit_url( $coupon_id, $coupon_page = '' )` |`dokan_get_avatar_url( $url, $id_or_email, $args )`|
|`dokan_get_navigation_url( $name = '' )` |`dokan_country_dropdown( $options, $selected = '', $everywhere = false )`|
|`dokan_state_dropdown( $options, $selected = '', $everywhere = false )` |`dokan_get_shipping_processing_times()`|
|`dokan_get_processing_time_value( $index )` |`dokan_get_vendor_order_details( $order_id, $vendor_id = null )`|
|`dokan_wc_email_recipient_add_seller_no_stock( $recipient, $product )` |`dokan_product_listing_filter_months_dropdown( $user_id )`|
|`dokan_product_listing_filter()` |`dokan_product_search_by_sku( $where )`|
|`dokan_get_social_profile_fields()` |`dokan_seller_address_fields( $verified = false, $required = false )`|
|`dokan_get_seller_address( $seller_id = '', $get_array = false )` |`dokan_get_seller_short_address( $store_id, $line_break = true )`|
|`dokan_get_toc_url( $store_id )` |`dokan_after_login_redirect( $redirect_to, $user )`|
|`dokan_is_valid_owner( $post_id, $user_id )` |`dokan_set_is_home_false_on_store()`|
|`dokan_register_store_widget()` |`dokan_get_category_wise_seller_commission( $product_id, $category_id = 0 )`|
|`dokan_get_category_wise_seller_commission_type( $product_id, $category_id = 0 )` |`dokan_get_earning_by_product( $product_id, $seller_id )`|
|`dokan_delete_user_details( $user_id, $reassign )` |`dokan_get_vendor( $vendor_id = null )`|
|`dokan_get_all_caps()` |`dokan_get_all_cap_labels( $cap )`|
|`is similiar to WordPress wp_parse_args(` |`dokan_parse_args( &$args, $defaults = [] )`|
|`dokan_get_translations_for_plugin_domain( $domain, $language_dir = null )` |`dokan_get_jed_locale_data( $domain, $language_dir = null )`|
|`dokan_revoke_change_order_status()` |`dokan_remove_action_column( $columns )`|
|`dokan_remove_action_button( $actions )` |`dokan_get_translated_days( $day = '' )`|
|`dokan_get_store_times( $day, $return_type, $index = null, $store_id = null )` |`dokan_is_store_open( $user_id )`|
|`dokan_customer_has_order_from_this_seller( $customer_id, $seller_id = null )` |`dokan_pro_buynow_url()`|
|`dokan_add_vendor_info_in_rest_order( $response )` |`dokan_stop_sending_multiple_email()`|
|`dokan_remove_hook_for_anonymous_class( $hook_name = '', $class_name = '', $method_name = '', $priority = 0 )`|`dokan_get_variable_product_earning( $product_id, $formated = true, $deprecated = false )`|
|`( $id )` |`dokan_get_permalink( $page_id )`|
|`dokan_is_store_listing()` |`dokan_generate_username( $name = 'store' )`|
|`dokan_replace_policy_page_link_placeholders( $text )` |`dokan_privacy_policy_text( $return = false )`|
|`dokan_commission_types()` |`dokan_login_form( $args = [], $echo = false )`|
|`dokan_validate_boolean( $var )` |`dokan_admin_settings_rearrange_map( $option, $section )`|
|`dokan_get_terms_condition_url()` |`dokan_array_after( $array, $position, $new_array )`|
|`dokan_get_seller_status_count()` |`dokan_install_wp_org_plugin( $plugin_slug, $main_file = null )`|
|`dokan_redirect_to_admin_setup_wizard()` |`dokan_generate_ratings( $rating, $stars )`|
|`dokan_met_minimum_php_version_for_wc( $required_version = '7.0' )` |`dokan_has_map_api_key()`|
|`dokan_clear_product_caches( $product )` |`dokan_is_vendor_info_hidden( $option = null )`|
|`current_datetime() compatibility for wp version < 5` |`dokan_current_datetime()`|
|`wp_timezone() compatibility for wp version < 5` |`dokan_wp_timezone()`|
|`wp_timezone_string() compatibility for wp version < 5` |`dokan_wp_timezone_string()`|
|`dokan_format_datetime( $date = '', $format = false )` |`dokan_format_date( $date = '', $format = false )`|
|`dokan_format_time( $date = '', $format = false )` |`dokan_get_timestamp( $date_string, $gmt_date = false )`|
|`dokan_get_withdraw_threshold( $user_id )` |`dokan_mask_email_address( $email )`|
|`dokan_array_insert_after( array $old_array, array $new_array, $insert_after_key )` |`dokan_is_admin_coupon_applied( $order, $vendor_id, $product_id = 0 )`|
|`dokan_get_vendor_store_banner_width()` |`dokan_get_vendor_store_banner_height()`|
|`dokan_get_recaptcha_site_and_secret_keys( $bool = false )` |`dokan_handle_recaptcha_validation( $action, $token, $secretkey )`|
|`dokan_get_additional_product_sections()` |`dokan_string_to_bool( $value )`|
|`dokan_bool_to_on_off( $bool )` |`is_tweleve_hour_format()`|

### Order Functions

| | |
| --- | --- |
|`dokan_get_seller_amount_from_order( $order_id, $get_array = false )` |`dokan_get_seller_orders( $seller_id, $args )`|
|`dokan_get_seller_orders_by_date( $start_date, $end_date, $seller_id = false, $status = 'all' )` |`dokan_get_seller_withdraw_by_date( $start_date, $end_date, $seller_id = false )`|
|`dokan_get_seller_orders_number( $args = [] )` |`dokan_is_seller_has_order( $seller_id, $order_id )`|
|`dokan_count_orders( $user_id )` |`dokan_delete_sync_order( $order_id )`|
|`dokan_delete_sync_duplicate_order( $order_id, $seller_id )` |`dokan_sync_insert_order( $order_id )`|
|`dokan_get_seller_id_by_order( $order_id )` |`dokan_get_order_status_class( $status )`|
|`dokan_get_order_status_translated( $status )` |`dokan_get_product_list_by_order( $order, $glue = ',' )`|
|`dokan_is_sub_order( $order_id )` |`dokan_total_orders()`|
|`dokan_get_sellers_by( $order )` |`dokan_get_seller_ids_by( $order_id )`|
|`dokan_get_suborder_ids_by( $parent_order_id )` |`dokan_get_admin_commission_by( $order, $context )`|
|`dokan_get_customer_orders_by_seller( $customer_id, $seller_id )` |`dokan_order_csv_headers()`|
|`dokan_order_csv_export( $orders, $file = null )` |`dokan_get_seller_id_by_order_id( $id )`|
|`dokan_is_order_already_exists( $id )`| |

### Product Function

| | |
| --- | --- |
|`dokan_save_product( $args )` |`dokan_product_output_variations()`|
|`dokan_get_product_visibility_options()` |`dokan_search_seller_products( $term, $user_ids = false, $type = '', $include_variations = false )`|
|`dokan_products_array_filter_editable( $product )` |`dokan_product_get_row_action( $post )`|
|`dokan_get_vendor_by_product( $product, $get_vendor_id = false )` |`dokan_get_translated_product_stock_status( $stock = false )`|
|`dokan_store_product_catalog_orderby()`|

### Withdraw Functions

| | |
| --- | ---|
|`dokan_withdraw_register_methods()` |`dokan_withdraw_get_methods()`|
|`dokan_withdraw_get_active_methods()` |`dokan_get_seller_active_withdraw_methods( $vendor_id = 0 )`|
|`dokan_withdraw_get_method( $method_key )` |`dokan_withdraw_get_method_title( $method_key, $request = null )`|
|`dokan_withdraw_method_paypal( $store_settings )` |`dokan_withdraw_method_skrill( $store_settings )`|
|`dokan_withdraw_method_bank( $store_settings )` |`dokan_get_withdraw_count( $user_id = null )`|
|`dokan_withdraw_get_active_order_status()` |`dokan_withdraw_get_active_order_status_in_comma()`|
|`dokan_withdraw_get_method_icon( $method_key )` |`dokan_withdraw_get_method_additional_info( $method_key )`|
|`dokan_withdraw_get_default_method( $vendor_id = 0 )` |`dokan_withdraw_is_manual_request_enabled()`|
|`dokan_withdraw_is_disabled()` |`dokan_withdraw_get_withdrawable_active_methods()`|
|`dokan_is_withdraw_method_enabled( $method_id )`|

### Compatibility Functions
| | |
| --- | --- |
|`dokan_wc_get_product( $product )` |`dokan_get_prop( $object, $prop, $callback = false )`|
|`dokan_replace_func( $old_method, $new_method, $object = null )` |`dokan_get_date_created( $order )`|
|`dokan_get_metadata( $order, $item_id )` |`dokan_get_product_downloads( $product )`|
|`dokan_save_product_price( $product_id, $regular_price, $sale_price = '', $date_from = '', $date_to = '' )` |`dokan_process_product_file_download_paths_permission( $product_id, $variation_id, $downloadable_files )`|

### Dokan Woocommerce Functions

|  |  |
| --- | --- |
|`dokan_process_product_meta( $post_id, $data = [] )` |`dokan_process_product_file_download_paths( $product_id, $variation_id, $downloadable_files )`|
|`dokan_sub_order_get_total_coupon( $order_id )` |`dokan_seller_displayname( $display_name )`|
|`dokan_get_featured_products( $per_page = 9, $seller_id = '', $page = 1 )` |`dokan_get_latest_products( $per_page = 9, $seller_id = '', $page = 1 )`|
|`dokan_get_best_selling_products( $per_page = 8, $seller_id = '', $page = 1, $hide_outofstock = false )` |`check_more_seller_product_tab()`|
|`dokan_get_top_rated_products( $per_page = 8, $seller_id = '', $page = 1 )` |`dokan_get_on_sale_products( $per_page = 10, $paged = 1, $seller_id = '' )`|
|`dokan_get_seller_balance( $seller_id, $formatted = true )` |`dokan_get_seller_earnings( $seller_id, $formatted = true, $on_date = '' )`|
|`dokan_get_seller_rating( $seller_id )` |`dokan_get_readable_seller_rating( $seller_id )`|
|`dokan_exclude_child_customer_receipt( &$phpmailer )` |`dokan_filter_woocommerce_dashboard_status_widget_sales_query( $query )`|
|`dokan_save_account_details()` |`dokan_clear_best_selling_product_category_cache( $order_id )`|
|`dokan_clear_edit_product_category_cache( $term_id )` |`dokan_date_time_format( $time, $date_only = false )`|
|`dokan_split_profile_completion_value( $progress_values )` |`dokan_set_more_from_seller_tab( $tabs )`|
|`dokan_get_more_products_from_seller( $seller_id = 0, $posts_per_page = 6 )` |`dokan_bulk_order_status_change()`|
|`dokan_add_reply_to_vendor_email_on_wc_customer_note_mail( $headers, $id, $order )` |`dokan_keep_old_vendor_woocommerce_duplicate_product( $duplicate, $product )`|
|`send_email_for_order_cancellation( $recipient, $order )`|

### Admin Functions

|  |  |
| --- | --- |
|`dokan_admin_get_help(` |`dokan_override_product_author( $product, $seller_id `|
|`dokan_admin_report_data( $group_by = 'day', $year = '', $start = '', $end = '', $seller_id = '' )` |`dokan_admin_report( $group_by = 'day', $year = '', $start = '', $end = '' `|
|`dokan_admin_report_by_seller( $chosen_seller_id )`|

### Dokan Store Function


`dokan_store_theme_sidebar_enabled()`