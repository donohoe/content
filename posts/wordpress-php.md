# Adjustments to WordPress 
#### December 16th 2022

A collection of useful functions, actions, and other ways to alter WordPress.

### Change default slug for Posts

The default slug is based on the initial Title. If the title is long htis can be very annoying as I personally like short paths and without basic repeating words like _the_, _and_, _I_, etc. This also prevents a slug from being longer than 6 words. You are always free to edit afterwards.

Source: https://gist.github.com/donohoe/4766b8a20cc6573de3dd3cb59df9fc32

### Disable External Embeddding

Tell modern browsers to disallow embedding of our site from other domains. 

More information: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options (developer.mozilla.org)

```php
function disable_external_embedding( $headers ) {
	$headers[ 'X-Frame-Options' ] = 'SAMEORIGIN';
	return $headers;
}
add_filter( 'wp_headers', 'disable_external_embedding' );
```

### Disable FLoC

Prevent the (Chrome) browser from performing profiling for third-party trackers using [Federated Learning of Cohorts](https://developer.chrome.com/docs/privacy-sandbox/floc/).

```php
function disable_floc( $headers ) {
	$headers[ 'Permissions-Policy' ] = 'browsing-topics=()';
	return $headers;
}
add_filter( 'wp_headers', 'disable_floc' );
```

### Remove Comments from WP Admin menu

After you disable comments it still shows up. Lets address that.

```php
function row_remove_menu_items() {
	remove_menu_page( 'edit-comments.php' );
	remove_menu_page( 'edit.php?post_type=sidebar' );
}
add_action( 'admin_menu', 'row_remove_menu_items' );
```
### Remove jQuery and wp-embed.js

jQuery had its time and place but it is time to move on. You don't really need a framework for most projects.

```php
function deregister_unused_scripts_and_styles(){

	/* Required by plugin Query Monitor so leave alone if active */
	if (!class_exists('QM_Plugin')) {
		wp_deregister_style( 'dashicons' ); 
		wp_deregister_script( 'jquery' );
	}

	wp_deregister_script( 'wp-embed' );
	wp_dequeue_style( 'wp-block-library' );
	wp_dequeue_style( 'wpcom-notes-admin-bar' );
	wp_dequeue_style( 'noticons');
	
}
add_action( 'wp_enqueue_scripts', 'deregister_unused_scripts_and_styles' );
```

### Remove what you do not really need...

Across different versions its not clear if these all still work. I've found some incocnisstencies in their effect.

```php
/*
	Remove JetPack CSS
	Link: https://css-tricks.com/snippets/wordpress/removing-jetpack-css/
*/
add_filter( 'jetpack_sharing_counts',       '__return_false', 99 );
add_filter( 'jetpack_implode_frontend_css', '__return_false', 99 );

/*
	Remove Emojis
	https://crunchify.com/not-using-emoji-on-your-wordpress-blog-stop-loading-wp-emoji-release-min-js-and-css-file/
*/
remove_action( 'wp_head',         'print_emoji_detection_script', 7 );
remove_action( 'wp_print_styles', 'print_emoji_styles' );

remove_action( 'admin_print_scripts', 'print_emoji_detection_script' );
remove_action( 'admin_print_styles',  'print_emoji_styles' );

/* 
	Remove pre-fetch META tags
*/
remove_action( 'wp_head', 'wp_resource_hints', 2 );

/*
	Remove default icons
*/
remove_action( 'wp_head', 'wp_site_icon', 99 );

/*
	Clean the HEAD
*/
remove_action( 'wp_head', 'wp_resource_hints', 2 ); /* Remove pre-fetch META tags */
remove_action( 'wp_head', 'rsd_link' );
remove_action( 'wp_head', 'wlwmanifest_link' );
remove_action( 'wp_head', 'adjacent_posts_rel_link_wp_head');
remove_action( 'wp_head', 'wp_generator' );
remove_action( 'wp_head', 'feed_links', 2 );

remove_action( 'wp_head', 'wp_shortlink_wp_head' );
remove_action( 'template_redirect', 'wp_shortlink_header', 11);
remove_action( 'template_redirect', 'rest_output_link_header', 11, 0);

remove_action( 'rss2_head',  'the_generator' );
remove_action( 'rss_head',   'the_generator' );
remove_action( 'rdf_header', 'the_generator' );
remove_action( 'atom_head',  'the_generator' );
remove_action( 'opml_head',  'the_generator' );
remove_action( 'app_head',   'the_generator' );
remove_action( 'comments_atom_head', 'the_generator' );
remove_action( 'commentsrss2_head',  'the_generator' );
```

