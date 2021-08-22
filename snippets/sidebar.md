```
<style>
  .sidenav {
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

<div class="sidenav">
	Fame
	<progressbar data-type="fame"></progressbar>
	Fear
	<progressbar data-type="fear"></progressbar>
	Fortune
	<progressbar data-type="fortune"></progressbar>
</div>

<%= window.story.render("Progress Bar") %>
```
