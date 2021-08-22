## Description

Adds a right-aligned sidebar to your passages. This side bar contains three [progress bars](/snippets/progress_bar.md)

To use this code in your story, copy the "Code" snippet to a new Passage titled "Sidebar" and make sure to run this script by invoking the code within your passage using:

```
<%= window.story.render("Sidebar") %>
```

## Code
```
<!-- Right-aligned sidebar styling -->
<style>
  .sidebar {
	height: 100%;
	width: 250px;
	position: fixed;
	z-index: 1;
	top: 0;
	right: 0;
	overflow-x: hidden;
	padding-top: 20px;
	border-left: 5px double black; 
  }
</style>

<!-- Sidebar displaying three progress bars inside -->
<div class="sidebar">
	Fame
	<progressbar data-type="fame"></progressbar>
	Fear
	<progressbar data-type="fear"></progressbar>
	Fortune
	<progressbar data-type="fortune"></progressbar>
</div>

<!-- Replace each "<progressbar>" tag with HTML defined in "Progress Bar" -->
<%= window.story.render("Progress Bar") %>
```
