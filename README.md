# Embed GitHub Gist

Embed GitHub Gists into WordPress.

You can find [Embed GitHub Gist](http://wordpress.org/extend/plugins/embed-github-gist/)
at the [WordPress Plugin Directory](http://wordpress.org/extend/plugins/).


## Description

Embed [GitHub](http://github.com/) [Gists](http://gist.github.com) into
WordPress. Provides a shortcode for posts and pages but also has the ability
to embed by hand in the event that a Gist needs to be embedded somewhere in
the page that does not pass through the shortcode filters.

Examples:

 * `[gist id=546764]`
 * `[gist id=546764 file=file.txt]`
 * `[gist id=546764 file=file.txt bump=1]`
 * `[gist]http://gist.github.com/546764[/gist]`


Cache is implemented with the Transients API to minimize delay on loading
content. Default TTL (time to live) is 86400 seconds or one day.

If `json_decode` is available, the HTML markup for the source code will be
injected into the post inline. This will ensure that the code is available to
spiders and feed readers.

If `json_decode` is not available, the standard GitHub Gist embed script
(JavaScript) is included and the raw content will be added into a `NOSCRIPT`
section wrapped as follows:

    <noscript>
    <div class="embed-github-gist-source">
    <code>
    <pre>raw code here</pre>
    </code >
    </div>
    </noscript>


## Installation

1. Download the plugin zip file
1. Unzip contents of plugin zip file
1. Upload the embed-github-gist directory to the `/wp-content/plugins/` directory
1. Activate the plugin through the 'Plugins' menu in WordPress
1. Start using the plugin by adding Gists to posts!


## Frequently Asked Questions

### How can I fix rate limit exceded errors?

Define EMBED_GISTHUB_USERNAME and EMBED_GISTHUB_PASSWORD in wp-settings.php.

### Can the cache be broken?

Yes. Use a unique bump value to force cache to update. For instance, if you have
the following:

`[gist id=546764]`

The cache can be broken by specifying a bump value:

`[gist id=546764 bump=1]`

To break the cache again later, change to a new unique bump value:

`[gist id=546764 bump=2]`

### Can I change the TTL on a Gist-by-Gist basis?

Yes. Specify a TTL (in seconds) like this:

`[gist id=546764 ttl=3600]`

### Can I embed a Gist outside of a post or a page?

Yes.

`<?php echo embed_github_gist(546764); ?>`

### Can I display a specific file from my gist?

Ues. You can use the `file` parameter:

`[gist id=546764 file=file.txt]`


## Community

If you have questions or want to help out, join us in the
[#dflydev](irc://irc.freenode.net/#dflydev) channel on irc.freenode.net.
