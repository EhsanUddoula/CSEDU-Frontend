React + JavaScript + Vite
This template provides a minimal setup to get React working in Vite with Hot Module Replacement (HMR) and some ESLint rules.
Currently, two official plugins are available:

@vitejs/plugin-react uses Babel for Fast Refresh
@vitejs/plugin-react-swc uses SWC for Fast Refresh

Expanding the ESLint Configuration
If you are developing a production application, we recommend updating the ESLint configuration to include robust lint rules for JavaScript and React:
// eslint.config.js
import eslint from '@eslint/js'
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
    extends: [
      // Base ESLint recommended rules for JavaScript
      'eslint:recommended',
      // Add other configurations as needed
    ],
    rules: {
      // Customize rules as needed
      'no-unused-vars': ['error', { vars: 'all', args: 'after-used', ignoreRestSiblings: false }],
    },
  },
]

You can also install eslint-plugin-react and eslint-plugin-react-hooks for React-specific lint rules:
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
      // Base ESLint recommended rules
      'eslint:recommended',
      // React-specific rules
      'plugin:react/recommended',
      // React Hooks rules
      'plugin:react-hooks/recommended',
    ],
    rules: {
      // Customize React-specific rules
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
