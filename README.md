# Svelte Swiftcursor

Svelte cursor component for creating customizable cursors.

## Installation

NPM

```bash
npm i svelte-swiftcursor
```

Yarn

```bash
yarn add svelte-swiftcursor
```

PNPM

```bash
pnpm add svelte-swiftcursor
```

## Usage

import the library

```js
import { Cursor } from 'svelte-swiftcursor';
```

And simply use it:

```html
<Cursor color="black" mixBlendMode="normal" size="{28}" />
```

To use hover effects, you can simply add a `.hoverable` class to the element you want to apply the effect to.

```html
<div class="hoverable">
	<h1>Hover me!</h1>
</div>
```

## Customization

- `size`: Number - The size of the cursor. (Default: `28`)
- `color`: String - The color of the cursor. (Default: `'black'`)
- `shape`: String - The shape of the cursor. (Default: `'circle'`)
- `mixBlendMode`: String - The mix-blend-mode of the cursor. (Default: `'none'`)
