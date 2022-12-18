# Modify default Slug for WordPress Posts 
#### December 18th 2022

The default slug is based on the initial Title. If the _title_ is long htis can be very annoying as I personally like short paths and without basic repeating words like _the_, _and_, _I_, etc. This also prevents the _slug_ from being longer than 6 words. You are always free to edit afterwards.

For example; if youe starting Title:

"_The small fox jumps through a simple set of 9 new burning hoops of flame_"

Instead of a default slug of:

`the-small-fox-jumps-through-a-simple-set-of-9-new-burning-hoops-of-flame`

You'd get: 

`small-fox-jumps-through-simple-set-9-new-burning-hoops-flame`

And becuase I further limit to 6 terms the final slug is:

`small-fox-jumps-through-simple-set`

First does some checks, like if the post already has a _slug_ then we won't modify it. The order of operations goes like this:

- Takes the current Title
- Removes all non-alphanumeric characters
- Removes all 1 letter occurrences (numbers ok)
- Removes all words in the list
- Limits new slug to no more than first 6 words

This happens when the post on first save, not on subsequent updates.

```php
/*
	Alter default Post slug upon first save
*/
function slug_save_post_callback( $post_id, $post, $update ) {

	if (empty($post->post_title) || !empty($post->post_name)) {
		return;
	}

	if ($post->post_type != 'post' || $post->post_status == 'auto-draft') {
		return;
	}

	$slug = preg_replace("/[^A-Za-z0-9 ]/", '', $post->post_title);
	$slug = trim(preg_replace("/(^|\s+)(\D(\s+|$))+/", ' ', $slug));

	$remove_list = array(
		'after', 'an', 'and', 'are', 'around', 'as', 'at', 'back', 'be', 'behind', 'being', 'big', 'biggest', 'but', 'by', 
		'can', 'cant', 'changed', 'did', 'do', 'drive', 'far', 'for', 'from', 'get', 'going', 'got', 'grab', 'great', 
		'had', 'has', 'hasnt', 'have', 'heres', 'his', 'how', 'in', 'into', 'is', 'its', 'just', 
		'knows', 'like', 'means', 'more', 'most', 'need', 'needs', 'new', 'not', 
		'of', 'off', 'on', 'only', 'or', 'ok', 'says', 'see', 'set', 'stay', 'still', 'story', 
		'than', 'that', 'the', 'their', 'theyre', 'this', 'to', 'use', 'used', 'using', 
		'want', 'we', 'what', 'whats', 'when', 'where', 'who', 'whom', 'why', 'will', 'with', 'wont', 'you'
	);

	foreach($remove_list as $word) {
		$slug = preg_replace("/\b$word\b/i", "", $slug);
	}

	$slug = explode("-", sanitize_title($slug));
	$slug = implode("-", array_slice($slug, 0, 6));

	if ($slug == $post->post_name) {
		return;
	}

	// Unhook this function to prevent infinite looping, restore it later
	remove_action( 'save_post', 'slug_save_post_callback', 5, 3 );

	wp_update_post(array(
		'ID'        => $post_id,
		'post_name' => $slug
	));

	add_action( 'save_post', 'slug_save_post_callback', 5, 3 );
	clean_post_cache($post_id);
}
add_action( 'save_post', 'slug_save_post_callback', 5, 3 );
```
Gist: https://gist.github.com/donohoe/4766b8a20cc6573de3dd3cb59df9fc32
