# [svelte-mathquill](https://tristan-f-r.github.io/svelte-mathquill)

[![npm](https://img.shields.io/npm/v/svelte-mathquill)](https://npmjs.com/package/svelte-mathquill)

A wrapper around MathQuill, a very intuitive math typing editor

`npm i -D svelte-mathquill`

## Usage

Add this to your `+layout.svelte` or any wrapper file where you use MathQuill:

```html
<script>
	import { MathQuillSetup } from 'svelte-mathquill';
</script>

<MathQuillSetup />
```

This injects jQuery and MathQuill (+ styles) into the head of the document,
to begin using MathQuill in your components.

Simple example:

```html
<script lang="ts">
	import { MathQuill } from 'svelte-mathquill';

	let latex = '';
</script>

<MathQuill bind:latex="{latex}" />
<br />
<input bind:value="{latex}" />
```

## Documentation

### Properties

`autofocus: boolean` - if the element should focus on mount

`latex: string (bindable & updates)` - the content of the element

`noBorderOutline: boolean` - if styling should be applied to remove borders / outlines. **Only use if you have a wrapper that's styled (outlines help accessibility!)**

`class: string` - classes to apply to the math element

`config: MathQuillConfig (updateable)` - Apply a config to the element.

### Events

Triggers when the text is edited: `on:edit={latex => ...}`

Triggers when the enter key is pressed: `on:enter={() => ...}`

#### Direction Events (L(eft) | R(ight) | U(p) | D(own))

Triggers when the up arrow is pressed: `on:upOutOf={() => ...}`

Triggers when the down arrow is pressed: `on:downOutOf={() => ...}`

Triggers when the right / left arrows are pressed: `on:moveOutOf={("L" | "R") => ...}`

Triggers when the content is selected out of: `on:selectOutOf={("L" | "R") => ...}`

Triggers when the content is deleted: `on:deleteOutOf={("L" | "R") => ...}`

Triggers when any out of is triggered: `on:outOf={("L" | "R" | "U" | "D") => ...}`

Triggers when any out of is triggered WITHOUT deleteOutOf: `on:outOfOnly={("L" | "R" | "U" | "D") => ...}`

### Functions

Focus the element: `mathQuillElement.focus()`

Unfocus the element: `mathQuillElement.blur()`

Refresh the element: `mathQuillElement.reflow()`

Select the current element: `mathQuillElement.select()`

Clear any active selection: `mathQuillElement.clearSelection()`

Mimic a keystroke (ex Shift-Left): `mathQuillElement.keystroke(string)`

Type Text: `mathQuillElement.typedText(string)`
