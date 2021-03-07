Looks for <pickup> elements in your story and creates clikcable items you can add to your "inventory" global object.

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
