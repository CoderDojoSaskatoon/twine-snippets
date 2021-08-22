## Description
Replaces a `<progressbar>` tag with a div displaying a percentage value from 0 - 100%.

To use, add a snippet named "Progress Bar" and paste the code into it. Add a `<progressbar` tag with the appropriate `data-type` value and add the following render tag:
```
<%= window.story.render("Progress Bar") %>
```

See [sidebar](/snippets/sidebar.md) for examples.

## Code

```
<%
	$(function() {
		// Loop through each "<progressbar>" element and replace it with the bar elements
		$("progressbar").each(function() {
			// The data-type attribute on the <progressbar> controls which
			// window.story.state attribute to use for the bar's value
			const barType = $(this).data("type");
			const value = s[barType] || 0;
			
			// The progress bar is two elements: an outer box and an inner fill element
			// The width of the inner element is controled by the bar's value
			const progressBarEl = $(
				`<div style="width: 200px; border: 1px solid black; margin: auto;">
					<div id="${barType}-bar" style="height: 20px; width: ${value + "0%"}; background-color: black;"><div>
				</div>`
			);
			
			$(this).replaceWith(progressBarEl);
		});
	});
%>
```
