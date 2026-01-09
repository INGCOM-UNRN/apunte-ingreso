# Presentaciones Estilo Takahashi

Este directorio contiene versiones minimalistas de las presentaciones del curso, siguiendo el **Método Takahashi** de comunicación visual.

## ¿Qué es el Método Takahashi?

El método Takahashi es una técnica de presentación desarrollada por Masayoshi Takahashi que se caracteriza por:

- **Máximo 1-3 palabras por diapositiva**
- **Tipografía extra grande y negrita** (ocupa 70-90% del espacio)
- **Alto contraste** (fondos monocromáticos)
- **Conceptos atómicos**: cada slide = 1 idea
- **Transiciones rápidas** (15-20 segundos por slide)

## Estructura del Directorio

```
takahashi/
├── guidelines.md          # Guía para crear presentaciones Takahashi
├── takahashi.css         # Tema CSS personalizado para Marp
├── 0_introduccion.md     # Introducción al curso
├── 1_fundamentos.md      # Variables, tipos, operadores
├── 2_control_flujo.md    # If, while, for, break, continue
├── 3_estructuras.md      # Listas, tuplas, diccionarios, sets
├── 4_funciones.md        # Definición y uso de funciones
├── 5_modulos.md          # Importar y crear módulos
├── 6_excepciones.md      # Try-except y manejo de errores
├── 7_jupyterlab.md       # Uso de JupyterLab
└── 8_fstrings.md         # Formateo de strings
```

## Tema CSS: takahashi.css

El archivo `takahashi.css` define clases específicas para diferentes tipos de diapositivas:

### Clases Disponibles

- **`title`**: Títulos de sección (fondo rojo UNRN, texto gigante)
- **`emphasis`**: Énfasis extremo (fondo negro, texto con stroke)
- **`alert`**: Alertas y advertencias (fondo rojo brillante)
- **`comparison`**: Comparaciones visuales (fondo gris claro)
- **`code`**: Bloques de código (fondo azul oscuro)
- **`default`**: Estilo por defecto (texto negro sobre blanco)
- **`final`**: Diapositiva de cierre (gradiente animado)

### Uso de Clases

```markdown
<!-- _class: title -->
# **VARIABLES**

---

<!-- _class: emphasis -->
# MUY
# IMPORTANTE

---

<!-- _class: alert -->
# ¡CUIDADO!

---

<!-- _class: code -->
\`\`\`python
x = 10
\`\`\`
```

## Generar PDFs con Marp

Para convertir las presentaciones a PDF:

```bash
# Instalar Marp CLI
npm install -g @marp-team/marp-cli

# Convertir una presentación
marp takahashi/1_fundamentos.md --pdf --theme takahashi/takahashi.css

# Convertir todas
for file in takahashi/*.md; do
  [[ "$file" == *"guidelines"* ]] && continue
  marp "$file" --pdf --theme takahashi/takahashi.css
done
```

## Presentar con Marp

```bash
# Modo presentación en el navegador
marp takahashi/1_fundamentos.md --server --theme takahashi/takahashi.css
```

## Filosofía de Diseño

Las presentaciones Takahashi están diseñadas para:

1. **Forzar la síntesis**: reducir conceptos a su esencia
2. **Eliminar distracciones**: solo la idea central
3. **Aumentar el impacto**: tipografía gigante = memorable
4. **Apoyar la narración**: el presentador es el protagonista
5. **Mantener el ritmo**: cambios rápidos mantienen la atención

## Diferencias con Presentaciones Estándar

| Aspecto | Estándar | Takahashi |
|---------|----------|-----------|
| Palabras/slide | 20-50 | 1-3 |
| Bullet points | ✅ | ❌ |
| Imágenes | Medianas | Gigantes o ninguna |
| Código | Bloques largos | Líneas clave |
| Tiempo/slide | 2-5 min | 15-20 seg |
| Rol presentador | Apoyo | Protagonista |

## Consejos para Presentar

1. **Practica el timing**: cada slide debe fluir naturalmente
2. **No leas las diapositivas**: expandí el concepto verbalmente
3. **Usa pausas**: deja que el texto impacte antes de hablar
4. **Energía alta**: el ritmo rápido requiere dinamismo
5. **Cuenta historias**: las palabras son disparadores

## Personalización

Para crear tus propias presentaciones Takahashi:

1. Copia la plantilla base con el frontmatter:
   ```yaml
   ---
   marp: true
   theme: takahashi
   paginate: false
   ---
   ```

2. Usa las clases CSS según el tipo de contenido

3. Mantén el foco en **una idea por slide**

4. Prefiere **números grandes**, **emojis** y **símbolos** cuando sea posible

5. Usa **negritas** para palabras clave: `**IMPORTANTE**`

## Referencias

- [Método Takahashi (Wikipedia)](https://en.wikipedia.org/wiki/Takahashi_method)
- [Marp - Markdown Presentation Ecosystem](https://marp.app/)
- [UNRN.css](../presentaciones/UNRN.css) - Tema base de la universidad

---

**Creado para el Curso de Ingreso - Ingeniería en Computación - UNRN Andina**
