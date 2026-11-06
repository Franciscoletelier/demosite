# Respaldo de prompts — Proyecto web de historia económica de China

Este documento conserva los dos prompts operativos de la última iteración: primero la auditoría documental y luego la implementación web basada en esa auditoría. La secuencia es deliberada: el Prompt 2 debe utilizar el inventario validado por el Prompt 1 como contrato de datos.

---

# PROMPT 1 — Auditoría documental y validación de datos
## Proyecto: Historia económica de China — Brandt, Ma y Rawski (2014)

### Rol
Actúa como un equipo interdisciplinario integrado por:
- Historiador económico especializado en China.
- Economista del desarrollo y de las instituciones.
- Investigador con experiencia en revisión documental y trazabilidad de datos.
- Especialista en metodología de investigación y visualización de evidencia histórica.

Trabaja con rigor académico. La fidelidad al documento fuente tiene prioridad sobre la espectacularidad narrativa o visual.

### Objetivo
Preparar una auditoría documental del artículo:

Brandt, Loren, Debin Ma y Thomas G. Rawski (2014), “From Divergence to Convergence: Reevaluating the History Behind China's Economic Boom”, *Journal of Economic Literature*, 52(1), 45–123. DOI: 10.1257/jel.52.1.45.

Utiliza el paper original como fuente primaria de verificación. Usa el documento de análisis previo —“Análisis Cronológico de la Economía China: De la Divergencia a la Convergencia”— como apoyo para identificar temas, estructura y afirmaciones que deben cotejarse. No asumas que la síntesis previa es correcta.

### Fase 1. Inventario de evidencia
Identifica y revisa, como mínimo:
1. Tabla 1: perspectiva histórica comparada de población, PIB, PIB per cápita y participaciones relativas.
2. Tabla 2: ingresos fiscales en China entre 1085 y 1776.
3. Tabla 3: comparación internacional de ingresos fiscales Qing.
4. Figura 1: gasto fiscal de la dinastía Qing.
5. Mapa 1: comparación territorial Ming y Qing.
6. Cualquier otra cifra o afirmación cuantitativa que se proponga utilizar en la presentación.

Para cada dato u observación registra:
- Valor exacto tal como aparece en el paper.
- Año o período.
- Unidad de medida.
- Indicador y definición.
- País, región, población o universo al que corresponde.
- Número de tabla, figura, sección y página impresa.
- Fuente estadística original citada por los autores.
- Notas, limitaciones o advertencias metodológicas.
- Estado de verificación.

### Fase 2. Clasificación de evidencia
Clasifica cada afirmación en una de estas categorías:
- Dato tabulado directamente.
- Estimación citada por los autores.
- Afirmación narrativa del texto.
- Cálculo derivado a partir de datos publicados.
- Interpretación de los autores.
- Síntesis o interpretación propia.
- No verificado / fuente insuficiente.

No presentes una afirmación narrativa como observación tabulada. No conviertas un cálculo derivado en un dato original del paper. Identifica claramente las interpretaciones propias.

### Fase 3. Auditoría de discrepancias
Coteja expresamente, sin corregir silenciosamente:
- La ausencia de una observación para el año 1300 en la Tabla 1, aunque el texto discuta la evolución del PIB per cápita hasta ese período.
- La consistencia interna de los valores de población, PIB total y PIB per cápita de la Tabla 1, especialmente el dato de 1820.
- Las estimaciones demográficas de China en torno a 1850 y antes de la Rebelión Taiping.
- Las estimaciones de mortalidad asociadas a la Rebelión Taiping.
- Las diferencias entre la cronología general Song (960–1279) y cualquier referencia interna a Southern Song con fechas distintas.
- La fecha del Tratado de Shimonoseki tal como aparece en el paper y cualquier discrepancia histórica relevante.
- Las unidades, períodos y definiciones de los tres paneles de la Tabla 3.
- Las limitaciones para recuperar valores numéricos exactos de la Figura 1.
- La procedencia de toda cifra de industrialización republicana, período maoísta y reformas posteriores a 1978 que aparezca en la síntesis previa.

Para cada discrepancia informa: formulación del paper, formulación de la síntesis, naturaleza del problema, evidencia disponible y tratamiento recomendado.

### Fase 4. Geografía histórica
Revisa el Mapa 1 y las referencias geográficas del artículo.
- Distingue límites históricos, territorios controlados, regiones económicas, puertos y ciudades.
- No inventes fronteras, rutas, áreas de influencia ni coordenadas.
- Si se usan ubicaciones modernas para contextualizar procesos históricos, etiquétalas como referencias aproximadas.
- Explica qué información geográfica puede y no puede representarse responsablemente en un mapa web.

### Fase 5. Entregable de auditoría
Presenta los resultados en este orden:
1. Resumen ejecutivo de la auditoría.
2. Inventario de tablas, figuras y mapa.
3. Registro de datos validados, con valores, unidades, períodos y referencias.
4. Discrepancias y errores potenciales.
5. Cifras excluidas por falta de trazabilidad.
6. Limitaciones documentales y geográficas.
7. Recomendaciones para visualizaciones y narrativa web.
8. Bibliografía y fuentes secundarias citadas por el artículo.

