# Adjustments to WordPress 
#### December 16th 2022

A collection of useful functions, actions, and other ways to alter WordPress.

### Change default slug for Posts

The default slug is based on the initial Title. If the title is long htis can be very annoying as I personally like short paths and without basic repeating words like _the_, _and_, _I_, etc. This also prevents a slug from being longer than 6 words. You are always free to edit afterwards.

Source: https://gist.github.com/donohoe/4766b8a20cc6573de3dd3cb59df9fc32

### Disable External Embeddding

Tell modern browsers to disallow embedding of our site from other domains. 

More information: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options (developer.mozilla.org)

```
function disable_external_embedding( $headers ) {
	$headers[ 'X-Frame-Options' ] = 'SAMEORIGIN';
	return $headers;
}
add_filter( 'wp_headers', 'disable_external_embedding' );
```

### Disable FLoC

Prevent the (Chrome) browser from performing profiling for third-party trackers

```
function disable_floc( $headers ) {
		$headers[ 'Permissions-Policy' ] = 'browsing-topics=()';
		return $headers;
}
add_filter( 'wp_headers', 'disable_floc' );
```

### Remove Comments from WP Admin menu
```
function row_remove_menu_items() {
	remove_menu_page( 'edit-comments.php' );
	remove_menu_page( 'edit.php?post_type=sidebar' );
}
add_action( 'admin_menu', 'row_remove_menu_items' );
```
