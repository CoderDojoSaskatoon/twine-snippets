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