### Reglas obligatorias
- No inventes datos, referencias, páginas ni citas.
- No interpolar años que no estén observados.
- No tratar datos ausentes como cero.
- No mezclar unidades, períodos ni universos estadísticos.
- Mantener rangos como rangos.
- Si una figura no permite recuperar valores exactos, no digitalices ni estimes puntos visuales sin indicarlo y justificar el método.
- No corregir discrepancias en silencio: registra el valor publicado y explica el problema.
- Prioriza la fuente original sobre la síntesis previa.
- Si no puedes verificar una afirmación, indícalo expresamente.
- Distingue siempre evidencia del paper, interpretación de los autores e interpretación propia.

El resultado de esta fase será el contrato documental y de datos para la fase de desarrollo. No escribas todavía el HTML.


---

# PROMPT 2 — Desarrollo de la web interactiva de historia económica de China
## Proyecto: De la divergencia a la convergencia

### Rol
Actúa como un equipo interdisciplinario compuesto por:
- Frontend developer senior especializado en HTML, CSS y JavaScript.
- Diseñador UX/UI con experiencia en storytelling editorial y dashboards.
- Especialista en visualización de datos históricos y económicos.
- Especialista GIS y cartografía web.
- Historiador económico y economista institucional encargado de preservar la exactitud del contenido.

### Objetivo
Construir una web de una sola página que explique la transformación de la economía china desde la era Song hasta las reformas contemporáneas, utilizando como fuente principal:

Brandt, Loren, Debin Ma y Thomas G. Rawski (2014), “From Divergence to Convergence: Reevaluating the History Behind China's Economic Boom”, *Journal of Economic Literature*, 52(1), 45–123. DOI: 10.1257/jel.52.1.45.

La web debe basarse en:
1. El paper original.
2. El inventario y la auditoría documental validados en la Fase 1.
3. El documento de análisis previo, utilizado solo como apoyo narrativo.

La auditoría validada es el contrato de datos: no agregues cifras que no estén en ella sin verificarlas primero.

### Resultado requerido
Entrega un único archivo `index.html`, completo y listo para publicarse en GitHub Pages. No entregues una aplicación que requiera backend, base de datos, instalación local, compilación ni claves privadas.

### Dirección visual y experiencia
Estilo **hybrid**:
- Editorial académico: tipografía serif para títulos, jerarquía clara, ritmo de lectura y espacio en blanco.
- Dashboard analítico: indicadores, gráficos, comparaciones y visualización de evidencia.
- Storytelling histórico: narrativa cronológica y contextualización territorial.

La experiencia debe incluir:
- Diseño responsive para escritorio, tablet y móvil.
- Scroll suave.
- Estados hover discretos.
- Navegación por secciones.
- Transiciones moderadas y accesibles.
- Contraste, legibilidad y jerarquía visual.
- Lenguaje visual sobrio, académico y contemporáneo.

### Estructura de contenido
Organiza la página en estas secciones:

1. **Hero / Introducción**
   - Título: “De la divergencia a la convergencia”.
   - Pregunta histórica central.
   - Marco temporal y referencia bibliográfica.
   - Una síntesis breve del argumento del artículo.

2. **Tesis central**
   - Explica la relación entre crecimiento, instituciones, capacidad fiscal, mercados y cambio estructural.
   - Distingue crecimiento extensivo de crecimiento intensivo.
   - No reduzcas el argumento a una explicación monocausal.

3. **Cronología histórica y mapa interactivo**
   Organiza la narrativa en seis bloques editoriales:
   - Song (960–1279).
   - Ming–Qing (1368–1850).
   - Qing tardío (1800–1911).
   - República (1912–1949).
   - Maoísmo (1949–1976).
   - Reformas (1978–2010s).

   Para cada período incluye:
   - Contexto histórico.
   - Estructura económica.
   - Instituciones y actores.
   - Restricciones y mecanismos económicos.
   - Cambios y resultados.
   - Legado para el período siguiente.

   La división en seis períodos es una decisión editorial de la web; no la atribuyas como clasificación formal de los autores si el artículo no lo hace.

4. **Evidencia cuantitativa**
   - Tabla 1: perspectiva global de largo plazo.
   - Tabla 2: ingresos fiscales Song, Ming y Qing.
   - Tabla 3: comparación fiscal internacional Qing, manteniendo separados sus tres paneles.
   - Figura 1: gasto fiscal Qing.
   - Otras cifras solo si están validadas en la auditoría.

   Requisitos:
   - Preservar años, unidades, definiciones, rangos y notas originales.
   - No interpolar años.
   - No convertir datos faltantes en cero.
   - No mezclar unidades o paneles.
   - Para gráficos con años discretos, representar únicamente las observaciones disponibles.
   - Para la Figura 1, si no existen valores numéricos recuperables, utilizar la figura original o una explicación cualitativa; no reconstruir puntos estimados.

