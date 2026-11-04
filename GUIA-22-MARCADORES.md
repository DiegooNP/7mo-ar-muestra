# Sistema AR de la muestra - 22 obras

## Objetivo

La muestra usará una sola aplicación web y 22 marcadores distintos.

- Marcador 01 -> Hipogrifo
- Marcador 02 -> Obra 02
- ...
- Marcador 22 -> Obra 22

Los marcadores elegidos son 4x4 BCH(13,5,5). Hay 32 identificadores disponibles, por lo que 22 obras entran sin problema.

## Por qué no usamos el mismo HIRO para todos

HIRO siempre representa el mismo marcador. Si las 22 obras tuvieran el mismo HIRO, AR.js no podría saber qué criatura corresponde a cada obra.

Con Barcode Markers cada dibujo tiene un ID numérico distinto.

## Prueba segura antes de migrar todo

El archivo `barcode-test.html` reconoce solamente el marcador ID 1 y muestra el hipogrifo.

Esto permite comprobar que:
1. la cámara reconoce el nuevo tipo de marcador;
2. el hipogrifo conserva levitación y aros;
3. la detección es suficientemente estable.

El `index.html` actual con HIRO se conserva hasta completar esta prueba.

## Impresión

Abrir `marcadores.html`.

Al imprimir:
- papel A4;
- orientación vertical;
- escala 100 %;
- no usar "Ajustar a página";
- desactivar encabezados y pies del navegador.

Cada patrón está definido a 15 cm x 15 cm.

## Configuración AR.js

La escena de Barcode Markers usa:

```html
detectionMode: mono_and_matrix;
matrixCodeType: 4x4_BCH_13_5_5;
```

Cada obra se asociará con:

```html
<a-marker type="barcode" value="N">
  <!-- contenido AR de esa obra -->
</a-marker>
```

donde N será un número de 1 a 22.

## Próximo paso

Probar primero el Marcador 01 con:

`barcode-test.html`

Si funciona correctamente, se construirá la versión final con los 22 marcadores dentro de una sola escena.
