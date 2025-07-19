# React + JavaScript + Vite

This template provides a minimal setup to get React working in Vite with Hot Module Replacement (HMR) and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint Configuration

If you are developing a production application, we recommend updating the ESLint configuration to include robust lint rules for JavaScript and React:

```javascript
// eslint.config.js
import eslint from '@eslint/js'
import globals from 'globals'

export default [
  {
    ignores: ['dist'],
  },
  {
    files: ['**/*.{js,jsx}'],
    languageOptions:appearance: {
      parserOptions: {
        ecmaVersion: 'latest',
        sourceType: 'module',
        ecmaFeatures: {
          jsx: true,
        },
      },
      globals: {
        ...globals.browser,
        ...globals.node,
      },
    },
    extends: [
      'eslint:recommended',
      // Add other configurations as needed
    ],
    rules: {
      'no-unused-vars': ['error', { vars: 'all', args: 'after-used', ignoreRestSiblings: false }],
    },
  },
]
```

You can also install eslint-plugin-react and eslint-plugin-react-hooks for React-specific lint rules:

```javascript
// eslint.config.js
import eslint from '@eslint/js'
import react from 'eslint-plugin-react'
import reactHooks from 'eslint-plugin-react-hooks'
import globals from 'globals'

export default [
  {
    ignores: ['dist'],
  },
  {
    files: ['**/*.{js,jsx}'],
    languageOptions: {
      parserOptions: {
        ecmaVersion: 'latest',
        sourceType: 'module',
        ecmaFeatures: {
          jsx: true,
        },
      },
      globals: {
        ...globals.browser,
        ...globals.node,
      },
    },
    plugins: {
      react,
      'react-hooks': reactHooks,
    },
    extends: [
      'eslint:recommended',
      'plugin:react/recommended',
      'plugin:react-hooks/recommended',
    ],
    rules: {
      'react/prop-types': 'off', // Disable prop-types if not using them
      'react/jsx-uses-react': 'off', // Not needed with React 17+ JSX Transform
      'react/react-in-jsx-scope': 'off', // Not needed with React 17+ JSX Transform
    },
    settings: {
      react: {
        version: 'detect', // Automatically detect React version
      },
    },
  },
]
```