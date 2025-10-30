# ChatApp
Using Vite with React

Vite provides a default plugin that makes working with React super fast and smooth. It helps with quick updates during development, handles JSX automatically, and lets you customize Babel if needed. The plugin is lightweight but powerful enough for most setups.
This project is built using React with Vite as the build tool to make development faster and smoother. Vite provides features like quick Hot Module Reloading (Fast Refresh) and optimized builds, which help improve performance during both development and deployment. The setup uses the official React plugin for Vite, enabling automatic JSX runtime and allowing custom Babel configurations when needed. Overall, this setup offers a lightweight and modern environment that’s easy to maintain and great for learning as well as building real-world applications.


















Basic configuration for using React in a Vite project:

// vite.config.js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
})
1. include / exclude

By default, Vite works with .js, .jsx, .ts, and .tsx files while ignoring node_modules/.


import mdx from '@mdx-js/rollup'

export default defineConfig({
  plugins: [
    { enforce: 'pre', ...mdx() },
    react({ include: /\.(mdx|js|jsx|ts|tsx)$/ }),
  ],
})

2. jsxImportSource

Where JSX is imported from.
Emotion for styling:

react({ jsxImportSource: '@emotion/react' })

3. jsxRuntime

The plugin uses the automatic JSX runtime by default, but if something doesn’t work as expected, you can switch to the classic one:

react({ jsxRuntime: 'classic' })

4. babel

react({
  babel: {
    presets: [...],
    plugins: [...],
    babelrc: true,
    configFile: true,
  },
})


Note: When no custom Babel plugins are used, Vite relies on esbuild, which makes builds much faster.

Experimental Syntax

react({
  babel: {
    parserOpts: {
      plugins: ['decorators-legacy'],
    },
  },
})


TypeScript syntax is supported automatically, so you don’t need to do anything extra for that.

React Refresh Host (For Module Federation)


react({ reactRefreshHost: 'http://localhost:3000' })


This ensures that the hot reloading works across both apps smoothly.

SSR Note

For server-side rendering (SSR) projects 

import '@vitejs/plugin-react/preamble'
