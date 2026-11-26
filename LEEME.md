# KUBI · Filtro de eventos

Nicolás Sánchez · Realidades Expandidas · Ejercicio individual

## Qué hace

Unas gafas 3D con montura de fresa, semillas y hojas siguen la posición, el tamaño
y la orientación de la cabeza. Dos expresiones producen dos sonidos distintos:

| Gesto | Respuesta visual | Sonido |
| --- | --- | --- |
| Sonreír | Las gafas crecen suavemente y vuelven a su tamaño | Melodía de tres notas |
| Abrir la boca | Las hojas se balancean y vuelven a su posición | Efecto de burbuja |

Mantener el mismo gesto no repite el audio continuamente. Vuelve a una expresión
neutra y realiza de nuevo el gesto. La casilla Sonidos activos permite silenciarlo.

## Cómo demostrarlo

1. Inicia y permite la cámara.
2. Mueve suavemente la cabeza: las gafas deben acompañarte.
3. Sonríe durante un instante sin abrir mucho la boca: se activa la melodía.
4. Vuelve a una expresión neutra.
5. Abre claramente la boca: se activa la burbuja.
6. Mantén el gesto: no debe reproducirse en bucle.

## Cómo explicarlo

“Este ejercicio usa Three.js para mostrar unas gafas frutales en 3D y MediaPipe
para seguir mi rostro. MediaPipe devuelve valores de sonrisa y apertura de boca.
En gestures.js, cada gesto tiene un umbral de activación, otro de salida y un tiempo
mínimo para evitar disparos por ruido. main.js relaciona cada evento con una
animación y un archivo de sonido diferente. Un gesto sostenido se activa una sola vez.”

## Dónde está cada parte

- js/gestures.js: detección estable y pausa entre repeticiones.
- js/main.js → updateGestures: relación entre gestos, animación y sonido.
- js/main.js → updateGlasses: posición y orientación sobre la cabeza.
- assets/audio/sonrisa.wav: melodía original sintetizada.
- assets/audio/burbuja.wav: efecto original sintetizado.
- app.json: escena de gafas creada para este ejercicio; se puede importar en el editor.

Para ajustar sensibilidad, cambia los umbrales de new GestureGate en main.js.
La sonrisa usa .52/.28 y la boca .42/.18 (entrada/salida); ambos valores van de 0 a 1.

## Subir a GitHub y Vercel

1. Descomprime este ZIP.
2. Crea un repositorio NUEVO en GitHub para este ejercicio.
3. En Add file → Upload files, arrastra el CONTENIDO de la carpeta: index.html,
   app.json, js, css, assets, vercel.json y los demás archivos. El index.html debe
   quedar visible en la raíz del repositorio, sin una carpeta adicional encima.
4. Pulsa Commit changes.
5. En Vercel, crea un proyecto nuevo e importa ese repositorio.
6. Framework Preset: Other. Root Directory: raíz del repositorio.
   No escribas un Build Command ni un Install Command personalizado.
   vercel.json ya indica que la salida es la carpeta actual (.).
7. Pulsa Deploy. Abre el enlace HTTPS en el navegador del celular y permite la cámara.
8. Prueba el ejercicio y entrega ese enlace en su actividad correspondiente.

Hazlo por separado para cada ejercicio. No reemplaces el repositorio de KUBI final.
Si subes una carpeta exterior por accidente, selecciona esa carpeta como Root Directory.
Para futuras correcciones en el mismo repositorio, carga los archivos modificados y
confirma el commit; el proyecto de Vercel conectado podrá volver a desplegarse.

## Uso y requisitos del equipo

- Abrir desde HTTPS en un navegador con cámara y WebGL habilitado.
- No abrir index.html con doble clic: usa Vercel o un servidor local.
- Pulsar Iniciar cámara antes de probar el filtro.
- Tener buena luz de frente y un solo rostro visible.
- La cámara se procesa en el navegador; el código no envía ni guarda fotos.
- Las bibliotecas, el modelo y los recursos del ejercicio están incluidos.
- No necesita claves, cuentas de servicios de IA ni una tarjeta de activación.
- Detener libera la cámara. Puedes volver a iniciar.

## Archivos principales

- index.html: estructura de la página y controles.
- css/app.css: diseño adaptable a celular y computador.
- js/main.js: cámara, MediaPipe, encuadre y renderizado Three.js.
- js/config.js: identifica el ejercicio que se carga.
- app.json: escena propia en el formato de proyecto del editor Three.js.
- js/vendor: bibliotecas locales; conservar esta carpeta completa, incluido wasm.
- assets/mediapipe/face_landmarker.task: modelo de detección facial.
- vercel.json: configuración de despliegue estático.

## Procedencia de la base

Se tomó como referencia técnica el ZIP Filtro-main.zip compartido por el estudiante.
No se ha confirmado qué partes de esa base proceden del docente y cuáles de terceros.
Se conserva el modelo facial y, en maquillaje, el motor TextureStudio y sus utilidades.
La escena, la interfaz de estos ejercicios, el maquillaje KUBI, la lógica de gestos y
los dos sonidos se prepararon para esta adaptación. No se reutilizan las gafas,
la nariz, la flecha, los audios ni las URLs de la escena del archivo de referencia.

Three.js se distribuye bajo MIT. MediaPipe y su modelo facial canónico proceden
de Google y se distribuyen bajo sus licencias correspondientes (Apache 2.0).
Las licencias incluidas se encuentran en js/vendor.

## Verificación antes de entregar

Se comprobaron la sintaxis, los archivos e importaciones locales, la geometría,
la textura y la lógica de eventos. Las páginas y el Studio se revisaron en navegador.
El navegador de prueba no dispone de WebGL operativo, por lo que no fue posible
validar aquí el filtro completo, el detector ni la cámara en vivo.
La comprobación final debe hacerse con tu celular en el enlace HTTPS desplegado.
