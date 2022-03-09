# Useful mods to the SEO Framework Plugin
#### March 8th 2022

I love this plugin, The SEO Framework, for WordPress. It makes so muck on the editorial side easier when it comes to managing SEO and social previews. It has numerous hooks and [actions](https://theseoframework.com/docs/api/actions/), though most are not documented as such. That said, I've found it necessary to change things from time to time and hope this proves useful.

### Simplify Credits
The plugin, by default inserts attribution into every page by way of a HTML comment. It can look like this when you _View Source_:

```html
<title>donohoe.dev</title>
<!-- The SEO Framework by Sybre Waaijer -->
<meta name="robots" content="max-snippet:-1,max-image-preview:standard,max-video-preview:-1" />
```

I like to keep things minimal, this reduces the foot-print a little bit:

```php
/*
	Allow plugin credit in HTML comment, but keep it simple
*/
function plugin_seo_framework_simple_credit( $arg ) {
    return '';
}
add_filter( 'sybre_waaijer_<3', 'plugin_seo_framework_simple_credit', 10, 1 );
```

### Disable the "twitter:creator"

I work with sites that use the Co-Authors Plus plugin to manage a large number of contributors. It works greta, but the SEO plugin will pull Twitter information from the post author and not the contributor.

```php
/*
	Disable "twitter:creator" META tag in "SEO Framework" plugin.
	Otherwise it will grab Twitter handle of Editor (or user that created the article), not the Author.
*/
add_filter( 'the_seo_framework_twittercreator_output', '__return_empty_string' );
```

### Rename Tabs

When creating an article, in the SEO Framework UI, I personally found "General" not to be very specific so I wanted to rename it to "SEO".

```php
/*
	Rename the "General" tab to be "SEO".
*/
function plugin_seo_framework_rename_seo_tab ( $tabs, $args ) {
	if (isset($tabs['general'])) {
		$tabs['general']['name'] = 'SEO';
	}
	return $tabs;
}
add_filter('the_seo_framework_inpost_settings_tabs', 'plugin_seo_framework_rename_seo_tab', 10, 2);
```
