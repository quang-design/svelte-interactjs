# Svelte InteractJS

A modern SvelteKit application demonstrating the integration of interact.js for creating draggable and resizable elements using Svelte 5's new reactivity system.

## Features

- **Draggable Elements**: Easily create draggable components with position tracking
- **Resizable Elements**: Add resizable functionality to any component
- **Svelte 5 Integration**: Utilizes Svelte 5's new reactivity system with `$state` and `$effect`
- **TypeScript Support**: Fully typed for better developer experience
- **Tailwind CSS 4.0**: Modern styling with the latest Tailwind features

## Getting Started

### Prerequisites

- Node.js (v18+)
- npm, pnpm, or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/quang-design/svelte-interactjs.git
cd svelte-interactjs

# Install dependencies
npm install
# or
pnpm install
# or
yarn install
```

### Development

Start the development server:

```bash
npm run dev

# Or start the server and open the app in a new browser tab
npm run dev -- --open
```

### Building for Production

Create a production build:

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

## Usage Example

```svelte
<script lang="ts">
  import interact from 'interactjs';
  import type { Action } from 'svelte/action';

  // Use Svelte 5's reactive state
  const position = $state({ x: 0, y: 0 });

  // Create a Svelte action for draggable functionality
  const draggable: Action<HTMLDivElement> = (node) => {
    // Implementation details...
    
    $effect(() => {
      const interaction = interact(node)
        .draggable({
          // Draggable options...
        })
        .resizable({
          // Resizable options...
        });

      return () => {
        interaction.unset();
      };
    });
  };
</script>

<div use:draggable class="your-styling-here">
  Draggable and Resizable Element
</div>
```

## Project Structure

- `src/routes/` - SvelteKit routes
- `src/lib/` - Reusable components and utilities
- `static/` - Static assets

## Technologies

- [SvelteKit](https://kit.svelte.dev/) - Full-stack Svelte framework
- [Svelte 5](https://svelte.dev/) - Component framework with runes
- [interact.js](https://interactjs.io/) - JavaScript drag and drop, resizing, and multi-touch gestures
- [TypeScript](https://www.typescriptlang.org/) - Type safety
- [Tailwind CSS 4.0](https://tailwindcss.com/) - Utility-first CSS framework

## License

MIT

## Acknowledgements

- [interact.js Documentation](https://interactjs.io/docs/)
- [Svelte 5 Documentation](https://svelte.dev/docs/runes)
