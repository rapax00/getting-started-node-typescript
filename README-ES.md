# Guia simple para inciar un proyecto con Node.js y TypeScript

## Indice

- [Instalación](#instalación)
- [Configuración](#configuración)

## Configuración

1. Crear un directorio para el proyecto

```bash
mkdir node_project
cd node_project
```

2. Inicializar el proyecto con pnpm

```bash
pnpm init
```

Copiar lo siguiente y pegarlo en `package.json`.

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

3. Crear un archivo de configuración para TypeScript

```bash
touch tsconfig.json
```

Copiar lo siguiente y pegarlo en `tsconfig.json`.

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

4. Instalar eslint

```bash
pnpm install --save-dev eslint
```

Iniciar eslint

```bash
npx eslint --init
```

Copiar lo siguiente y pegarlo en `eslint.config.mjs`.

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

## Uso

### Eslint

```bash
pnpm  lint
```

### Correr el proyecto

> Paso previos:
> Tener un `src/index.ts`, etc.
> Instalar las dependencias

```bash
pnpm start
```

> Compila el proyecto y corre el archivo `dist/index.js`

---

Hecho con :open_hands: por [Rapax](https://rapax.dev)

Tips son bienvenido a través de Lightning Zap a :zap:**rapax@lawallet.ar**.
