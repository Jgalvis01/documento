# Entrega de la estructura de tesis

La estructura está lista en [main.tex](./main.tex), con **nueve capítulos**, **14 cuadros**, **13 marcadores de figuras**, una ecuación numerada y **132 marcadores pendientes en las fuentes**. Se generó [main.pdf](./main.pdf), de 35 páginas, mediante `latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex`, con salida satisfactoria.

No se redactaron párrafos de contenido: se conservaron los textos institucionales de las cartas y se incorporaron títulos, tablas, palabras clave, comentarios de guía y marcadores rojos. [thesis.cls](./thesis.cls) y [format.tex](./format.tex) conservan exactamente sus hashes originales; no se cambiaron clase, márgenes, fuente ni formato de portada/cartas.

## Árbol de archivos

```text
tesis_documento/
├── .vscode/
│   └── tasks.json
├── abstract.tex
├── anexo_ia.tex
├── anteproyecto.pdf
├── capitulos/
│   ├── cap1_introduccion.tex
│   ├── cap2_descripcion_problema.tex
│   ├── cap3_componente_teorico.tex
│   ├── cap4_datos_preprocesamiento.tex
│   ├── cap5_modelos_entrenamiento.tex
│   ├── cap6_construccion_aplicacion.tex
│   ├── cap7_resultados_validacion.tex
│   ├── cap8_conclusiones.tex
│   └── cap9_trabajo_futuro.tex
├── ENTREGA.md
├── format.tex
├── img/
│   └── pujlogo.png
├── main.aux
├── main.bbl
├── main.blg
├── main.fdb_latexmk
├── main.fls
├── main.idx
├── main.ilg
├── main.ind
├── main.lof
├── main.log
├── main.lot
├── main.maf
├── main.mtc
├── main.mtc0
├── main.out
├── main.pdf
├── main.tex
├── main.toc
├── referencias.bib
├── resumen.tex
├── slashbox.sty
└── thesis.cls
```

Los archivos auxiliares `main.*` distintos de [main.tex](./main.tex) y [main.pdf](./main.pdf) se generan al compilar. [main.log](./main.log) contiene el registro LaTeX y [main.blg](./main.blg), el de BibTeX.

## Compilación

En una instalación de TeX Live o MiKTeX con `latexmk` disponible:

```powershell
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
```

También se configuró la tarea **Compilar tesis (latexmk -pdf)** en [.vscode/tasks.json](./.vscode/tasks.json). En esta sesión utiliza TinyTeX instalado en un directorio temporal fuera del proyecto. Si se borra ese directorio, usa una instalación local y retira de la tarea el prefijo temporal del PATH. No se modificó el PATH global del equipo.

## Advertencias que permanecen

La compilación final no presenta errores, desbordamientos `Overfull`, referencias indefinidas ni destinos PDF duplicados. BibTeX no reporta advertencias. Permanecen:

- La clase solicitada es `thesis`, pero la plantilla declara internamente `ThesisStyle`. Se conserva la clase original.
- Dos avisos de `fancyhdr`: se configuran encabezados pares (`E`) con la opción `oneside`.
- Un aviso de `fancyhdr`: altura de encabezado de 13.6 pt frente a 14.33044 pt recomendados. Se mantienen las dimensiones de la plantilla.
- La forma tipográfica `OT1/cmr/bx/sc` no existe: LaTeX sustituye la forma y español simula las versalitas. Incluye cuatro avisos de `spanish` y el resumen de sustituciones de fuentes. Se conserva la fuente original.
- `minitoc(hints) W0024`: remite a observaciones de compatibilidad con `tocbibind` y `float`; no impide generar los índices solicitados.
- Dos avisos `Underfull \hbox`: uno en la alineación del cuadro de resultados por modelo y otro en la referencia de la OMS. No hay contenido desbordado; se revisó visualmente la tabla.

Registro exacto de avisos de la última compilación:

- [main.log:13](./main.log:13):

  ```text
  LaTeX Warning: You have requested document class `thesis',
                 but the document class provides `ThesisStyle'.
  ```

