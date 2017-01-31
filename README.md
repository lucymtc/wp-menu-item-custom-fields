# WP Menu Item Custom Fields

Useful to easily append custom fields to WordPress menu items.

### Usage

To get it going you need to include Menu.php into your theme or plugin.
```
require_once dirname( __FILE__ ) . '/Menu.php';
```
Then set up the list of custom fields into an array and pass it over as the argument when declaring a new Menu.
Currently supports adding text fields and select dropdows.

An example:

```php
add_action( 'init', 'setup_menu_custom_fields' );
function setup_menu_custom_fields() {

	$fields = array(
		'_mycustom_field_1' => array(
			'label' => __( 'Custom field 1', 'domain' ),
			'element' => 'input',
			'sanitize_callback' => 'sanitize_text_field',
			'attrs' => array(
				'type' => 'text',
				),
			),
		'_mycustom_field_2' => array(
			'label' => __( 'Custom field 2', 'domain' ),
			'element' => 'select',
			'sanitize_callback' => 'sanitize_text_field',
			'options' => array(
				'option-1' => __( 'Option 1', 'domain' ),
				'option-2' => __( 'Option 2', 'domain' ),
				),
			),
		);

		// Menu Management custom fields.
		new \Lucymtc\Menu( $fields );
}
```
