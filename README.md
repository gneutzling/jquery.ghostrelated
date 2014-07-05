jquery.ghostrelated
===================

This jQuery plugin displays a list of related posts for the Ghost blogging platform. 

## How it works

Ghost Related parses your blogs rss feed and matches the current post with posts from your blog that have any tags in common. You will need to attach the plugin to an unordered or ordered list in your post.hbs template to output the related posts

## Installation

1. Download jquery.ghostrelated.js or jquery.ghostrelated.min.js and save it to the js folder in your theme directory.
2. Include the script below `{{ghost_foot}}` in your themes default.hbs file `<script src="/assets/js/jquery.ghostrelated.min.js"></script>`
    
        {{! Ghost outputs important scripts and data with this tag (jquery is included in ghost_foot) }}
        {{ghost_foot}}
        
        <script type="text/javascript" src="/assets/js/main.js"></script>
        <script type="text/javascript" src="/assets/js/ghostrelated.min.js"></script>

3. Add an ordered or unordered list with a class identifier (related-posts is the default class identifier) in your post.hbs template file. 

            <ul class="related-posts">
            </ul>
        </footer>
        {{/post}}
        
4. Call the ghostrelated plugin on the list class identifier that you created in step 3 somewhere in your main js file

        $('.related-posts').ghostRelated();
        

## Options
The theme has some default options defined for you. Based on your theme you may need to override some of these when you initiate the plugin

            defaults = {
                feed: '/rss',
                titleClass: '.post-title',
                tagsClass: '.post-meta',
                debug: false
            }
            
#### feed:
This is the location of the rss feed for your blog. Ghost uses /rss, so you shouldn't need to change this.

#### titleClass:
This is the class identifier for the heading element for your single post title. This makes sure that the post that is currently being read does not come back as a related post.

Ghost's default casper theme uses: `<h2 class="post-title">Title of current post</h2>` by default.

#### tagsClass: 
This is the class identifier for the element that the current post tags are in. This is used to grab the current post tags and match them against other posts.

This are looks like this in casper: 

        <span class="post-meta">
            <time datetime="2014-07-03">03 Jul 2014</time> on 
            <a href="/tag/getting-started/">Getting Started</a> | 
            <a href="/tag/another-tag/">Another Tag</a>
        </span>
        
So the option uses .post-meta and the plugin looks for the anchor tags inside of it

#### debug:

If the plugin isn't returning any related posts, set this option to true. This option will output error information to the list you created to help you figure out why the plugin is failing.

## Start with custom options

            $('.related-posts').ghostRelated({
                titleClass: '.my-title',
                tagsClass: '.my-tags-class'
            });
            
            
## Roadmap
* More advanced post matching
