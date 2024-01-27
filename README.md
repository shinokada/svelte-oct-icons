# Svelte Oct

<div class="flex gap-2 my-8">
<a href="https://github.com/sponsors/shinokada" target="_blank"><img src="https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86" alt="sponsor" ></a>
<a href="https://www.npmjs.com/package/svelte-oct" rel="nofollow" target="_blank"><img src="https://img.shields.io/npm/v/svelte-oct" alt="npm" ></a>
<a href="https://twitter.com/shinokada" rel="nofollow" target="_blank"><img src="https://img.shields.io/badge/created%20by-@shinokada-4BBAAB.svg" alt="Created by Shin Okada" ></a>
<a href="https://opensource.org/licenses/MIT" rel="nofollow" target="_blank"><img src="https://img.shields.io/github/license/shinokada/svelte-oct" alt="License" ></a>
<a href="https://www.npmjs.com/package/svelte-oct" rel="nofollow" target="_blank"><img src="https://img.shields.io/npm/dw/svelte-oct.svg" alt="npm" ></a>
</div>

500+ SVG [Octicons](https://github.com/primer/octicons) components for Svelte.

Thank you for considering my open-source package. If you use it in a commercial project, please support me by sponsoring me on GitHub: https://github.com/sponsors/shinokada. Your support helps me maintain and improve this package for the benefit of the community.

## Repo

[GitHub Repo](https://github.com/shinokada/svelte-oct)

## Original source

[primer/octicons](https://github.com/primer/octicons)

## License

[Svelte-Oct License](https://github.com/shinokada/svelte-oct/blob/main/LICENSE)

[primer/octicons LICENSE](https://github.com/primer/octicons/blob/main/LICENSE)

## Installation

```sh
pnpm i -D svelte-oct
```

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

If you need only a few icons from this library in your Svelte app, import them directly. This can optimize compilation speed and improve performance by reducing the amount of code processed during compilation.

```html
<script>
  import Archive16 from 'svelte-oct/Archive16.svelte';
</script>

<Archive16 />
```

## Props

- size = ctx.size || '24';
- role = ctx.role || 'img';
- color = ctx.color || 'currentColor';
- ariaLabel = 'file name';

## IDE support

If you are using an LSP-compatible editor, such as VSCode, Atom, Sublime Text, or Neovim, hovering over a component name will display a documentation link, features, props, events, and an example.

## Size

Use the `size` prop to change the size of icons.

```html
<Accessibility16 size="40" />
<Alert16 size="50" />
<Archive16 size="60" />
```

If you are using Tailwind CSS, you can add a custom size using Tailwind CSS by including the desired classes in the class prop. For example:

```html
<Accessibility16 class="shrink-0 h-20 w-20" />
```

## Setting Global Icon using setContext

You can establish global icon preferences in your Svelte application using `setContext`. This allows you to configure icon-related properties once and share them across multiple components. Here's how you can do it:

```html
<script>
  import { setContext } from 'svelte';

  // Define your global icon settings
  const iconCtx = {
    size: '100', // Icon size in pixels
    color: '#ff4488', // Icon color in hexadecimal or CSS color name
    role: 'svg icon image' // Accessible role for the icon
  };
  setContext('iconCtx', iconCtx);
</script>
```

The `size`, `color`, and `role` properties are optional, allowing you to fine-tune the appearance and accessibility of your icons as needed.

If you set `size`, icons can be customized with different colors. For example:

```html
<script>
  import { setContext } from 'svelte';
  import { Accessibility16 } from 'svelte-oct';
  const iconCtx = {
    size: '50'
  };
  setContext('iconCtx', iconCtx);
</script>

<Accessibility16 color="#ff4488" />
```

Remember that you can set only one or two of these properties, allowing you to tailor icon settings to your specific design and accessibility requirements.

Feel free to mix and match these properties as needed to create visually appealing and accessible icons in your Svelte application.

## Creating a Default Icon Setting

You can create a config file, `/src/lib/icon.config.json`.

The `Icon` component serves as a wrapper for svelte:component, allowing you to establish a global default setting or expand the capabilities of a component.

To create a default global icon setting, follow these steps:

### Configuration File

Start by creating a configuration file named `/src/lib/icon.config.json` with the following structure:

```json
{
  "config1": {
    "size": 40,
    "color": "#FF5733"
  },
  "config2": {
    "size": 50,
    "color": "#445533"
  }
}
```

In this JSON file, you can define different configurations (config1 and config2 in this case) for your icons, specifying attributes like size, variation, and color.

### Implementation

In your Svelte page file, make use of the configurations from the JSON file:

```html
<script lang="ts">
  type IconConfig = {
    config1: {
      size: number;
      color: string;
    };
    config2: {
      size: number;
      color: string;
    };
  };
  import config from '$lib/icon.config.json';
  import { Icon, Accessibility16, Alert16 } from 'svelte-oct';

  const iconConfig: IconConfig = config;
  const config1 = iconConfig.config1;
  const config2 = iconConfig.config2;
</script>

<Icon {...config1} icon="{Accessibility16}" />
<Icon {...config2} icon="{Alert16}" />
```

We import the configurations from the JSON file and assign them to config1 and config2. We then utilize the Icon component with the spread attributes `{...config1}` and `{...config2}` to apply the respective configurations to each icon.

### Custom Default Icon

If you wish to create a custom default icon, you can follow these steps:

Create a Svelte component named `src/lib/MyIcon.svelte`:

```html
<script lang="ts">
  import type { ComponentType } from 'svelte';
  const config = {
    size: 30,
    color: '#FF5733'
  };
  import { Icon } from 'svelte-oct';
  export let icon: ComponentType;
</script>

<Icon {...config} {icon} />
```

This component, `MyIcon.svelte`, accepts an `icon` prop which you can use to pass in the specific icon component you want to display. The default configuration is also applied to the icon.

### Implementation in a Page

To use your custom default icon in a Svelte page, do the following:

```html
<script>
  import MyIcon from '$lib/MyIcon.svelte';
  import { Accessibility16 } from 'svelte-oct';
</script>

<MyIcon icon="{Accessibility16}" />
```

Here, we import the `MyIcon` component and the `Accessibility16` icon. By passing the `Accessibility16` icon to the `icon` prop of MyIcon, you apply the default configuration to the icon.

## CSS HEX Colors

Use the `color` prop to change colors with HEX color code.

```html
<Accessibility16 color="#c61515" />
<Alert16 color="#3759e5" />
<Archive16 color="#3fe537" />
```

## CSS framworks suport

You can apply CSS framework color and other attributes directly to the icon component or its parent tag using the `class` prop.

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

## Events

All icons have the following events:

- on:click
- on:keydown
- on:keyup
- on:focus
- on:blur
- on:mouseenter
- on:mouseleave
- on:mouseover
- on:mouseout

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

[Svelte-Icon-Sets](https://svelte-svg-icons.vercel.app/)
