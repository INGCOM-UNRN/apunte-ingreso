# Directivas optimizadas para el CLI de Gemini con MystMD

A continuación, se presentan las directivas revisadas, siguiendo las mejores prácticas y la sintaxis correcta de MyST.

---

## 0. Terminología especifica

Los bucles son lazos

## 1. Tono y Estilo

- **Tono:** Relajado, académico y técnico.
- **Voz:** Con voseo, en Tercera persona.
- **Complejidad:** Nivel universitario, manteniendo el rigor conceptual sin simplificar en exceso los temas a explicar.

No utilices emojis gráficos a no ser que se pida explícitamente.
---

## 2. Estructura y Formatos Avanzados (MystMD)

Esta sección detalla el uso correcto de las directivas y la sintaxis de MyST para generar contenido enriquecido.

### Admonitions

Para destacar bloques de contenido, utilizá las directivas de `admonition`.

````myst
:::{note}
Este es un bloque de nota. Es útil para añadir información complementaria.
:::

:::{important}
Existen varias clases, como `note`, `important`, `warning`, `tip`, entre otras.
:::
````

### Expresiones Matemáticas (LaTeX)

Para fórmulas en línea, usá el formato `$ ... $`, como en $E=mc^2$. Para bloques de ecuaciones, utilizá `$$...$$`.

```myst
$$\int_a^b f(x) dx = F(b) - F(a)$$
```

### Figuras y Diagramas

Para imágenes, empleá la directiva `figure`. Para diagramas, creá archivos SVG en un subdirectorio específico.

#### Organización de Diagramas SVG

**Convención de nombres y ubicación:**
- Los diagramas SVG se crean en un subdirectorio con el mismo nombre base que el archivo del apunte
- Ejemplo: para `apunte/13_tad.md`, los SVG van en `apunte/13/`
- Nombres descriptivos: `pila_arreglo.svg`, `cola_circular.svg`, etc.

**Estructura de archivos:**
```
apunte/
├── 13_tad.md
└── 13/
    ├── pila_arreglo.svg
    ├── cola_circular.svg
    └── deque.svg
```

**Referencia en el documento:**
````myst
```{figure} 13/pila_arreglo.svg
:label: fig-pila-arreglo
:align: center
:width: 90%

Pila implementada con arreglo. El índice `tope` indica la posición del último elemento.
```
````

**Estilo visual de los SVG:**
- Mantené consistencia con los SVG existentes del proyecto
- Usá colores coherentes por tipo de estructura (ej: rojo/azul para pilas, verde para colas, morado para deques)
- Incluí ejemplos de código en el SVG cuando sea relevante
- Especificá dimensiones apropiadas (viewBox) para escalabilidad

### Ejercicios y Soluciones

Para plantear problemas y sus correspondientes soluciones, usá las directivas `exercise` y `solution`. Esto permite una enumeración automática y la posibilidad de ocultar las soluciones.

````myst
```exercise
:label: mi-ejercicio
¿Cuál es la derivada de $f(x) = x^2$?
```

```solution
:for: mi-ejercicio
La derivada de $f(x) = x^2$ es $f'(x) = 2x$.
```
````

### Tablas

MystMD soporta tablas en formato *Github Flavored Markdown* y también directivas como `list-table` para mayor control y la adición de títulos y etiquetas.

```myst
:::{table} Comparación de características
:label: tbl-comparacion

| Característica | Opción A | Opción B |
| :--- | :---: | ---: |
| Velocidad | Alta | Media |
| Costo | Bajo | Alto |
:::
```

### Citas y Bibliografía

Las citas se manejan con la sintaxis `[@clave]` para referencias parentéticas, por ejemplo `[@heagy2017]`, o roles como `{cite:t}`clave`` para citas textuales/narrativas.

---

## 3. Directivas de Contenido y Referencias Cruzadas

### Referencias a Reglas de Estilo

Para mantener la consistencia y precisión, es fundamental referenciar las reglas de estilo documentadas en `../apunte/0_estilo.md`.

1.  **Definí una etiqueta** sobre el elemento que querés referenciar:
    ```myst
    (regla-claridad-0x0000h)=
    ### Claridad en el Código
    El código debe ser legible y autoexplicativo...
    ```

2.  **Referenciá la etiqueta** desde cualquier otro lugar usando el rol `{ref}`:
    ```myst
    La claridad y prolijidad son cruciales. Para más detalles, consultá la regla {ref}`regla-claridad-0x0000h`.
    ```

### Uso Práctico

:::{important} Integración de Referencias

Al generar código que demuestre una buena práctica, la herramienta debe insertar la referencia a la regla correspondiente de forma contextual. Esto asegura que el contenido no solo sea técnicamente correcto, sino que también guíe a los estudiantes hacia la fuente principal de las directrices, consolidando el conocimiento de las **buenas prácticas**.

:::

### Aplicación de cuestiones de estilo

:::{tip} Estilo

Aquí aplica la cuestion de estilo..., seguido de una explicación y el enlace a la misma.

:::

---

## 4. Creación de Diagramas SVG Técnicos

### Guía para Infografías de Estructuras de Datos

Cuando se necesite crear diagramas SVG para estructuras de datos, seguí estas pautas:

#### Estructura Base del SVG

