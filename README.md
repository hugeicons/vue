![31c9262e-aeea-4403-9086-3c8b88885cab](https://github.com/hugeicons/hugeicons-react/assets/130147052/ff91f2f0-095a-4c6d-8942-3af4759f9021)

# @hugeicons/vue

> HugeIcons Pro Vue Component Library - Beautiful and customizable icons for your Vue applications

## What is HugeIcons?

HugeIcons is a comprehensive icon library designed for modern web and mobile applications. The free package includes 4,000+ carefully crafted icons in the Stroke Rounded style, while the pro version offers over 36,000 icons across 9 unique styles.

### Key Highlights
- **4,000+ Free Icons**: Extensive collection of Stroke Rounded icons covering essential UI elements, actions, and concepts
- **Pixel Perfect**: Every icon is crafted on a 24x24 pixel grid ensuring crisp, clear display at any size
- **Customizable**: Easily adjust colors, sizes, and styles to match your design needs
- **Regular Updates**: New icons added regularly to keep up with evolving design trends

> 📚 **Looking for Pro Icons?** Check out our comprehensive documentation at [docs.hugeicons.com](https://docs.hugeicons.com) for detailed information about pro icons, styles, and advanced usage.

![a40aa766-1b04-4a2a-a2e6-0ec3c492b96a](https://github.com/hugeicons/hugeicons-react/assets/130147052/f82c0e0e-60ae-4617-802f-812cdc7a58da)

## Table of Contents
- [What is HugeIcons?](#what-is-hugeicons)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Props](#props)
- [Examples](#examples)
  - [Basic Usage](#basic-usage)
  - [Custom Size and Color](#custom-size-and-color)
  - [Interactive Examples](#interactive-examples)
- [Performance](#performance)
- [Troubleshooting](#troubleshooting)
- [Browser Support](#browser-support)
- [Related Packages](#related-packages)
- [Pro Version](#pro-version)
- [License](#license)
- [Related](#related)

## Features

- 🎨 Customizable colors and sizes
- 💪 TypeScript support with full type definitions
- 🎯 Tree-shakeable for optimal bundle size
- 📦 Multiple bundle formats (ESM, CJS, UMD)
- ⚡ Lightweight and optimized
- 🔄 Alternate icon support for dynamic interactions

## Installation

```bash
# Using npm
npm install @hugeicons/vue @hugeicons/core-free-icons

# Using yarn
yarn add @hugeicons/vue @hugeicons/core-free-icons

# Using pnpm
pnpm add @hugeicons/vue @hugeicons/core-free-icons

# Using bun
bun add @hugeicons/vue @hugeicons/core-free-icons
```

## Usage

```vue
<template>
  <HugeiconsIcon
    :icon="SearchIcon"
    :size="24"
    color="currentColor"
    :stroke-width="1.5"
  />
</template>

<script>
import { HugeiconsIcon } from '@hugeicons/vue';
import { SearchIcon } from '@hugeicons/core-free-icons';

export default {
  components: {
    HugeiconsIcon
  },
  setup() {
    return {
      SearchIcon
    }
  }
}
</script>
```

## Props

| Prop (in template) | Prop (in script) | Type | Default | Description |
|-------------------|------------------|------|---------|-------------|
| `icon` | `icon` | `[string, Record<string, any>][]` | Required | The main icon to display (array of SVG elements and their attributes) |
| `size` | `size` | `number \| string` | `24` | Icon size in pixels. Must be a positive number. String values will be parsed to numbers |
| `stroke-width` | `strokeWidth` | `number \| undefined` | `undefined` | Width of the icon strokes. When used with `absoluteStrokeWidth`, the stroke width will be automatically scaled relative to the icon size |
| `absolute-stroke-width` | `absoluteStrokeWidth` | `boolean` | `false` | When true, the stroke width will be scaled relative to the icon size to maintain visual consistency across different sizes |
| `alt-icon` | `altIcon` | `[string, Record<string, any>][]` | `undefined` | Alternative icon that can be used for states, interactions, or animations |
| `show-alt` | `showAlt` | `boolean` | `false` | When true, displays the altIcon instead of the main icon |
| `color` | `color` | `string` | `currentColor` | Icon color (CSS color value) |

Note: 
- The component accepts all standard SVG attributes as props which will be passed to the root SVG element.
- The `size` prop accepts both numbers and strings, but strings will be parsed to numbers and must result in a positive number.
- Icon arrays are tuples of `[elementName: string, attributes: Record<string, any>][]` representing SVG elements.

## Examples

### Basic Usage
```vue
<template>
  <HugeiconsIcon :icon="SearchIcon" />
</template>

<script>
import { HugeiconsIcon } from '@hugeicons/vue';
import { SearchIcon } from '@hugeicons/core-free-icons';

export default {
  components: { HugeiconsIcon },
  setup() {
    return { SearchIcon }
  }
}
</script>
```

### Custom Size and Color
```vue
<template>
  <HugeiconsIcon
    :icon="NotificationIcon"
    :size="32"
    color="#FF5733"
  />
</template>

<script>
import { HugeiconsIcon } from '@hugeicons/vue';
import { NotificationIcon } from '@hugeicons/core-free-icons';

export default {
  components: { HugeiconsIcon },
  setup() {
    return { NotificationIcon }
  }
}
</script>
```

### Interactive Examples

#### Search Bar with Clear Button
```vue
<template>
  <div>
    <input
      v-model="searchValue"
      type="text"
      placeholder="Search..."
    />
    <HugeiconsIcon
      :icon="SearchIcon"
      :alt-icon="CloseCircleIcon"
      :show-alt="searchValue.length > 0"
      @click="clearSearch"
    />
  </div>
</template>

<script>
import { ref } from 'vue';
import { HugeiconsIcon } from '@hugeicons/vue';
import { SearchIcon, CloseCircleIcon } from '@hugeicons/core-free-icons';

export default {
  components: { HugeiconsIcon },
  setup() {
    const searchValue = ref('');
    
    const clearSearch = () => {
      if (searchValue.value.length > 0) {
        searchValue.value = '';
      }
    };

    return {
      searchValue,
      clearSearch,
      SearchIcon,
      CloseCircleIcon
    }
  }
}
</script>
```

#### Theme Toggle
```vue
<template>
  <button @click="toggleTheme">
    <HugeiconsIcon
      :icon="SunIcon"
      :alt-icon="MoonIcon"
      :show-alt="isDark"
    />
  </button>
</template>

<script>
import { ref } from 'vue';
import { HugeiconsIcon } from '@hugeicons/vue';
import { SunIcon, MoonIcon } from '@hugeicons/core-free-icons';

export default {
  components: { HugeiconsIcon },
  setup() {
    const isDark = ref(false);
    const toggleTheme = () => isDark.value = !isDark.value;

    return {
      isDark,
      toggleTheme,
      SunIcon,
      MoonIcon
    }
  }
}
</script>
```

## Performance

- **Tree-shaking**: The package is fully tree-shakeable, ensuring only the icons you use are included in your final bundle
- **Optimized SVGs**: All icons are optimized for size and performance
- **Code Splitting**: Icons can be easily code-split when using dynamic imports

## Troubleshooting

### Common Issues

1. **Icons not showing up?**
   - Make sure you've installed both `@hugeicons/vue` and `@hugeicons/core-free-icons`
   - Check that the icon names are correctly imported

2. **TypeScript errors?**
   - Ensure your `tsconfig.json` includes the necessary type definitions
   - Check that you're using the latest version of the package

3. **Bundle size concerns?**
   - Use named imports instead of importing the entire icon set
   - Implement code splitting for different sections of your app

## Browser Support

The library supports all modern browsers.

## Related Packages

- [@hugeicons/react](https://www.npmjs.com/package/@hugeicons/react) - React component
- [@hugeicons/svelte](https://www.npmjs.com/package/@hugeicons/svelte) - Svelte component
- [@hugeicons/angular](https://www.npmjs.com/package/@hugeicons/angular) - Angular component
- [@hugeicons/react-native](https://www.npmjs.com/package/@hugeicons/react-native) - React Native component

## Pro Version

> 🌟 **Want access to 36,000+ icons and 9 unique styles?** 
> Check out our [Pro Version](https://hugeicons.com/pricing) and visit [docs.hugeicons.com](https://docs.hugeicons.com) for comprehensive documentation.

### Available Pro Styles
- **Stroke Styles**
  - Stroke Rounded (`@hugeicons-pro/core-stroke-rounded`)
  - Stroke Sharp (`@hugeicons-pro/core-stroke-sharp`)
  - Stroke Standard (`@hugeicons-pro/core-stroke-standard`)
- **Solid Styles**
  - Solid Rounded (`@hugeicons-pro/core-solid-rounded`)
  - Solid Sharp (`@hugeicons-pro/core-solid-sharp`)
  - Solid Standard (`@hugeicons-pro/core-solid-standard`)
- **Special Styles**
  - Bulk Rounded (`@hugeicons-pro/core-bulk-rounded`)
  - Duotone Rounded (`@hugeicons-pro/core-duotone-rounded`)
  - Twotone Rounded (`@hugeicons-pro/core-twotone-rounded`)

## License

This project is licensed under the [MIT License](LICENSE.md).

## Related

- [@hugeicons/core-free-icons](https://www.npmjs.com/package/@hugeicons/core-free-icons) - Free icon package
- [HugeIcons Website](https://hugeicons.com) - Browse all available icons 

## Changelog

### v1.1.0
- Added `absoluteStrokeWidth` prop for consistent stroke width scaling
- Improved stroke width handling by applying it at the SVG level
- Enhanced TypeScript types and documentation

### v1.0.0
- Initial release
- Basic icon rendering functionality
- Support for customization (size, color, alternate icons)
- Full TypeScript support 