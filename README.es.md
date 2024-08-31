# Guia simple para inciar un proyecto con Node.js y TypeScript

## Características

- [pnpm](https://pnpm.io/) para manejar las dependencias
- [TypeScript](https://typescriptlang.org/)
- [ESlint](https://eslint.org/) para errores de sintaxis
- [Prettier](https://prettier.io/) para formatear el código

## Indice

- [Instalación](#instalación)
- [Configuración](#configuración)
- [Uso](#uso)
  - [ESlint](#eslint)
  - [Prettier](#prettier)
  - [Correr el proyecto](#correr-el-proyecto)

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
    "format": "pnpm exec prettier . --write",
    "format-spec": "prettier --write",
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
pnpm eslint --init
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

5. Instalar prettier

```bash
pnpm install --save-dev prettier
```

Crear un archivo de configuración para prettier

```bash
touch .prettierrc
```

Copiar lo siguiente y pegarlo en `.prettierrc`.

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

Crear un archivo de ignore para prettier

```bash
touch .prettierignore
```

Copiar lo siguiente y pegarlo en `.prettierignore`.

```txt
node_modules
dist
```
> Prettier también seguirá las reglas especificadas en .gitignore si existe en el mismo directorio desde el que se ejecuta.

## Uso

### ESLint

```bash
pnpm lint
```

### Prettier

Formatear el código

```bash
pnpm format
```

Formatear una carpeta o archivo específico

```bash
pnpm format-spec <ruta>
```

Formatear todos los archivos de prueba

```bash
pnpm format-spec <ruta/**/*.test.js>
```

Chequear si el código está formateado

```bash
pnpm check
```

### Correr el proyecto

> Paso previos:
> - Tener un `src/index.ts`, etc.
> - Instalar las dependencias

```bash
pnpm start
```

> Compila el proyecto y corre el archivo `dist/index.js`

---

Hecho con :open_hands: por [Rapax](https://rapax.dev)

Tips son bienvenido a través de Lightning Zap a :zap:**rapax@lawallet.ar**.
