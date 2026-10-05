# db-ui-kit

Librería de componentes UI para **Angular 21**, con componentes standalone y estilos con **Tailwind CSS 4**.

## Componentes

- **Formularios:** `db-textbox`, `db-text-area`, `db-numberbox`, `db-selectbox`, `db-multi-select`, `db-checkbox`, `db-radio`, `db-switch`, `db-date-picker`, `db-file-input`, `db-html-editor`
- **Visualización:** `db-button`, `db-badge`, `db-card`, `db-data-table`, `db-gallery`, `db-tooltip`, `db-loader`
- **Feedback y diálogos:** `db-modal`, `db-alert-modal`, `db-confirm-modal`, `db-toast`

## Instalación

```bash
npm install @davidbgemin7357/db-ui-kit
```

Dependencias peer (si tu proyecto no las tiene ya):

```bash
npm install @angular/cdk flatpickr quill material-symbols
```

## Configuración en la aplicación

### 1. Tailwind CSS 4

Los componentes usan clases de Tailwind. Indica a Tailwind que escanee el paquete en tu hoja de estilos global (ajusta la ruta relativa a `node_modules`):

```css
@import "tailwindcss";
@source "../node_modules/@davidbgemin7357/db-ui-kit";
```

### 2. Tema

Los componentes usan los tokens de color del tema (`brand`, `gray`, `gray-dark`, `success`, `error`, `warning`, `orange`, `blue-light`, sombras `theme-*`, fuente `outfit`), la variante `dark` (`@custom-variant dark (&:is(.dark *));`) y las clases `db-glass-*`. Todo debe estar definido en los estilos globales de la app. Como referencia, usa el `src/styles.css` de la plantilla `angular-starter-template`.

### 3. Iconos y estilos de terceros

En `angular.json` → `styles`:

```json
"styles": [
  "src/styles.css",
  "node_modules/flatpickr/dist/flatpickr.css",
  "node_modules/quill/dist/quill.core.css"
]
```

Y en tu CSS global: `@import "material-symbols/outlined.css";`

Si usas flatpickr (lo usa `db-date-picker`), añade `"allowedCommonJsDependencies": ["flatpickr"]` en las opciones de build.

### 4. Scroll con modales

Los modales (`db-modal`, `db-confirm-modal`, `db-alert-modal`) bloquean el scroll con `body { overflow: hidden }`. Para que el contenido no se desplace al abrir o cerrar un modal:

```css
html {
  scrollbar-gutter: stable;
}
```

## Uso

```ts
import { Component } from '@angular/core';
import { DbButtonComponent } from '@davidbgemin7357/db-ui-kit';

@Component({
  selector: 'app-example',
  imports: [DbButtonComponent],
  template: `<db-button>Guardar</db-button>`,
})
export class ExampleComponent {}
```

Revisa `public-api.ts` para ver todo lo que exporta la librería.

## Licencia

MIT
