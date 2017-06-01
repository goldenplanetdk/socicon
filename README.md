![socicon logo](http://www.socicon.com/static/img/logo.svg)

# socicon font

Social icons font is downloaded from http://www.socicon.com/download.php
Based on `v3.5.2`  *v2017.05*

Reason behind creating this repo is that [on NPM](https://www.npmjs.com/search?q=socicon) 
there was only [one library](https://www.npmjs.com/package/socicon) with an outdated version `3.0.5` of the socicon. 
It had completely different character codes and that broke our frontend.

# Generating rules for icons

Whenever socicon version is updated 
(e.g. new icons added, changed character codes, icon colors) 
navigate to [Socicon home page](http://www.socicon.com/chart.php).
Then in the DevTools execute following code:

```js
{
	let rules = '';

	$('.icons').each(function() {

		const $icon = $(this);
		const selector = '.' + $icon.find('.usage').text().match(/"(.*)"/)[1];
		const color = $icon.find('.color').text();
		const charCode = $icon.find('.unicode').text();

		rules += `${selector} { .socicon-colors(${color}); &:before { content: '${charCode}'; } }\n`;
	});


	console.log(rules);
	copy(rules);
	console.log('NOTE: Rules are Copied to Clipboard');
}
```

Then copy paste it to `obb-socicon.less`

In **PhpStorm**:
- Sort the lines with `Edit` > `Sort Lines`
- Align with `Edit` > `String Manipulation` > `Align` > `Align to Columns` > `{`. 
You will need to have the **String Manipulation** plugin installed.