**Opción 1: Usando el CSS compartido (RECOMENDADO)**

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<?xml-stylesheet href="../resources/svg.css" type="text/css"?>
<svg width="600" height="450" viewBox="0 0 600 450" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <!-- Marcadores de flechas -->
    <marker id="arrowhead" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <polygon points="0 0, 10 3, 0 6" fill="var(--unrn-red)"/>
    </marker>
    <marker id="arrowhead-primary" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <polygon points="0 0, 10 3, 0 6" fill="var(--unrn-red)"/>
    </marker>
    <marker id="arrowhead-secondary" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <polygon points="0 0, 10 3, 0 6" fill="var(--unrn-dark-blue)"/>
    </marker>
  </defs>
  
  <!-- Título -->
  <text x="300" y="25" class="title">Título del Diagrama</text>
  
  <!-- Subtítulo (opcional) -->
  <text x="300" y="45" class="subtitle">Descripción breve</text>
  
  <!-- Elementos del diagrama usando clases del CSS compartido -->
  <!-- Ejemplo para pila: -->
  <rect x="50" y="60" width="120" height="60" class="stack-node"/>
  <text x="110" y="85" class="label-bold">pila_t</text>
  
  <!-- Ejemplo de código -->
  <rect x="30" y="300" width="540" height="100" class="code-block"/>
  <text x="40" y="320" class="code">int *ptr = malloc(sizeof(*ptr));</text>
</svg>
```

**Opción 2: CSS incrustado (solo si se necesita personalización específica)**

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<svg width="600" height="450" viewBox="0 0 600 450" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <style>
      .node { fill: #fff; stroke: #192437; stroke-width: 2; }
      .node-data { fill: #bbdefb; }
      .arrow { fill: none; stroke: #eb2141; stroke-width: 2; }
      .label { font-family: 'Lato', Arial, sans-serif; font-size: 12px; }
      .title { font-family: 'Fabrikat', Arial, sans-serif; font-size: 16px; font-weight: bold; }
      .code { font-family: 'Share Tech Mono', monospace; font-size: 11px; }
    </style>
    <marker id="arrowhead" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <polygon points="0 0, 10 3, 0 6" fill="#eb2141"/>
    </marker>
  </defs>
  
  <!-- Elementos del diagrama -->
  <!-- ... -->
</svg>
```

#### Paleta de Colores Institucional UNRN

El archivo `resources/svg.css` proporciona una paleta completa basada en los colores institucionales:

**Colores primarios:**
- **Rojo UNRN:** `#eb2141` (principal)
- **Azul oscuro UNRN:** `#192437` (secundario)

**Clases CSS por tipo de estructura (usar con el CSS compartido):**

| Estructura | Clases principales | Colores |
|------------|-------------------|---------|
| **Pilas** | `.stack-node`, `.stack-data`, `.stack-arrow` | Rojos cálidos |
| **Colas** | `.queue-node`, `.queue-data`, `.queue-arrow` | Verdes |
| **Deques** | `.deque-node`, `.deque-data`, `.deque-arrow` | Morados |
| **Listas** | `.list-node`, `.list-data`, `.list-arrow` | Azules |
| **Árboles** | `.tree-node`, `.tree-data`, `.tree-arrow` | Verde natural |
| **Grafos** | `.graph-node`, `.graph-data`, `.graph-edge` | Naranjas |
| **Hash/Mapas** | `.hash-node`, `.hash-data`, `.hash-arrow` | Índigos |

**Tipografías disponibles:**
- **Fabrikat** (títulos y encabezados) - fuente institucional UNRN
- **Lato** (texto general y etiquetas)
- **Share Tech Mono** (código y elementos técnicos)

#### Elementos Comunes con Clases CSS

Al usar el CSS compartido, aplicá estas clases a los elementos SVG:

1. **Nodos de datos:**
   ```xml
   <rect class="stack-node"/>         <!-- Contenedor principal -->
   <rect class="stack-data"/>         <!-- Campo de datos -->
   <rect class="stack-pointer"/>      <!-- Campo de puntero -->
   <rect class="node-null"/>          <!-- Puntero NULL -->
   ```

2. **Flechas:**
   ```xml
   <path class="arrow"/>              <!-- Flecha genérica -->
   <path class="stack-arrow"/>        <!-- Flecha específica de pila -->
   <path class="arrow-dashed"/>       <!-- Flecha punteada -->
   ```

3. **Etiquetas y texto:**
   ```xml
   <text class="title">Título</text>
   <text class="label">Etiqueta</text>
   <text class="label-bold">Importante</text>
   <text class="code">int x = 42;</text>
   <text class="code-comment">// comentario</text>
   ```

4. **Contenedores:**
   ```xml
   <rect class="code-block"/>         <!-- Fondo para código -->
   <rect class="highlight-box"/>      <!-- Caja resaltada -->
   <rect class="info-box"/>           <!-- Caja informativa -->
   ```

#### Ejemplo Completo de Referencias

En el archivo `apunte/13_tad.md`:
```myst
```{figure} 13/pila_arreglo.svg
:label: fig-pila-arreglo
:align: center
:width: 85%

Implementación de pila con arreglo dinámico. El índice `tope` señala 
el último elemento insertado.
```
```

### Validación de Diagramas

Antes de finalizar un SVG, verificá:
- [ ] Dimensiones apropiadas (típicamente 600-800px de ancho)
- [ ] Etiquetas legibles y sin superposiciones
- [ ] Consistencia de colores con diagramas similares
- [ ] Ejemplos de código sin errores de sintaxis
- [ ] ViewBox configurado correctamente para escalabilidad