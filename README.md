<h1 align="center">Svelte Oct</h1>

<p align="center">
<a href="https://svelte-oct.codewithshin.com/">Svelte-Oct</a>
</p>

<p align="center">
<a href="https://github.com/sponsors/shinokada" target="_blank"><img src="https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86" height="25"></a>
<a href="https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps" target="_blank"><img src="https://img.shields.io/badge/PWA-enabled-brightgreen" alt="PWA Shield" height="25">
</a>
<a href="https://www.npmjs.com/package/svelte-oct" rel="nofollow" target="_blank"><img src="https://img.shields.io/npm/v/svelte-oct" alt="npm" height="25"></a>
<a href="https://twitter.com/shinokada" rel="nofollow" target="_blank"><img src="https://img.shields.io/badge/created%20by-@shinokada-4BBAAB.svg" alt="Created by Shin Okada" height="25"></a>
<a href="https://opensource.org/licenses/MIT" rel="nofollow" target="_blank"><img src="https://img.shields.io/github/license/shinokada/svelte-oct" alt="License" height="25"></a>
<a href="https://www.npmjs.com/package/svelte-oct" rel="nofollow" target="_blank"><img src="https://img.shields.io/npm/dw/svelte-oct.svg" alt="npm" height="25"></a>
</p>

500+ SVG [Octicons](https://github.com/primer/octicons) components for Svelte. Svelte-oct icons support major CSS frameworks using the `class` props.

Thank you for considering my open-source package. If you use it in a commercial project, please support me by sponsoring me on GitHub: https://github.com/sponsors/shinokada. Your support helps me maintain and improve this package for the benefit of the community.

<p align="center">
<img width="650" src="/static/images/oct-650-1050-optimized.png" />
</p>

## Icon name list

[Icon list](/icon-list.md)

## Icon images

[Icon images](/icon-images.md)

## Installation

```sh
npm i -D svelte-oct
```

## REPL

[Demo](https://svelte.dev/repl/fccdaf257870448bbb6b924fda6c3a5e)

## Usages

In a svelte file:

```html
<script>
  import { Accessibility16, Alert16, Archive16 } from 'svelte-oct';
</script>

<Accessibility16 />
<Alert16 />
<Archive16 />
```

## Faster compiling

If you only need to use a couple of icons from this library in your Svelte app, importing it directly. This can help optimize compilation speed. 
By importing only what you need, you can reduce the amount of code that needs to be processed, which can improve overall performance.


```html
<script>
  import Archive16 from 'svelte-oct/Archive16.svelte';
</script>

<Archive16 />
```

If you are TypeScript user, install **typescript version 5.0.0 or above**.

As of March 2023, the `typescript@beta` version is now available:

```sh
pnpm i -D typescript@beta
```

To avoid any complaints from the editor, add `node16` or `nodenext` to `moduleResolution` in your tsconfig.json file.

```json
{
  //...
  "compilerOptions": {
    // ...
    "moduleResolution": "nodenext"
  }
}
```

## Size

Use the `size` prop to change the size of icons.

```html
<Accessibility16 size="40" />
<Alert16 size="50" />
<Archive16 size="60" />
```

## CSS HEX Colors

Use the `color` prop to change colors with HEX color code.

```html
<Accessibility16 color="#c61515" />
<Alert16 color="#3759e5" />
<Archive16 color="#3fe537" />
```

## CSS framworks suport

Use the `class` prop to change size, colors and add additional css.

Tailwind CSS example:

```html
<Accessibility16 class="h-24 w-24 text-blue-700 mr-4" />
```

Bootstrap examples:

```html
<Accessibility16 class="position-absolute top-0 px-1" />
```

## Dark mode

If you are using the dark mode on your website with Tailwind CSS, add your dark mode class to the `class` prop.

Let's use `dark` for the dark mode class as an example.

```html
<Accessibility16 class="text-blue-700 dark:text-red-500" />
```

## aria-label

All icons have aria-label. For example `Accessibility16` has `aria-label="accessibility 16"`.
Use `ariaLabel` prop to modify the `aria-label` value.

```html
<Accessibility16 ariaLabel="accessibility" />
```

## Unfocusable icon

If you want to make an icon unfocusable, add `tabindex="-1"`.

```html
<Accessibility16 tabindex="-1" />
```

## Passing down other attributes

You can pass other attibutes as well.

```html
<Accessibility16 tabindex="0" />
```

## Using svelte:component

```html
<script>
  import { Accessibility16 } from 'svelte-oct';
</script>

<svelte:component this="{Accessibility16}" />
```

## Using onMount

```html
<script>
  import { Accessibility16 } from 'svelte-oct';
  import { onMount } from 'svelte';
  const props = {
    size: '50',
    color: '#ff0000'
  };
  onMount(() => {
    const icon = new Accessibility16({ target: document.body, props });
  });
</script>
```

## Import all

Use `import * as Icon from 'svelte-oct`.

```html
<script>
  import * as Icon from 'svelte-oct';
</script>

<Icon.Accessibility16 />
<Icon.Alert16 />

<h1>Size</h1>
<Icon.Accessibility16 size="30" />
<Icon.Alert16 size="40" />

<h1>CSS HEX color</h1>
<Icon.Accessibility16 color="#c61515" size="40" />

<h1>Tailwind CSS</h1>
<Icon.Accessibility16 class="text-blue-500" />
<Icon.Alert16 class="text-pink-700" />
```

## Other icons

- [Svelte-Icon-Sets](https://svelte-svg-icons.vercel.app/)

## Experience lightning-fast browsing and offline access with Our PWA

This website can be downloaded and installed on your device for offline access as a Progressive Web App.

To install a PWA, look for the "Add to Home Screen" option in the browser's menu or settings. On most mobile devices, this option can be found by visiting the website, then selecting the "Options" or "Menu" button in the browser, and looking for the "Add to Home Screen" option. On some desktop browsers, right-click on the page and select "Install".
