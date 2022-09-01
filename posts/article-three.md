---
id: 1003
title: Article three
categories: [code]
# tags: []
published: 2022-04-22
author: Achim Vedam, @vedamart
descr: CSS-Variablen mit Javascript on-the-fly ändern.
keywords: Svelte, Svelte-Kit, HTML, CSS, Javascript
# series:
views: 245
likes: 14
---

Mit einer simplen Javascript-Funktion können in CSS angelegte Variablen ausgelesen oder verändert werden. Zur weiteren Verwendung.

```js
function computed(el, prop, val) {
	if (val) {
		el.style.setProperty(prop, val)
		return el
	}
	return getComputedStyle(el).getPropertyValue(prop)
}
```

Die Variablen in css anlegen:

```css
/* These "--my-custom-name:" are called css custom-properties */
body {
	--prime: #07e4b7;
	--back: #f4f4f4;
	--head: #323235;
	--color-text: #7a7a7c;
}
```

```js
// with our function these vars are accessible
// get value ...
computed(myInputEl, '--prime')

// ... and set value
computed(myInputEl, '--prime', '#f30')
```

Dies erweist sich z. B. bei der Erstellung von Themes als sehr nützlich. Das Aussehen oder die definierten Variablen können on-the-fly geändert und das Ergebnis an Ort und Stelle überprüft werden.

**Plus:** Ist ein Theme einmal auf diese Weise erstellt, kann man im Handumdrehen beliebig viele Variationen erstellen, ohne den Quellcode erneut anfassen zu müssen. Geändert werden lediglich die Werte der CSS-Variablen, in unserem Fall, die Farben.

**btw**  
Das hier für Farben verwendete Muster kann auf alle Stile angewendet werden, die CSS zu bieten hat. Schriftarten, Box-Shadows, Farbverläufe oder Rahmenstile. Happy Theming.
