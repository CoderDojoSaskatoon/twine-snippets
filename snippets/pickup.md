## Description

Looks for <pickup> elements in your story and creates clikcable items you can add to your "inventory" global object.

To use this code in your story, copy the "Code" snippet to a new Passage titled "Pickup". To use it within a passage, create <pickup> elements like this:

```
<pickup
	data-name="sandwhich"
	data-description="Mmm, bologna!"
	data-exclusive="You pick up the sandwhich, better not crush it!"
/>
```

The `data-name` and `data-description` are used in the inventory modal. The `data-exclusive` tag ensures that you can only select one out of a choice of items and then displays that pickup text.

Make sure to run this script by invoking the code within your passage using:

```
<%= window.story.render("Pickup") %>
```

## Code

```
<div id="pickup-items"></div>

<style>
	.item {
		display: block;
		cursor: pointer;
	}
</style>

<%
	var pickUpItem = function() {
		s.inventory[$(this).data("item")] = {
			active: true,
			description: $(this).data("description")
		};

		if ($(this).data("exclusive")) {
			$("#pickup-items").replaceWith(
				`<div>${$(this).data("exclusive")}</div>`
			);
		}

		$(this).hide();
	}

	$(function() {
		$("pickup").each(function() {
			var itemEl = $(
				`<a
					class="item"
					data-item="${$(this).data('name')}"
					data-description="${$(this).data('description')}"
					data-exclusive="${$(this).data('exclusive')}"
				>
					Pick up the ${$(this).data("name")}
				</a>`
			);

			itemEl.click(pickUpItem);

			$("#pickup-items").append(itemEl)
		});
	});
%>
```
