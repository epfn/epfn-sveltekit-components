# EPFN Components for SvelteKit

Opinionated SvelteKit components for my personal purposes.

## Installation

```
npm i epfn-sveltekit-components
```

## Importing component

```js
import { Drawer } from 'epfn-sveltekit-components';
```

## Recommendation

Components have no CSS reset, use Tailwind: https://tailwindcss.com/docs/guides/sveltekit

## Drawer

Headless-like side appearing drawer with backdrop. You must provide content (with styles) for button and drawer via slots. Button position is controlled by putting **Drawer Component** anywhere you like. Drawer position is controlled via **position** prop.

### Props

| prop       | description                                                                                                                                             | type            | default value |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------------- |
| width      | width of drawer in px                                                                                                                                   | number          | 260           |
| position   | position of drawer                                                                                                                                      | "left", "right" | "left"        |
| duration   | duration of drawer animation in ms                                                                                                                      | number          | 150           |
| breakpoint | max window width in px when drawer will be visible to prevent unexpected behavior (actual drawer visibility must be controlled by parent component/tag) | number, false   | false         |

### Slots

| slot         | description                                                                |
| ------------ | -------------------------------------------------------------------------- |
| button-open  | content inside button when drawer is not visible, usually "hamburger" icon |
| button-close | content inside button when drawer is visible, usually "x" icon             |
| content      | content inside drawer                                                      |

### Styling

| CSS variable     | description       | default value       |
| ---------------- | ----------------- | ------------------- |
| --backdrop-color | color of backdrop | rgba(0, 0, 0, 0.75) |
