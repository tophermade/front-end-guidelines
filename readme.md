
#Background

This document should serve as a guideline for all front end development. It is licensed under a Creative Commons 3.0 Share a Like license.

The document defines future friendly standards and best practices for formating HTML and CSS, with an eye towards consistency, performance, and improved maintainability. These guidelines apply only to development files, not end use files served to the client (such as compiled LESS, minified markup, etc) which should be minified.



##Misc Guidelines

###Asset Location
Scripts at the bottom, Stylesheet at the top.

###Inline Styles and JS
Don't do this. All JS must be contained within external files, except for analytics code, and css must be within the single compiled stylesheet.

	<p style="font-size: 14px; background: #ddd">Don't do this, or a pox shall be upon you.</p>

###Code Commenting
Code comments should be used to explain any code whose purpose is not immediately understood, and to indicate completion of modularized sections within the markup.

###Quotation Marks (HTML/CSS)
Attribute values should be within double quotation marks.

###Proper Separation
Structure, presentation, and behavior must be separated.

###Indentation
Indent by spaces, not tabs, 4 spaces to an indent. You can set your editor to insert 4 spaces when pressing tab.

###Capitalization
Use only lowercase characters

###Readability
Readability must be maintained over compression. Any concerns about file size can likely be resolved server side.

### Cache 
Cache everything, even ajax calls when possible. Keep in mind iOS can't cache a page, script, or css file over 25kb.



##Browser Support
Browsers are given support levels as defined below:

Level A : Chrome 16+, FF 4+, Safari 6+, Opera 11+, IE10+ full experience including animations and all enhancements.

Level B : IE9 A fully functional experience, less flash and minimal animations

Level C : IE8, FF3.5, and Pre 2011 Chrome, Safari, Opera
A functional but reduced experience. Animations will be disabled, ajax effects minimized, some visual differences.

Mobile browser support will generally be Android 2.3+, iOS 6+, Blackberry 10+, and Windows Phone 8



##Protocols

###Assets
Assets should be included in a protocol agnostic format

	http://mysite.com/asset.js | Bad
	//mysite.com/asset.js | Good 



##Encoding & Type

Files should always be UTF-8 encoded.

Doctype must always be HTML5 - <!doctype html>

The type Attribute should be omitted from stylesheets and scripts.



##Images

###Color Profiles
If the PS file you are working on contains a color profile, you must not embed that profile when exporting that image. sRGB should be the default profile, but often is not.

###Format
PNG8/24 should be used for decorative imagery and icons. JPG should be used for large decorative imagery, photos, and large backgrounds.

###Sprites
Sprites are good. Revisions happen. Implementing a sprite sheet at the tail end of a project will reduce excess in a sprite file, and reduce wasted time caused by modifications to icons or other imagery.



##Markup

### Style

	<section id="sidebar">
		<div class="module">
			<h3>Module Title</h3>
			<p>
				Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
				<a href="#">Read More</a>
			</p>
		</div>
	</section>

###Closing Tags
Closing tags should always be used within <head> or <body>, avoid self closing tags except for form elements.

###Capitalization
Never use all capitals or all lowercase in a presentational manner, rather use text-transform inside the CSS.

###Dash vs Underscore
Underscores should not be used within the markup. A more thorough discussion on this can be had, but preferences aside one should be chosen for a project to avoid confusion, and this project shall use dashes.

###Element Use
Use elements according to their intended use whenever possible, eg: paragraphs should be wrapped in the <p> tag not a <div>.

###Form Elements
Labels should not wrap their corresponding input field, but should exist before it in the markup, and reference the associated filed via the "for" attribute.

###Size Attribute
Do not assign a size value to any form fields.

###Tables
Tables should be used for tabular data, not for structural layout. When using a table be sure to use <thead>, <tbody>, and <th>/<td> tags as appropriate, and <caption> whenever possible.

###Submit Button vs Link
Submit buttons should be used when transmitting data from the client to the server, or storing data in local-storage. Links should be used when moving the user from one page to another. Javascript may be used to enhance the experience, but both links and buttons must function without.

###Inline Styles
There is never an excuse to hard code inline styles within the markup. All styles must exist within the CSS, and when necessary be modified via JS.

###Semantics
Semantic naming of all elements shall be required, visually descriptive naming is not appropriate, eg  #navigation is good while #red menu is bad.

Progressive naming my often be appropriate while maintaining semantics. For example when showing a list of employees within a company the list might be .employees with each employee inside an LI classed .employee and the employee img classed as .employee-picture with the employees name as an h3 with the class of .employee-name.

	<ul class="employees">
		<li class="employee">
			<img src="img/awesomepic.jpg" alt="Picture of Employee Name" class="employee-picture" />
			<h3 class="employee-name">Employee Name</h3>
		</li>
	</ul>

*This is just an example, you would not normally need to class every element.*


###Selectors
Selectors should be classes for any element that might ever be duplicated within a single page load, and IDs for all elements that will only exist once. Good examples are #navigation for the main site navigation and #logo for the site's logo. Selectors, whether classes or IDs should be either meaningful or generic (eg #navigation is meaningful and .module is generic).

###Child Indentation
Children of an element should be indented be indented regardless of length.

###Fallbacks
Fallbacks for any functional portion of a site must be provided. This means the site must function even without JS, and users not supporting HTML5 should be given a flash player, and failing that a direct download link the the a/v file, etc.

###HTML5 Elements
HTML5 elements should be used where possible and semantically meaningful. Navigation should be inside a <nav> tag, blog posts inside an <article>, etc.

###Form Field Validation
HTML5 form validation should be used, with a fallback in JS. This must not and should not replace server side validation.

###Modularity
Markup should be written in order to be as modular as possible, allowing it to be used within different contexts without needing additional rules within the css.



##CSS

### Style
	
	#sidebar{
		// rules here
	}

		.module{
			// rules here

			p{
				// rules here, properly nested
			}

			a{
				// rules here, properly nested
			}
		}

###Units
Pixels should be used for sizing elements, along with % for widths wherever possible.

###Type Selectors
Either target elements based on type and a class or ID. targeting based on just type, class, or ID should be sufficient.

###Hexadecimal Values
Hexadecimal color values should be lowercase, #ffffff rather than uppercase, #FFFFFF and in 3 character notation form, #fff if possible.

###Vendor Prefixes
Vendor prefixes should be managed by mixins. If a mixin doesn't exist for a use case, create a new one if it will be used more than once.

###Rule Spacing
Rules should exist on their own line, with single space following the properties colon.

###Pseudo Classes
Pseudo classes must be used only as an enhancement, no required functionality should rely on them.

###Specificity
Browsers calculate specificity along a very complicated model. A calculator may be helpful, but if the css has reached a level when a calculator is necessary a much larger issue exists. Rules should have as little specificity as possible. 

Class and ID references should not be prefixed by an element, for example nav#navigation is incorrect, while #navigation is correct.


###Nesting
When developing with LESS rules may be nested. Nesting is a fundamental of CSS preprocessors but must be used carefully. Every nested level increases specificity, for this reason do not nest more than 3 levels deep.

###Using !important
Don't. 

###Font Sizing
Fonts should be sized via px, and corresponding line heights in a relative value, eg "line-height: 1.5;". A common exception here is buttons and navigation links which often require a fixed height.

###CSS Hacks
They are rarely necessary. Use them with caution and don't forget to escape them in the LESS sheet.

###Shorthand
Shorthand is easier to read and faster. It is preferred whenever possible.



##QA

Bugs should be filed in GitHub or BitBucket.


