# ADMIN-AJAX

## Overview
- What is AJAX?
- How can admin-ajax be used for troubleshooting?
- Example of a simple plugin using admin-ajax to ____

## What is AJAX?

AJAX is the acronym for Asynchronous JavaScript And XML. Ajax is an Internet communications technique that allows a web page displayed in a user’s browser to request specific information from a server and display this new information on the same page without the need to reload the entire page.
[Read More](https://developer.wordpress.org/plugins/javascript/ajax/)

## Use In Troubleshooting

Discovered in troubleshooting [this ticket](https://ithemeshelp.zendesk.com/agent/tickets/545879)

Snippet to output all of the admin-ajax hooks to the `debug.log` with a timestamp:
```php
$pp_time = microtime(true);
$last_time = microtime(true);
$uuid = uniqid();

add_action('all', function() use($pp_time, $uuid, $last_time) {
	if(empty($_POST['action']) || $_POST['action'] != 'save-attachment') {
		return;
	}
	$ct = microtime(true);
	$delta = $ct - $last_time;
	$last_time = microtime(true);
	if(defined( 'DOING_AJAX' ) && DOING_AJAX && is_admin() && $delta > 3) {
	   error_log($uuid.'-'.current_filter().' '.microtime(true));
	}
});
```