5. **Economía política e instituciones**
   Explica, cuando corresponda según el paper:
   - Crecimiento extensivo e intensivo.
   - Crecimiento Smithiano.
   - Capacidad fiscal.
   - Relaciones principal–agente y costos de agencia.
   - Patronazgo y papel de las élites locales / gentry.
   - Derechos de propiedad y contratos.
   - Innovación y cambio tecnológico.
   - Incentivos políticos y económicos.
   - Descentralización y competencia subnacional.
   - Capital humano, comercio y productividad.

   Puedes incluir una matriz comparativa de los seis períodos, pero debe rotularse expresamente como **síntesis analítica propia**, no como tabla original del artículo.

6. **Reformas y convergencia**
   - Explica el proceso gradual de reformas desde 1978.
   - Trata las reformas rurales, empresas rurales, sistema fiscal, empresas estatales e integración internacional según la evidencia verificada.
   - Distingue mecanismos e interpretación de los autores de resultados cuantitativos.

7. **Conclusiones y referencias**
   - Sintetiza los mecanismos de largo plazo.
   - Incluye referencias bibliográficas y notas de procedencia de los datos.
   - Identifica las limitaciones de la evidencia y de la representación geográfica.

### Mapa interactivo
Utiliza Leaflet y OpenStreetMap.
- El mapa debe evolucionar cronológicamente al desplazarse por los períodos (scroll-driven map).
- El mapa debe permanecer sticky en escritorio y adaptarse a móvil.
- Sincroniza los marcadores, foco, zoom, título y nota explicativa con el período activo.
- Los lugares candidatos pueden incluir Jiangnan / Lower Yangzi, delta del Yangzi, Shanghai, Hankou/Wuhan, Guangzhou, Manchuria, Guangdong, Fujian, Anhui y Sichuan, siempre que su uso esté respaldado por el contexto histórico.
- Utiliza ubicaciones aproximadas cuando corresponda y decláralo.
- No inventes coordenadas exactas, fronteras históricas, rutas comerciales ni áreas de influencia.
- No presentes cartografía contemporánea como si representara límites históricos.
- El mapa debe complementar la narrativa, no sugerir una precisión que las fuentes no permiten.

### Gráficos y visualización
Utiliza Chart.js.
- Diseña gráficos limpios, legibles y con unidades visibles.
- Incluye títulos, leyendas, ejes y notas de fuente.
- Mantén separados los paneles de la Tabla 3.
- Conserva rangos y valores faltantes de la auditoría.
- Añade advertencias visibles cuando un dato tenga problemas de consistencia o incertidumbre.
- Evita gráficos decorativos que no comuniquen evidencia.

### Arquitectura y tecnología
- Un único archivo `index.html`.
- HTML5 semántico.
- Tailwind CSS mediante CDN.
- Vanilla JavaScript ES6+.
- Leaflet para cartografía.
- Chart.js para gráficos.
- OpenStreetMap como cartografía base.
- Sin backend, base de datos, build tools ni claves API privadas.
- Mantén los datasets en estructuras JavaScript claramente separadas del código de presentación. Usa, cuando corresponda, estructuras como:
  - `historicalPeriods`
  - `timelineEvents`
  - `geographicLocations`
  - `economicDatasets`
  - `institutionalComparisons`
  - `bibliography`
  - `dataAudit`

Cada observación cuantitativa debe mantener trazabilidad: valor, período, unidad, indicador, fuente, tabla/figura y nota metodológica.

### Control de calidad obligatorio
Antes de entregar:
1. Revisa la sintaxis HTML y JavaScript.
2. Verifica que todas las dependencias externas estén correctamente referenciadas.
3. Comprueba que los gráficos se inicialicen y que los controles funcionen.
4. Comprueba la sincronización del mapa con el scroll.
5. Comprueba la visualización responsive.
6. Verifica accesibilidad básica, contraste y navegación.
7. Revisa que ninguna cifra contradiga el inventario validado.
8. Comprueba que cada gráfico tenga unidades, fuente y notas.
9. Verifica que no se hayan añadido interpolaciones, estimaciones o fronteras ficticias.
10. Distingue expresamente datos originales, estimaciones, afirmaciones narrativas y síntesis propias.

### Entregables
Entrega:
1. El archivo `index.html` completo y descargable.
2. Un resumen breve de la arquitectura.
3. Las instrucciones para publicarlo en GitHub Pages.
4. Una lista de discrepancias, limitaciones o datos excluidos por falta de verificación.
5. Un resumen de las validaciones técnicas realizadas y de las pruebas que aún requieran revisión en navegador.

### Principio rector
**Fidelidad documental antes que espectacularidad visual.** Si la fuente no respalda un dato, no lo inventes ni lo completes: exclúyelo o presenta explícitamente la limitación.
