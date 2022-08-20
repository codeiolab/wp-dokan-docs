### During Boot

#### Actions
|`woocommerce_loaded` |`woocommerce_flush_rewrite_rules`|
|`plugins_loaded` |`init`|
|`plugins_loaded` |`in_plugin_update_message-dokan-lite/dokan.php`|
|`widgets_init`|

### Filters
`plugin_action_links_{dokan plugin path}`
`dokan_template_path`
`dokan_get_class_container`
`dokan_is_pro_exists`

### Withdraw
Class `WeDevs\Dokan\Withdraw\Hooks`


#### Actions
|  | |
| --- | ---|
|`dokan_withdraw_request_approved` |`wp_ajax_dokan_handle_withdraw_request`|
|`wp_ajax_dokan_withdraw_handle_make_default_method`| |

#### Filter

`dokan_get_withdraw_method_title`

### Order
Class `WeDevs\Dokan\Order\Hooks`

#### Actions
|  | |
| --- | ---|
|`woocommerce_order_status_changed` |`woocommerce_order_status_changed`|
|`woocommerce_checkout_update_order_meta` |`woocommerce_checkout_update_order_meta`|
|`dokan_checkout_update_order_meta` |`woocommerce_process_shop_order_meta`|
|`woocommerce_reduce_order_stock` |`woocommerce_reduce_order_stock`|
|`wc-admin_import_orders` |`woocommerce_order_status_changed`|

#### Filters
|  | |
| --- | ---|
|`woocommerce_coupon_is_valid` |`woocommerce_analytics_orders_select_query`|
|`dokan_csv_export_headers` |`woocommerce_order_item_display_meta_key`|
|`woocommerce_order_item_display_meta_value`|

### Product
#### Actions
|  | |
| --- | ---|
|`template_redirect` |`dokan_bulk_product_status_change`|
|`dokan_store_profile_frame_after` |`wp_ajax_dokan_store_product_search_action`|
|`wp_ajax_nopriv_dokan_store_product_search_action` |`woocommerce_product_quick_edit_save`|
|`woocommerce_product_bulk_edit_save` |`woocommerce_new_product`|
|`woocommerce_update_product`|`woocommerce_product_meta_end`|
|`dokan_new_product_added` |`dokan_product_updated`|
|`dokan_product_deleted` |`dokan_product_duplicate_after_save`|
|`woocommerce_new_product` |`woocommerce_update_product`|
|`woocommerce_product_duplicate` |`woocommerce_product_import_inserted_product_object`|
|`wp_trash_post` |`delete_post`|
|`woocommerce_attribute_updated` |`woocommerce_attribute_deleted`|
|`dokan_product_updated` |`dokan_bulk_product_status_change`|
#### Filters

|  | |
| --- | ---|
|`dokan_settings_fields`| |

### Product Category

#### Actions

|  | |
| --- | ---|
|`pre_delete_term`|`dokan_delete_reference_category_from_chosen_cat`|
|`edit_product_cat`| `pre_delete_term`|
|`create_product_cat`||

### Vendor

#### Actions

|  | |
| --- | ---|
|`dokan_new_vendor` |`dokan_update_vendor`|
|`dokan_delete_vendor` |`dokan_vendor_enabled`|
|`dokan_vendor_disabled` |`dokan_store_profile_saved`|
|`user_register` |`profile_update`|
|`delete_user`| |

### Upgrades

#### Actions

|  | |
| --- | ---|
|`wp_ajax_dokan_do_upgrade`|`dokan_upgrade_is_not_required`|
|`dokan_upgrade_finished`| |

#### Filters

|  | |
| --- | ---|
|`dokan_upgrade_is_upgrade_required`|`dokan_upgrade_upgrades`|
|`dokan_admin_notices`| |

### UserSwitch

#### Action
`dokan_dashboard_content_inside_before`

#### Filters
| | |
| --- | --- |
|`dokan_admin_localize_script`|`dokan_rest_store_additional_fields`|

### Cache Invalidate
#### Actions
| | |
| --- | --- |
|`comment_post` |`edit_comment`|
|`delete_comment` |`wp_set_comment_status`|

### Vendor Store List

#### Action
`dokan_store_lists_filter_form`

#### Filter
`dokan_seller_listing_args`

### Theme Manager
#### Filter
`dokan_load_theme_support_files`

### Admin

#### Actions

| |  |
| --- | --- |
|`manage_shop_order_posts_custom_column` |`admin_footer`|
|`wp_trash_post` |`untrash_post`|
|`delete_post` |`restrict_manage_posts`|
|`pending_to_publish` |`add_meta_boxes`|
|`woocommerce_process_product_meta`|

#### Filters
| | |
|--- | ---|
|`woocommerce_reports_get_order_report_query` |`manage_edit`|
|`post_class` |`post_types_to_delete_with_user`|
|`dokan_save_settings_value`|

### Admin Menu
#### Actions
| |  |
| --- | --- |
|`admin_menu` | `wp_before_admin_bar_render`|
|`admin_bar_menu`|

#### Filter
`dokan_show_admin_bar_visit_dashboard`

### Admin Pointer
#### Actions
| |  |
| --- | --- |
|`admin_enqueue_scripts`|`wp_ajax_dokan-dismiss-wp-pointer`|

### Admin Settings
#### Actions
| |  |
| --- | --- |
|`wp_ajax_dokan_get_setting_values` |`wp_ajax_dokan_save_settings`|
|`dokan_before_saving_settings` |`wp_ajax_dokan_refresh_admin_settings_field_options`|

#### Filters
| |  |
| --- | --- |
|`dokan_admin_localize_script` |`dokan_admin_localize_script`|
|`dokan_get_settings_values` |`dokan_get_settings_values`|
|`dokan_settings_general_site_options`|

### User Profile
#### Actions
| |  |
| --- | --- |
|`show_user_profile` |`edit_user_profile`|
|`personal_options_update` |`edit_user_profile_update`|
|`admin_enqueue_scripts`|

### Admin Setup Wizard
#### Actions
| |  |
| --- | --- |
|`admin_menu` |`admin_init`|
|`dokan_admin_setup_wizard_step_store_start` |`dokan_admin_setup_wizard_save_step_store`|
|`shutdown`|
#### Filters
| |  |
| --- | --- |
|`user_has_cap` |`dokan_admin_setup_wizard_steps`|
|`dokan_setup_wizard_enqueue_scripts`|