# CCUI Design Tokens

DTCG-compliant design tokens for the ClearCo UI design system.

## Installation

```bash
npm install ccui-tokens
```

The `dist/` folder is automatically generated on install via postinstall hook.

## Usage

### CSS Variables

Import the single CSS file containing all tokens and themes:

```tsx
import 'ccui-tokens/css';
```

This includes:
- Shared primitives (`:root`)
- Light theme as default (`:root` + `[data-mantine-color-scheme="light"]`)
- Dark theme (`[data-mantine-color-scheme="dark"]`)

Theme switching works automatically with Mantine:

```tsx
import { MantineProvider, useMantineColorScheme } from '@mantine/core';
import 'ccui-tokens/css';

function App() {
  return (
    <MantineProvider defaultColorScheme="light">
      <YourApp />
    </MantineProvider>
  );
}

function ThemeToggle() {
  const { toggleColorScheme } = useMantineColorScheme();
  return <button onClick={toggleColorScheme}>Toggle Theme</button>;
}
```

### Tokens Studio

Compatible with the [Tokens Studio Figma plugin](https://tokens.studio/):

```
dist/tokens-studio/
├── $metadata.json
├── $themes.json
├── core/
├── semantic/
└── components/
```

## Directory Structure

```
ccui-tokens/
├── src/
│   ├── core/           # Primitive tokens
│   └── themes/         # Semantic tokens
├── dist/               # Generated (not committed)
│   ├── css/
│   │   └── ccui-tokens.css
│   └── tokens-studio/
│       ├── $metadata.json
│       ├── $themes.json
│       ├── core/
│       ├── semantic/
│       └── components/
└── scripts/
    └── build.js
```

## Development

```bash
npm run build    # Build all tokens
npm run clean    # Remove dist/
npm run watch    # Rebuild on changes
npm test         # Run tests
```

## License

MIT