- [main.log:736](./main.log:736):

  ```text
  Package fancyhdr Warning: \fancyhead's `E' option without twoside option is useless.
  (fancyhdr)                Please consider using the `twoside' option on input line 88.
  ```

- [main.log:740](./main.log:740):

  ```text
  Package fancyhdr Warning: \fancyhead's `E' option without twoside option is useless.
  (fancyhdr)                Please consider using the `twoside' option on input line 90.
  ```

- [main.log:891](./main.log:891):

  ```text
  LaTeX Font Warning: Font shape `OT1/cmr/bx/sc' undefined
  (Font)              using `OT1/cmr/bx/n' instead on input line 49.
  ```

- [main.log:895](./main.log:895):

  ```text
  Package spanish Warning: Replacing `OT1/cmr/bx/sc' by 
  (spanish)                faked small caps on input line 49.
  ```

- [main.log:903](./main.log:903):

  ```text
  Package spanish Warning: Replacing `OT1/cmr/bx/sc' by 
  (spanish)                faked small caps on input line 52.
  ```

- [main.log:913](./main.log:913):

  ```text
  Package spanish Warning: Replacing `OT1/cmr/bx/sc' by 
  (spanish)                faked small caps on input line 2.
  ```

- [main.log:935](./main.log:935):

  ```text
  Package spanish Warning: Replacing `OT1/cmr/bx/sc' by 
  (spanish)                faked small caps on input line 53.
  ```

- [main.log:939](./main.log:939):

  ```text
  Package fancyhdr Warning: \headheight is too small (13.6pt): 
  (fancyhdr)                Make it at least 14.33044pt, for example:
  ```

- [main.log:1018](./main.log:1018):

  ```text
  Underfull \hbox (badness 10000) in alignment at lines 29--29
  ```

- [main.log:1055](./main.log:1055):

  ```text
  Underfull \hbox (badness 10000) in paragraph at lines 4--6
  ```

- [main.log:1074](./main.log:1074):

  ```text
  Package minitoc(hints) Warning: W0024
  (minitoc(hints))                Some hints have been written 
  ```

- [main.log:1090](./main.log:1090):

  ```text
  LaTeX Font Warning: Some font shapes were not available, defaults substituted.
  ```

## Observaciones de fuentes y datos

