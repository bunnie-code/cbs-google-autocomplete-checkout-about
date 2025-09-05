# Google Address Autocomplete for WooCommerce Checkout

A premium plugin that simplifies the checkout process by helping customers enter their addresses using Google Places API. This plugin enhances the user experience, reduces errors, and speeds up the checkout process.

## Current Version: 1.0.2

[View Changelog](CHANGELOG.md)

## Features

- **Address Autocomplete**: Use Google Places API to suggest addresses as customers type
- **Smart Address Field Management**: Auto-populate all standard WooCommerce address fields
- **Flexible Configuration**: Enable for billing, shipping, or both address sections
- **Display Options**: Choose between always showing address fields or revealing them after address selection
- **Custom Styling**: Native WooCommerce style or premium enhanced style
- **Neighborhood Support**: Additional fields for countries with specific address formats
- **Country Restriction**: Limit address suggestions to specific countries
- **Multi-language Support**: Works with all languages supported by Google Places API
- **Returning Customer Options**: Special handling for returning customers
- **HPOS Compatible**: Works with High-Performance Order Storage system
- **Developer Friendly**: Hooks and filters for extending functionality
- **Non-conflicting**: Uses unique prefix (cbs-gaac) to avoid conflicts with other plugins

## Installation

1. Upload the plugin files to the `/wp-content/plugins/cbs-google-autocomplete-checkout` directory
2. Activate the plugin through the 'Plugins' menu in WordPress
3. Go to WooCommerce → Address Autocomplete to configure the plugin

## Configuration

### API Key Setup

1. Visit the [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the Places API and Maps JavaScript API
4. Create API credentials (API key)
5. Set up appropriate restrictions (recommended):
   - HTTP referrers (websites): Your domain(s)
   - API restrictions: Places API and Maps JavaScript API
6. Copy the API key to the plugin settings

### Plugin Settings

#### General

- **Enable Plugin**: Turn the functionality on or off
- **Google Places API Key**: Your Google API key with Places API enabled
- **Language**: Select the language for address suggestions
- **Enable For**: Choose to enable for billing, shipping, or both address sections

#### Appearance

- **Field Style**: Select between native WooCommerce style or premium style
- **Display Mode**: Choose to show all fields by default or only after address selection
- **Field Labels**: Customize labels for various interface elements

#### Advanced

- **Country Restriction**: Limit address suggestions to specific countries
- **Optional Address Field**: Make the autocomplete field optional instead of required
- **Support Neighborhoods**: Enable additional fields for countries with specific address formats
- **Hide for Returning Customers**: Choose whether to hide address details for returning customers

## Developer Documentation

### Hooks and Filters

#### Filters

```php
// Modify Google API script parameters
add_filter('cbs_gaac_google_script_parameters', function($params) {
    // $params is a string with existing parameters
    return $params . '&libraries=places,geometry';
});

// Add additional fields after billing address
add_filter('cbs_gaac_billing_fields_after_address', function($fields) {
    // $fields is an array of field IDs
    $fields[] = 'my_custom_field_id';
    return $fields;
});

// Add additional fields after shipping address
add_filter('cbs_gaac_shipping_fields_after_address', function($fields) {
    // $fields is an array of field IDs
    $fields[] = 'my_custom_field_id';
    return $fields;
});

// Add countries that need additional fields
add_filter('cbs_gaac_countries_with_additional_fields', function($countries) {
    // $countries is an array of country codes
    $countries[] = 'IT'; // Add Italy
    return $countries;
});

// Define additional fields for specific countries
add_filter('cbs_gaac_additional_fields', function($fields) {
    // $fields is an array with billing and shipping sections
    $fields['billing']['street_name'] = 'billing_street_name';
    $fields['billing']['house_number'] = 'billing_house_number';
    return $fields;
});
```

## Troubleshooting

### Common Issues

1. **Address suggestions not appearing**
   - Verify your API key is correct and has Places API enabled
   - Check for JavaScript errors in browser console
   - Ensure your domain is authorized in the Google API Console

2. **Fields not populating correctly**
   - Check if there are any JavaScript conflicts with other plugins
   - Verify WooCommerce checkout fields haven't been modified by other plugins

3. **Country-specific formatting issues**
   - Enable the "Support Neighborhoods" option for countries with special address formats

### Support

For additional help, please contact us at [https://bunniecode.eu/support](https://bunniecode.eu/support)

## Changelog

### 1.0.0
- Initial release

## License

This plugin is licensed under the GPL v2 or later.

---

Made with ❤️ by [bunniecode](https://bunniecode.eu)