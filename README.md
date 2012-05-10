# jQuery Multipage Form Plugin

Sometimes, you have a lot of form fields, and you need
to break them up into multiple pages.  This plugin does that!

[Get it from Github](https://github.com/xoxco/jQuery-multipage-form)

[View Demo](http://xoxco.com/projects/code/multipage/)

[Test it yourself using this jsFiddle Demo](http://jsfiddle.net/eJKQn/)

Created by [XOXCO](http://xoxco.com)


By default, it will take all of the `<fieldset>` tags in your form,
and turn them into individual pages.  The user will start at
the first page, and be stepped through each page, until they
reach the final page.  The plugin will even generate clever 
"Next" and "Back" buttons based on your <legend> tags.

You can optionally pass in functions to generate different kinds
of navigation.  It is easy (and examples are provided) to make
a tabbed form instead of a paginated form, for example.  You can
replace the navigation, the state handling function, even the
transition between one page and another.

## Instructions

First, add the Javascript and CSS files to your <head> tag:

	<script src="jquery.multipage.js"></script>
	<link rel="stylesheet" type="text/css" href="jquery.multipage.css" />

Then, make sure you wrap your the elements in your form within `<fieldset>` tags
that represent the pages you want to create.  Each fieldset should have a
an id attribute, which you can use to target the page, and a <legend> tag,
which defines the page's title.

Inside each fieldset, you can design your form as per usual!

At the very end of your form, include a submit button that is OUTSIDE
of the last `<fieldset>` tag.  If you don't, one will be provided for you.


Now, your form is set!  To turn it into a multipage form, call the multipage 
jQuery method:

	$('#myform').multipage();

You may also call multipage() with a variety of options.  
The full set of options is as follows:

	$('#myform').multipage({
		'stayLinkable': false, 		// whether or not the id of the page will be appended to the url as a hashtag for permalinking purposes
		'submitLabel': 'Submit',	// default label for the last page's submit button, if not included in form
		'hideLegend': false, 		// should the plugin hide the <legend> tags?  useful in concert with externally generated nav
		'hideSubmit': true, 		// should the plugin hide the submit button?
		'generateNavigation': true,	// should the plugin generate its own navigation buttons?
		'activeDot': '&nbsp;&#x25CF;',			// the dot used to represent an active page in the nav
		'inactiveDot': '&nbsp;&middot;',		// the dot used to represent an inactive page in the nav
		'navigationFunction': function(pages){},		// a function that generates the nav, receives array of pages
		'stateFunction': function(page){},		// a function that shows what page the user is viewing, receives current page #
		'transitionFunction': function(from,to){} // a function that transitions from one page $(from) to another $(to)
	});


Once you've turned your form into a magical multipager, you can 
access the pages via the following functions:

	// go to the first page
	$('#myform').gotofirst();

	// go to the last page
	$('#myform').gotolast();

	// go to page by number or id
	$('#myform').gotopage(1);
	$('#myform').gotogopage(2);
	$('#myform').gotopage('#about');


	// go to the next page
	$('#myform').nextpage();

	// go to the previous page
	$('#myform').prevpage();

	// get an array of pages
	var pages = $('#myform').getPages();


## Feature Roadmap

* Form should be able to validate on a page by page basis
	* Validation function should receive the whole fieldset AND the page #
	* Option to turn off "always forward" style progression where you have to validate first before proceeding	
	* Option to disable next button til form is valid
	
* Tab order should make sense
