## Description

Looks for <item_option> elements in your story and creates clikcable links to interact with your story.

To use this code in your story, copy the "Code" snippet to a new Passage titled "Item Options". To use it within a passage, create <item_option> elements like this:

```
<item_option
	data-item="sandwhich"
	data-text="You give the elf your sandwhich"
/>
```

The `data-item` attribute will check that you have this item in your inventory and display a clickable link with the `data-text` text. Make sure to run this script by invoking the code within your passage using:

```
<%= window.story.render("Item Options") %>
```

## Code

```
<div id="item-options"></div>

<style>
	.item-option {
		display: block;
		cursor: pointer;
	}
</style>

<%
	// Loop through <item_option> elements and create clickable links
	$(function() {
		$("item_option").each(function() {
			var optionLink = $(`
				<a
					class="item-option"
				>
					${$(this).data('text')}
				</a>
			`);

			if (s.inventory[$(this).data('item')] && s.inventory[$(this).data('item')].active) {
				$("#item-options").append(optionLink);
			}
		});
	})
%>
```
