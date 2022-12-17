# Adding humans.txt for WordPress
#### December 17th 2022

Nothing earth shattering, just a standard place to start. **Bold** and _italics_.

Given enough time everything you do as a web developer will be gone. The ability to preserve any legacy is limited. All our code, our ingenuity, shameless hacks, eventually gets refactored, or deleted. The [humans.txt](https://humanstxt.org/) is one small corner where, maybe if you are lucky, you can point to after you have left the company and say _"Look, I helped build that"_.

I have been mentioned in the _humans.txt_ in a number of sites where I no longer work or have access to. A few survive still, but most don't:

- https://donohoe.dev/humans.txt - Not controversial, this site
- https://nytimes.com/humans.txt - Gone. Re-written.
- https://qz.com/humans.txt - Gone, 404
- https://newyorker.com/humans.txt - Still there!
- https://restofworld.org/humans.txt - Still there!

### Enable humans.txt

```php
<?php
/**
 * Register the rewrite rule for /humans.txt request.
 */
function add_humans_txt_rewrite() {
	add_rewrite_rule( '^humans\.txt$', 'index.php?humans_txt=true', 'top' );
}
add_action( 'init', 'add_humans_txt_rewrite', 10 );
 
/**
 * Filter the list of public query vars in order to allow the WP::parse_request
 * to register the query variable.
 *
 * @param array $public_query_vars The array of whitelisted query variables.
 *
 * @return array
 */
function add_humans_txt_query_var( $public_query_vars ) {
	$public_query_vars[] = 'humans_txt';
	return $public_query_vars;
}
add_filter( 'query_vars', 'add_humans_txt_query_var', 10, 1 );
 
/**
 * Hook the parse_request action and serve the humans.txt when custom query variable is set to 'true'.
 *
 * @param WP $wp Current WordPress environment instance
 */
function get_humans_txt_request( $wp ) {
	if ( isset( $wp->query_vars['humans_txt'] ) && 'true' === $wp->query_vars['humans_txt'] ) {
		header( 'Content-Type: text/plain' );
		echo file_get_contents( get_stylesheet_directory() . '/humans.txt' );
		exit;
	}
}
add_action( 'parse_request', 'get_humans_txt_request', 10, 1 );

```

### Write humans.txt

This is the plain-text template I would suggest. Newest team member added to top of list. As folks move on, move them to the Alumni section. I have had a few people over the years apply to jobs noting they found listings through this.

```
# TEAM

These shiny humans help direct the ones and zeros that run example.com:

    Sigourney Weaver  instagram.com/official_sigourneyweaver
    Michael Donohoe   octodon.social/@donohoe

# ALUMNI

These humans have helped us to be what we are today:

    Ed Norton         twitter.com/edwardnorton
    Peter O'Toole     peter (at) gmail dot com

# CONTACT

Help, questions, and general support:

    hello@example.com

# WORK WITH US ＼( °□° )／

Come join us, we're hiring (sometimes): 

    https://example.com/hiring/

```

I would suggest using this to create a _hoomans.txt_ to list people's dogs, but I have too much time on my hands.