- El adjunto auxiliar recibido tiene cero bytes. [anteproyecto.pdf](./anteproyecto.pdf) es una plantilla de ejemplo sin el texto ni la bibliografía del anteproyecto real. Los objetivos se dejaron pendientes de copiar textualmente, tal como se solicitó.
- [referencias.bib](./referencias.bib) se reconstruyó desde la bibliografía previa del proyecto. Las entradas no corregidas se conservaron como material del autor; su autenticidad no se da por verificada. La numeración antigua del encargo se documentó en comentarios; BibTeX renumera al compilar.
- Se eliminó la entrada duplicada de EnsembleSkinNet y se corrigió la conservada con [Cherukuri y Vara Prasad, Frontiers in Oncology](https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2025.1699960/full).
- Se corrigió la antigua referencia [7] con [Bello, Ng y Leung, Applied Sciences](https://www.mdpi.com/2076-3417/14/17/7707), y [10] con [Al Mamun et al., preprint de arXiv](https://arxiv.org/abs/2505.21597).
- Se incorporaron los identificadores y datos de [Tschandl et al., HAM10000](https://arxiv.org/abs/1803.10417) y [Codella et al., ISIC 2018](https://arxiv.org/abs/1902.03368).
- Silva et al. conserva el comentario literal `% VERIFICAR o retirar` y un marcador rojo en la bibliografía. No se presenta como referencia verificada.
- ConvNeXt-Tiny se incluyó con siete celdas pendientes porque no se suministraron resolución ni métricas. Las prioridades y verificaciones de requisitos tampoco se inventaron.
- Los requisitos no funcionales se presentan como metas suministradas, pendientes de evidencia; no como pruebas superadas.
- Las guías piden comprobar la selección del modelo con resultados de validación, los conteos con los manifiestos de partición y la ausencia de lesiones compartidas en ISIC 2018. Esos registros no están disponibles en el proyecto.
- La clase akiec se describe como premaligna / maligna in situ, porque agrupa queratosis actínicas y carcinoma intraepitelial; bkl contiene las tres categorías indicadas en el encargo.
- El comando `\nocite{*}` permite revisar toda la bibliografía mientras no hay párrafos redactados. Al completar el texto, usar citas en sus lugares correspondientes.

## Comprobaciones realizadas

- 56 capítulos/secciones/subsecciones con guía y marcador.
- 14 cuadros y 13 figuras con caption, label y referencia previa en el comentario de guía.
- Totales por clase, por partición, por lesiones y por fotos/lesión consistentes con las cifras suministradas.
- 19 claves bibliográficas únicas; duplicado eliminado y entradas solicitadas corregidas.
- No quedan contenidos ni nombres de capítulos del tema anterior en las fuentes finales.
- Revisión visual de portada, ambas cartas, clases y distribución HAM10000, requisitos, resultados por modelo, modos de decisión y validación ISIC.

## Lista completa de pendientes por capítulo

Cada casilla corresponde a una aparición de `\pendiente{...}` en las fuentes. El código del estudiante se define una vez y aparece en ambas cartas. Las celdas repetidas se enumeran individualmente. Las cifras que aparecen en esta lista cuentan tareas, no resultados experimentales.

### Preliminares: código de estudiante (1)

Archivo: [main.tex](./main.tex).

- [ ] código — Código del estudiante en ambas cartas. [Línea 24](./main.tex:24).

### Abstract (1)

Archivo: [abstract.tex](./abstract.tex).

- [ ] redactar el abstract en inglés — Abstract. [Línea 2](./abstract.tex:2).

### Resumen (1)

Archivo: [resumen.tex](./resumen.tex).

- [ ] redactar el resumen en español — Resumen. [Línea 2](./resumen.tex:2).

### Capítulo 1. Introducción (2)

Archivo: [capitulos/cap1_introduccion.tex](./capitulos/cap1_introduccion.tex).

- [ ] redactar la introducción — Introducción. [Línea 3](./capitulos/cap1_introduccion.tex:3).
- [ ] URL — Introducción. [Línea 6](./capitulos/cap1_introduccion.tex:6).

### Capítulo 2. Descripción del problema (14)

Archivo: [capitulos/cap2_descripcion_problema.tex](./capitulos/cap2_descripcion_problema.tex).

- [ ] redactar la presentación del problema — Descripción del problema. [Línea 3](./capitulos/cap2_descripcion_problema.tex:3).
- [ ] escribir la pregunta de investigación — Formulación. [Línea 7](./capitulos/cap2_descripcion_problema.tex:7).
- [ ] redactar las cuatro subpreguntas — Sistematización. [Línea 11](./capitulos/cap2_descripcion_problema.tex:11).
- [ ] subpregunta del objetivo específico 1 — Sistematización. [Línea 14](./capitulos/cap2_descripcion_problema.tex:14).
- [ ] subpregunta del objetivo específico 2 — Sistematización. [Línea 15](./capitulos/cap2_descripcion_problema.tex:15).
- [ ] subpregunta del objetivo específico 3 — Sistematización. [Línea 16](./capitulos/cap2_descripcion_problema.tex:16).
- [ ] subpregunta del objetivo específico 4 — Sistematización. [Línea 17](./capitulos/cap2_descripcion_problema.tex:17).
- [ ] presentar los objetivos — Objetivos. [Línea 22](./capitulos/cap2_descripcion_problema.tex:22).
- [ ] copiar el objetivo general del anteproyecto — Objetivo general. [Línea 26](./capitulos/cap2_descripcion_problema.tex:26).
- [ ] copiar textual del anteproyecto — Objetivos específicos. [Línea 31](./capitulos/cap2_descripcion_problema.tex:31).
- [ ] copiar textual del anteproyecto — Objetivos específicos. [Línea 32](./capitulos/cap2_descripcion_problema.tex:32).
- [ ] copiar textual del anteproyecto — Objetivos específicos. [Línea 33](./capitulos/cap2_descripcion_problema.tex:33).
- [ ] copiar textual del anteproyecto — Objetivos específicos. [Línea 34](./capitulos/cap2_descripcion_problema.tex:34).
- [ ] redactar la justificación y su relación con el ODS 3 — Justificación. [Línea 39](./capitulos/cap2_descripcion_problema.tex:39).

### Capítulo 3. Componente teórico (27)

Archivo: [capitulos/cap3_componente_teorico.tex](./capitulos/cap3_componente_teorico.tex).

- [ ] presentar el componente teórico — Componente teórico. [Línea 3](./capitulos/cap3_componente_teorico.tex:3).
- [ ] introducir el marco teórico — Marco teórico. [Línea 7](./capitulos/cap3_componente_teorico.tex:7).
- [ ] describir las lesiones y las siete clases — Lesiones cutáneas y melanoma. [Línea 11](./capitulos/cap3_componente_teorico.tex:11).
- [ ] explicar la dermatoscopia — Dermatoscopia. [Línea 15](./capitulos/cap3_componente_teorico.tex:15).
- [ ] explicar los fundamentos de las CNN — Redes neuronales convolucionales. [Línea 19](./capitulos/cap3_componente_teorico.tex:19).
- [ ] explicar la transferencia y el ajuste fino — Aprendizaje por transferencia y ajuste fino. [Línea 23](./capitulos/cap3_componente_teorico.tex:23).
- [ ] explicar el desbalance de clases — Desbalance de clases. [Línea 27](./capitulos/cap3_componente_teorico.tex:27).
- [ ] definir las métricas y su interpretación — Métricas de evaluación. [Línea 31](./capitulos/cap3_componente_teorico.tex:31).
- [ ] redactar el estado del arte y contrastar sus protocolos — Trabajos relacionados. [Línea 35](./capitulos/cap3_componente_teorico.tex:35).
- [ ] trabajo 1 — Comparación del estado del arte.; \pendiente{trabajo 1}; columna 1. [Línea 46](./capitulos/cap3_componente_teorico.tex:46).
- [ ] arquitectura — Comparación del estado del arte.; \pendiente{trabajo 1}; columna 2. [Línea 46](./capitulos/cap3_componente_teorico.tex:46).
- [ ] conjunto — Comparación del estado del arte.; \pendiente{trabajo 1}; columna 3. [Línea 46](./capitulos/cap3_componente_teorico.tex:46).
- [ ] partición — Comparación del estado del arte.; \pendiente{trabajo 1}; columna 4. [Línea 46](./capitulos/cap3_componente_teorico.tex:46).
- [ ] dato — Comparación del estado del arte.; \pendiente{trabajo 1}; columna 5. [Línea 46](./capitulos/cap3_componente_teorico.tex:46).
- [ ] métrica — Comparación del estado del arte.; \pendiente{trabajo 1}; columna 6. [Línea 46](./capitulos/cap3_componente_teorico.tex:46).
- [ ] trabajo 2 — Comparación del estado del arte.; \pendiente{trabajo 2}; columna 1. [Línea 47](./capitulos/cap3_componente_teorico.tex:47).
- [ ] arquitectura — Comparación del estado del arte.; \pendiente{trabajo 2}; columna 2. [Línea 47](./capitulos/cap3_componente_teorico.tex:47).
- [ ] conjunto — Comparación del estado del arte.; \pendiente{trabajo 2}; columna 3. [Línea 47](./capitulos/cap3_componente_teorico.tex:47).
- [ ] partición — Comparación del estado del arte.; \pendiente{trabajo 2}; columna 4. [Línea 47](./capitulos/cap3_componente_teorico.tex:47).
- [ ] dato — Comparación del estado del arte.; \pendiente{trabajo 2}; columna 5. [Línea 47](./capitulos/cap3_componente_teorico.tex:47).
- [ ] métrica — Comparación del estado del arte.; \pendiente{trabajo 2}; columna 6. [Línea 47](./capitulos/cap3_componente_teorico.tex:47).
- [ ] trabajo 3 — Comparación del estado del arte.; \pendiente{trabajo 3}; columna 1. [Línea 48](./capitulos/cap3_componente_teorico.tex:48).
- [ ] arquitectura — Comparación del estado del arte.; \pendiente{trabajo 3}; columna 2. [Línea 48](./capitulos/cap3_componente_teorico.tex:48).
- [ ] conjunto — Comparación del estado del arte.; \pendiente{trabajo 3}; columna 3. [Línea 48](./capitulos/cap3_componente_teorico.tex:48).
- [ ] partición — Comparación del estado del arte.; \pendiente{trabajo 3}; columna 4. [Línea 48](./capitulos/cap3_componente_teorico.tex:48).
- [ ] dato — Comparación del estado del arte.; \pendiente{trabajo 3}; columna 5. [Línea 48](./capitulos/cap3_componente_teorico.tex:48).
- [ ] métrica — Comparación del estado del arte.; \pendiente{trabajo 3}; columna 6. [Línea 48](./capitulos/cap3_componente_teorico.tex:48).

### Capítulo 4. Datos y preprocesamiento (9)

Archivo: [capitulos/cap4_datos_preprocesamiento.tex](./capitulos/cap4_datos_preprocesamiento.tex).

- [ ] presentar los datos y el preprocesamiento — Datos y preprocesamiento. [Línea 3](./capitulos/cap4_datos_preprocesamiento.tex:3).
- [ ] describir HAM10000 y sus clases — Conjunto de datos HAM10000. [Línea 7](./capitulos/cap4_datos_preprocesamiento.tex:7).
- [ ] imagen de ejemplo por clase — Conjunto de datos HAM10000. [Línea 53](./capitulos/cap4_datos_preprocesamiento.tex:53).
- [ ] explicar las imágenes repetidas por lesión — Imágenes por lesión. [Línea 60](./capitulos/cap4_datos_preprocesamiento.tex:60).
- [ ] documentar la partición agrupada y su verificación — Partición de los datos. [Línea 84](./capitulos/cap4_datos_preprocesamiento.tex:84).
- [ ] describir las etapas del preprocesamiento — Preprocesamiento. [Línea 110](./capitulos/cap4_datos_preprocesamiento.tex:110).
- [ ] antes y después de cada etapa — Preprocesamiento. [Línea 115](./capitulos/cap4_datos_preprocesamiento.tex:115).
- [ ] documentar el aumento en línea — Aumento de datos. [Línea 122](./capitulos/cap4_datos_preprocesamiento.tex:122).
- [ ] explicar los pesos de clase — Tratamiento del desbalance. [Línea 126](./capitulos/cap4_datos_preprocesamiento.tex:126).

### Capítulo 5. Modelos y entrenamiento (10)

Archivo: [capitulos/cap5_modelos_entrenamiento.tex](./capitulos/cap5_modelos_entrenamiento.tex).

- [ ] presentar el diseño experimental — Modelos y entrenamiento. [Línea 3](./capitulos/cap5_modelos_entrenamiento.tex:3).
- [ ] describir las arquitecturas y el estado de ConvNeXt-Tiny — Arquitecturas evaluadas. [Línea 7](./capitulos/cap5_modelos_entrenamiento.tex:7).
- [ ] diagrama de la arquitectura seleccionada — Arquitecturas evaluadas. [Línea 12](./capitulos/cap5_modelos_entrenamiento.tex:12).
- [ ] documentar las fases y los hiperparámetros — Estrategia de entrenamiento. [Línea 19](./capitulos/cap5_modelos_entrenamiento.tex:19).
- [ ] documentar el diagnóstico y los ajustes — Diagnóstico inicial y ajustes. [Línea 23](./capitulos/cap5_modelos_entrenamiento.tex:23).
- [ ] analizar las configuraciones a 224 px — Comparación a 224 px. [Línea 27](./capitulos/cap5_modelos_entrenamiento.tex:27).
- [ ] comparar los protocolos por imagen y por lesión — Partición por imagen frente a partición por lesión. [Línea 31](./capitulos/cap5_modelos_entrenamiento.tex:31).
- [ ] analizar el efecto de la resolución — Resolución de 384 px. [Línea 52](./capitulos/cap5_modelos_entrenamiento.tex:52).
- [ ] documentar la regla y aportar evidencia de validación — Regla de selección del modelo. [Línea 56](./capitulos/cap5_modelos_entrenamiento.tex:56).
- [ ] explicar la calibración y los modos de decisión — Calibración y umbrales de decisión. [Línea 60](./capitulos/cap5_modelos_entrenamiento.tex:60).

### Capítulo 6. Construcción de la aplicación (41)

Archivo: [capitulos/cap6_construccion_aplicacion.tex](./capitulos/cap6_construccion_aplicacion.tex).

- [ ] presentar la construcción del aplicativo — Construcción de la aplicación. [Línea 3](./capitulos/cap6_construccion_aplicacion.tex:3).
- [ ] presentar la arquitectura del sistema — Arquitectura del sistema. [Línea 7](./capitulos/cap6_construccion_aplicacion.tex:7).
- [ ] describir la visión general — Visión general. [Línea 11](./capitulos/cap6_construccion_aplicacion.tex:11).
- [ ] diagrama de contexto — Visión general. [Línea 16](./capitulos/cap6_construccion_aplicacion.tex:16).
- [ ] C4 de contenedores — Visión general. [Línea 24](./capitulos/cap6_construccion_aplicacion.tex:24).
- [ ] documentar los módulos del cliente — Módulos del cliente. [Línea 31](./capitulos/cap6_construccion_aplicacion.tex:31).
- [ ] documentar la exportación y su validación — Exportación del modelo a ONNX. [Línea 35](./capitulos/cap6_construccion_aplicacion.tex:35).
- [ ] describir el flujo de datos — Flujo de datos. [Línea 39](./capitulos/cap6_construccion_aplicacion.tex:39).
- [ ] casos de uso — Flujo de datos. [Línea 44](./capitulos/cap6_construccion_aplicacion.tex:44).
- [ ] diagrama de secuencia — Flujo de datos. [Línea 52](./capitulos/cap6_construccion_aplicacion.tex:52).
- [ ] documentar el despliegue en Vercel — Despliegue en Vercel. [Línea 59](./capitulos/cap6_construccion_aplicacion.tex:59).
- [ ] completar la especificación y su trazabilidad — Especificación de requisitos. [Línea 63](./capitulos/cap6_construccion_aplicacion.tex:63).
- [ ] prioridad — Requisitos funcionales del aplicativo.; RF-01; columna 3. [Línea 74](./capitulos/cap6_construccion_aplicacion.tex:74).
- [ ] criterio — Requisitos funcionales del aplicativo.; RF-01; columna 4. [Línea 74](./capitulos/cap6_construccion_aplicacion.tex:74).
- [ ] verificación — Requisitos funcionales del aplicativo.; RF-01; columna 5. [Línea 74](./capitulos/cap6_construccion_aplicacion.tex:74).
- [ ] prioridad — Requisitos funcionales del aplicativo.; RF-02; columna 3. [Línea 75](./capitulos/cap6_construccion_aplicacion.tex:75).
- [ ] criterio — Requisitos funcionales del aplicativo.; RF-02; columna 4. [Línea 75](./capitulos/cap6_construccion_aplicacion.tex:75).
- [ ] verificación — Requisitos funcionales del aplicativo.; RF-02; columna 5. [Línea 75](./capitulos/cap6_construccion_aplicacion.tex:75).
- [ ] prioridad — Requisitos funcionales del aplicativo.; RF-03; columna 3. [Línea 76](./capitulos/cap6_construccion_aplicacion.tex:76).
- [ ] criterio — Requisitos funcionales del aplicativo.; RF-03; columna 4. [Línea 76](./capitulos/cap6_construccion_aplicacion.tex:76).
- [ ] verificación — Requisitos funcionales del aplicativo.; RF-03; columna 5. [Línea 76](./capitulos/cap6_construccion_aplicacion.tex:76).
- [ ] prioridad — Requisitos funcionales del aplicativo.; RF-04; columna 3. [Línea 77](./capitulos/cap6_construccion_aplicacion.tex:77).
- [ ] criterio — Requisitos funcionales del aplicativo.; RF-04; columna 4. [Línea 77](./capitulos/cap6_construccion_aplicacion.tex:77).
- [ ] verificación — Requisitos funcionales del aplicativo.; RF-04; columna 5. [Línea 77](./capitulos/cap6_construccion_aplicacion.tex:77).
- [ ] prioridad — Requisitos funcionales del aplicativo.; RF-05; columna 3. [Línea 78](./capitulos/cap6_construccion_aplicacion.tex:78).
- [ ] criterio — Requisitos funcionales del aplicativo.; RF-05; columna 4. [Línea 78](./capitulos/cap6_construccion_aplicacion.tex:78).
- [ ] verificación — Requisitos funcionales del aplicativo.; RF-05; columna 5. [Línea 78](./capitulos/cap6_construccion_aplicacion.tex:78).
- [ ] prioridad — Requisitos funcionales del aplicativo.; RF-06; columna 3. [Línea 79](./capitulos/cap6_construccion_aplicacion.tex:79).
- [ ] criterio — Requisitos funcionales del aplicativo.; RF-06; columna 4. [Línea 79](./capitulos/cap6_construccion_aplicacion.tex:79).
- [ ] verificación — Requisitos funcionales del aplicativo.; RF-06; columna 5. [Línea 79](./capitulos/cap6_construccion_aplicacion.tex:79).
- [ ] evidencia — Requisitos no funcionales y metas de verificación.; RNF-01; columna 4. [Línea 93](./capitulos/cap6_construccion_aplicacion.tex:93).
- [ ] evidencia — Requisitos no funcionales y metas de verificación.; RNF-02; columna 4. [Línea 94](./capitulos/cap6_construccion_aplicacion.tex:94).
- [ ] evidencia — Requisitos no funcionales y metas de verificación.; RNF-03; columna 4. [Línea 95](./capitulos/cap6_construccion_aplicacion.tex:95).
- [ ] evidencia — Requisitos no funcionales y metas de verificación.; RNF-04; columna 4. [Línea 96](./capitulos/cap6_construccion_aplicacion.tex:96).
- [ ] evidencia — Requisitos no funcionales y metas de verificación.; RNF-05; columna 4. [Línea 97](./capitulos/cap6_construccion_aplicacion.tex:97).
- [ ] describir el diseño de la interfaz — Diseño de la interfaz. [Línea 104](./capitulos/cap6_construccion_aplicacion.tex:104).
- [ ] captura de la vista principal — Diseño de la interfaz. [Línea 109](./capitulos/cap6_construccion_aplicacion.tex:109).
- [ ] captura de resultados por lote — Diseño de la interfaz. [Línea 117](./capitulos/cap6_construccion_aplicacion.tex:117).
- [ ] captura del detalle por imagen — Diseño de la interfaz. [Línea 125](./capitulos/cap6_construccion_aplicacion.tex:125).
- [ ] documentar las funcionalidades implementadas — Funcionalidades principales. [Línea 132](./capitulos/cap6_construccion_aplicacion.tex:132).
- [ ] escribir el manual de usuario — Manual de usuario. [Línea 136](./capitulos/cap6_construccion_aplicacion.tex:136).

### Capítulo 7. Resultados y validación (16)

Archivo: [capitulos/cap7_resultados_validacion.tex](./capitulos/cap7_resultados_validacion.tex).

- [ ] introducir los resultados y la validación — Resultados y validación. [Línea 3](./capitulos/cap7_resultados_validacion.tex:3).
- [ ] analizar los resultados por modelo — Resultados de todos los modelos en prueba. [Línea 7](./capitulos/cap7_resultados_validacion.tex:7).
- [ ] dato — Resultados en prueba, media de tres semillas. Porcentajes salvo Macro-F1 y AUC.; ConvNeXt-Tiny; columna 2. [Línea 27](./capitulos/cap7_resultados_validacion.tex:27).
- [ ] dato — Resultados en prueba, media de tres semillas. Porcentajes salvo Macro-F1 y AUC.; ConvNeXt-Tiny; columna 3. [Línea 27](./capitulos/cap7_resultados_validacion.tex:27).
- [ ] dato — Resultados en prueba, media de tres semillas. Porcentajes salvo Macro-F1 y AUC.; ConvNeXt-Tiny; columna 4. [Línea 27](./capitulos/cap7_resultados_validacion.tex:27).
- [ ] dato — Resultados en prueba, media de tres semillas. Porcentajes salvo Macro-F1 y AUC.; ConvNeXt-Tiny; columna 5. [Línea 27](./capitulos/cap7_resultados_validacion.tex:27).
- [ ] dato — Resultados en prueba, media de tres semillas. Porcentajes salvo Macro-F1 y AUC.; ConvNeXt-Tiny; columna 6. [Línea 27](./capitulos/cap7_resultados_validacion.tex:27).
- [ ] dato — Resultados en prueba, media de tres semillas. Porcentajes salvo Macro-F1 y AUC.; ConvNeXt-Tiny; columna 7. [Línea 27](./capitulos/cap7_resultados_validacion.tex:27).
- [ ] dato — Resultados en prueba, media de tres semillas. Porcentajes salvo Macro-F1 y AUC.; ConvNeXt-Tiny; columna 8. [Línea 27](./capitulos/cap7_resultados_validacion.tex:27).
- [ ] gráfico de Macro-F1 por modelo — Resultados de todos los modelos en prueba. [Línea 36](./capitulos/cap7_resultados_validacion.tex:36).
- [ ] presentar el modelo seleccionado y sus resultados — Modelo seleccionado. [Línea 43](./capitulos/cap7_resultados_validacion.tex:43).
- [ ] matriz de confusión — Modelo seleccionado. [Línea 98](./capitulos/cap7_resultados_validacion.tex:98).
- [ ] curva ROC de melanoma — Modelo seleccionado. [Línea 106](./capitulos/cap7_resultados_validacion.tex:106).
- [ ] documentar la validación en ISIC 2018 — Validación en ISIC 2018. [Línea 113](./capitulos/cap7_resultados_validacion.tex:113).
- [ ] redactar la discusión de los resultados — Discusión. [Línea 136](./capitulos/cap7_resultados_validacion.tex:136).
- [ ] documentar las limitaciones — Limitaciones. [Línea 140](./capitulos/cap7_resultados_validacion.tex:140).

### Capítulo 8. Conclusiones (4)

Archivo: [capitulos/cap8_conclusiones.tex](./capitulos/cap8_conclusiones.tex).

- [ ] conclusión del objetivo específico 1 y cifra principal — Conclusiones. [Línea 4](./capitulos/cap8_conclusiones.tex:4).
- [ ] conclusión del objetivo específico 2 y cifra principal — Conclusiones. [Línea 5](./capitulos/cap8_conclusiones.tex:5).
- [ ] conclusión del objetivo específico 3 y cifra principal — Conclusiones. [Línea 6](./capitulos/cap8_conclusiones.tex:6).
- [ ] conclusión del objetivo específico 4 y cifra principal — Conclusiones. [Línea 7](./capitulos/cap8_conclusiones.tex:7).

### Capítulo 9. Trabajo futuro (1)

Archivo: [capitulos/cap9_trabajo_futuro.tex](./capitulos/cap9_trabajo_futuro.tex).

- [ ] redactar las líneas de trabajo futuro — Trabajo futuro. [Línea 3](./capitulos/cap9_trabajo_futuro.tex:3).

### Anexo de inteligencia artificial (4)

Archivo: [anexo_ia.tex](./anexo_ia.tex).

- [ ] herramientas usadas — Herramientas usadas. [Línea 4](./anexo_ia.tex:4).
- [ ] tareas en que se usaron — Tareas en que se usaron. [Línea 8](./anexo_ia.tex:8).
- [ ] qué hizo y verificó el autor — Qué hizo y verificó el autor. [Línea 12](./anexo_ia.tex:12).
- [ ] nota de autoría — Nota de autoría. [Línea 16](./anexo_ia.tex:16).

### Bibliografía (1)

Archivo: [referencias.bib](./referencias.bib).

- [ ] verificar o retirar la referencia de Silva et al. — Referencia Silva et al.. [Línea 87](./referencias.bib:87).

## Revisiones adicionales indicadas en comentarios

- [ ] Verificar el nombre vigente del director de carrera en [main.tex](./main.tex).
- [ ] Cotejar las referencias heredadas con el anteproyecto real.
- [ ] Incorporar las citas y las referencias visibles a cuadros y figuras al escribir los párrafos, siguiendo los comentarios GUÍA.
