## Description

Adds an "Inventory" button to your passages which loops through items in your "intentory" global object, and prints their name and description.

To use this code in your story, copy the "Code" snippet to a new Passage titled "Inventory" and make sure to run this script by invoking the code within your passage using:

```
<%= window.story.render("Inventory") %>
```

## Code

```
<button id="inventory-button">Inventory</button>

<div id="inventory-modal" class="modal">
  <!-- Modal content -->
  <div class="modal-content">
    <span id="modal-close" class="close">&times;</span>
    <ul id="inventory-list"></ul>
  </div>
</div>

<style>
  /* The Modal (background) */
  .modal {
	display: none; /* Hidden by default */
	position: fixed; /* Stay in place */
	z-index: 1; /* Sit on top */
	left: 0;
	top: 0;
	width: 100%; /* Full width */
	height: 100%; /* Full height */
	overflow: auto; /* Enable scroll if needed */
	background-color: rgb(0,0,0); /* Fallback color */
	background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
  }

  /* Modal Content/Box */
  .modal-content {
	background-color: #fefefe;
	margin: 15% auto; /* 15% from the top and centered */
	padding: 20px;
	border: 1px solid #888;
	width: 80%; /* Could be more or less, depending on screen size */
  }

  /* The Close Button */
  .close {
	color: #aaa;
	float: right;
	font-size: 28px;
	font-weight: bold;
  }

  .close:hover,
  .close:focus {
	color: black;
	text-decoration: none;
	cursor: pointer;
  }
</style>

<%
	$(function() {
		// Declare inventory object
		if (!s.inventory) {
			s.inventory = {};
		}

		// When the Inventory button is clicked
		$("#inventory-button").click(function() {
			$("#inventory-list").children().remove();

			// Loop over the inventory object and add the items to our modal
			$.each(s.inventory, function(itemName, itemProperties) {
				if (itemProperties.active) {
					$("#inventory-list").append(
						`<li>${itemName} (${itemProperties.description})</li>`
					)
				}
			});

			$("#inventory-modal").show();
		});

		// When the "X" button is clicked
		$("#modal-close").click(function() {
			$("#inventory-modal").hide();
		});
	});
%>
```
