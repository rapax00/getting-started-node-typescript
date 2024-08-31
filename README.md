# Simple Guide to Start a Project with Node.js and TypeScript

> Guide available in [Spanish](README.es.md)

## Features

- [pnpm](https://pnpm.io/) to manage dependencies
- [TypeScript](https://typescriptlang.org/)
- [ESlint](https://eslint.org/) for syntax errors
- [Prettier](https://prettier.io/) to format the code

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
  - [ESlint](#eslint)
  - [Prettier](#prettier)
  - [Run the project](#run-the-project)

## Configuration

1. Create a directory for the project

```bash
mkdir node_project
cd node_project
```

2. Initialize the project with pnpm

```bash
pnpm init
```

Copy the following and paste it into `package.json`.

```json
{
  "name": "node_project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "tsc && node dist/index.js",
    "lint": "eslint .",
    "format": "pnpm exec prettier . --write",
    "format-spec": "prettier --write",
    "check": "pnpm exec prettier . --check",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@eslint/js": "^9.9.1",
    "eslint": "^9.9.1",
    "globals": "^15.9.0",
    "prettier": "3.3.3",
    "typescript": "^5.5.4",
    "typescript-eslint": "^8.3.0"
  }
}
```

3. Create a configuration file for TypeScript

```bash
touch tsconfig.json
```

Copy the following and paste it into `tsconfig.json`.

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "esModuleInterop": true,
    "target": "es6",
    "moduleResolution": "node",
    "sourceMap": true,
    "outDir": "dist",
    "strict": true,
    "noImplicitAny": true,
    "skipLibCheck": true
  },
  "lib": ["es2015"],
  "include": ["**/*"],
  "exclude": ["node_modules", "dist"]
}
```

4. Install eslint

```bash
pnpm install --save-dev eslint
```

Initialize eslint

```bash
pnpm eslint --init
```

Copy the following and paste it into `eslint.config.mjs`.

```javascript
import globals from 'globals';
import pluginJs from '@eslint/js';
import tseslint from 'typescript-eslint';

export default [
  { files: ['**/*.{js,mjs,cjs,ts}'] },
  { ignores: ['node_modules', 'dist'] },
  { languageOptions: { globals: globals.node } },
  pluginJs.configs.recommended,
  ...tseslint.configs.recommended,
];
```

5. Install prettier

```bash
pnpm install --save-dev prettier
```

Create a configuration file for prettier

```bash
touch .prettierrc
```

Copy the following and paste it into `.prettierrc`.

```json
{
  "printWidth": 80,
  "tabWidth": 4,
  "useTabs": false,
  "semi": true,
  "singleQuote": true,
  "trailingComma": "es5",
  "bracketSpacing": true,
  "jsxBracketSameLine": false,
  "arrowParens": "always"
}
```

Create an ignore file for Prettier

```bash
touch .prettierignore
```

Copy the following and paste it into `.prettierignore`.

```txt
node_modules
dist
```

> Prettier will also follow rules specified in .gitignore if it exists in the same directory from which it is executed.

## Usage

### ESLint

```bash
pnpm lint
```

### Prettier

Format the code

```bash
pnpm format
```

Format the specific folder or file

```bash
pnpm format-spec <path>
```

Format the specific test file

```bash
pnpm format-spec <ruta/**/*.test.js>
```

Check if the code is formatted correctly

```bash
pnpm check
```

### Run the project

> Prerequisites:
> - Have a `src/index.ts`, etc.
> - Install the dependencies

```bash
pnpm start
```

> Compiles the project and runs the file `dist/index.js`

---

Made with :open_hands: by [Rapax](https://rapax.dev)

Tips are welcome through Lightning Zap to :zap:**rapax@lawallet.ar**.
