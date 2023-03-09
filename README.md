# EPFN Components for SvelteKit

Opinionated SvelteKit components for my personal purposes.

## Installation

```
npm i epfn-sveltekit-components
```

## Import component

```svelte
<script>
	import { Drawer } from 'epfn-sveltekit-components';
</script>
```

## Recommendation

Components have no CSS reset, use Tailwind: https://tailwindcss.com/docs/guides/sveltekit

## Drawer

Headless-like side appearing drawer with backdrop. You must provide content (with styles) for button and drawer via slots. Button position is controlled by putting **Drawer Component** anywhere you like. Drawer position is controlled via **position** prop.

### Props

| prop     | description                        | type            | default value |
| -------- | ---------------------------------- | --------------- | ------------- |
| width    | width of drawer in px              | number          | 260           |
| position | position of drawer                 | "left", "right" | "left"        |
| duration | duration of drawer animation in ms | number          | 150           |

### Slots

| slot         | description                                                                |
| ------------ | -------------------------------------------------------------------------- |
| button-open  | content inside button when drawer is not visible, usually "hamburger" icon |
| button-close | content inside button when drawer is visible, usually "x" icon             |
| content      | content inside drawer                                                      |

### Styling

| CSS variable     | description       | fallback value      |
| ---------------- | ----------------- | ------------------- |
| --backdrop-color | color of backdrop | rgba(0, 0, 0, 0.75) |

### Additional features

You can close drawer from child component via **closeDrawer** callback from context:

```svelte
<script lang="ts">
	import { getContext } from 'svelte';
	const { closeDrawer } = getContext<{ closeDrawer: () => void }>('closeDrawer');
</script>
```

## MenuDrawer

Vertical list of links with border between for drawer. Clicks on links closing drawer.

### Props

| prop  | description    | type                              | default value |
| ----- | -------------- | --------------------------------- | ------------- |
| links | array of links | { href: string; label: string }[] |               |

### Styling

| CSS variable   | description                        | fallback value |
| -------------- | ---------------------------------- | -------------- |
| --border-color | color of border between list items | gray           |

## MenuHeader

Horizontal list of links with underline on hover.

### Props

| prop  | description    | type                              | default value |
| ----- | -------------- | --------------------------------- | ------------- |
| links | array of links | { href: string; label: string }[] |               |

### Styling

| CSS variable          | description            | fallback value |
| --------------------- | ---------------------- | -------------- |
| --underline-thickness | thickness of underline | 2px            |
| --underline-offset    | offset of underline    | 20px           |
| --underline-color     | color of underline     | gray           |

## Spinner

Usual animated spinner

### Styling

| CSS variable    | description      | fallback value |
| --------------- | ---------------- | -------------- |
| --spinner-color | color of spinner | white          |

## Alerts

Vertical list of animated alerts

### Styling

You can apply additional styling from parent with data attributes: [data-type] for all items, [data-type='success'] for type "success", [data-type='error'] for type "error", [data-type='warning'] for type "warning"

### Props

| prop     | description                       | type                                                        | default value |
| -------- | --------------------------------- | ----------------------------------------------------------- | ------------- |
| items    | array of alerts                   | { text: string; type: 'success' \| 'error' \| 'warning' }[] |               |
| duration | duration of alert animation in ms | number                                                      | 200           |

| CSS variable       | description              | fallback value |
| ------------------ | ------------------------ | -------------- |
| --background-color | color of alert item      | white          |
| --svg-color        | color of alert item icon | gray           |
