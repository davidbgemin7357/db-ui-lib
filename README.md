# db-ui-lib

Repositorio de desarrollo de **[db-ui-kit](projects/db-ui-kit/README.md)**, una librería de componentes UI para Angular 21 con Tailwind CSS 4, publicada en npm.

Las aplicaciones la consumen con:

```bash
npm install db-ui-kit-angular
```

La guía de instalación y configuración para las apps consumidoras está en [projects/db-ui-kit/README.md](projects/db-ui-kit/README.md). Ese archivo es también el README que se publica en npm.

## Tecnologías

| Tecnología | Versión |
|---|---|
| Angular (core, common, forms, CDK) | 21.2 |
| ng-packagr | 21 |
| TypeScript | 5.9 |
| Tailwind CSS (en la app consumidora) | 4 |
| flatpickr / Quill | 4.6 / 2 |
| Vitest + jsdom | 4 / 27 |

## Requisitos

- Node.js `^20.19`, `^22.12` o `^24`
- npm 11 o superior

## Instalación

```bash
git clone https://github.com/<usuario>/db-ui-lib.git
cd db-ui-lib
npm install
```

> El archivo `.npmrc` activa `legacy-peer-deps`, para evitar conflictos con la dependencia opcional `@angular/localize`.

## Scripts

| Script | Descripción |
|---|---|
| `npm run build` | Compila la librería en `dist/db-ui-kit` |
| `npm run watch` | Compila en modo watch (configuración development) |
| `npm test` | Ejecuta las pruebas unitarias |
| `npm run publish:lib` | Compila y publica `dist/db-ui-kit` en npm |

## Probar cambios en una app local antes de publicar

```bash
# En db-ui-lib
npm run build
cd dist/db-ui-kit
npm pack            # genera db-ui-kit-angular-<versión>.tgz

# En la app consumidora
npm install ../db-ui-lib/dist/db-ui-kit/db-ui-kit-angular-<versión>.tgz
```

## Publicar una nueva versión en npm

1. Inicia sesión una sola vez: `npm login`
2. Sube la versión en `projects/db-ui-kit/package.json` siguiendo semver (`0.0.1` → `0.0.2` para correcciones, `0.1.0` para funcionalidades nuevas, `1.0.0` para cambios incompatibles).
3. Publica:
   ```bash
   npm run publish:lib
   ```
4. En las apps consumidoras: `npm install db-ui-kit-angular@latest`

## Estructura

```
├── projects/
│   └── db-ui-kit/
│       ├── src/
│       │   ├── lib/            # Un directorio por componente (db-button, db-modal, ...)
│       │   └── public-api.ts   # Exportaciones públicas del paquete
│       ├── ng-package.json
│       ├── package.json        # package.json que se publica en npm
│       └── README.md           # README que se publica en npm
├── angular.json
├── package.json                # Workspace (privado, no se publica)
└── tsconfig.json
```
