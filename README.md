# Simple Guide to Start a Project with Node.js and TypeScript

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)

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
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@eslint/js": "^9.9.1",
    "eslint": "^9.9.1",
    "globals": "^15.9.0",
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
npx eslint --init
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

## Usage

### Eslint

```bash
pnpm lint
```

### Run the project

> Prerequisites:
> Have a `src/index.ts`, etc.
> Install the dependencies

```bash
pnpm start
```

> Compiles the project and runs the file `dist/index.js`

---

Made with :open_hands: by [Rapax](https://rapax.dev)

Tips are welcome through Lightning Zap to :zap:**rapax@lawallet.ar**.
