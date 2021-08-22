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
		$("progressbar").each(function() {
			const value = s[$(this).data("type")] || 0;
			const progressBarEl = $(
				`<div style="width: 200px; border: 1px solid black; margin: auto;">
					<div style="height: 20px; width: ${value + "0%"}; background-color: black;"><div>
				</div>`
			);
			
			$(this).replaceWith(progressBarEl);
		});
	});
%>
```
