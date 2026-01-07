# Diagramas SVG - Capítulo 3: Estructuras de Datos

Este directorio contiene diagramas SVG utilizados en el Capítulo 3 del apunte para hacer el aprendizaje más visual e intuitivo.

## 📊 Diagramas Disponibles

### Listas
- **`lista_indices.svg`** - Visualiza cómo funcionan los índices positivos y negativos en las listas
- **`slicing.svg`** - Muestra ejemplos de slicing (rebanado) de listas con diferentes parámetros
- **`lista_metodos.svg`** - Catálogo visual de métodos de listas organizados por categoría (agregar, eliminar, buscar, ordenar, copiar)
- **`lista_anidada.svg`** - Ilustra listas dentro de listas (matrices) con analogías y ejemplos de acceso

### Tuplas
- **`lista_vs_tupla.svg`** - Compara las características de listas (mutables) vs tuplas (inmutables)
- **`tupla_unpacking.svg`** - Visualiza el desempaquetado de tuplas con múltiples ejemplos prácticos

### Diccionarios
- **`diccionario.svg`** - Ilustra la estructura clave-valor de los diccionarios
- **`dict_metodos.svg`** - Métodos esenciales de diccionarios con ejemplos de uso (.get, .update, .keys, .values, .items)

### Sets
- **`set_operaciones.svg`** - Diagrama de Venn mostrando operaciones de conjuntos (unión, intersección, diferencia)

### Strings
- **`string_metodos.svg`** - Catálogo completo de métodos de strings organizados por categoría (transformación, búsqueda, reemplazo, división, validación)

### Comprensiones
- **`comprension_listas.svg`** - Anatomía de list comprehensions con comparación entre forma tradicional y concisa

### Conceptos Avanzados
- **`memoria_referencias.svg`** - Visualización de cómo Python maneja referencias y memoria para tipos mutables e inmutables
- **`estructuras_comparacion.svg`** - Tabla comparativa de las cuatro estructuras principales de datos en Python
- **`cuando_usar_que.svg`** - Guía rápida con árbol de decisión para elegir la estructura apropiada

##  Características de los Diagramas

Todos los diagramas están diseñados con:
- ✅ **Colores consistentes** por tipo de estructura
- ✅ **Iconos visuales** para facilitar la memoria
- ✅ **Ejemplos prácticos** en código
- ✅ **Comentarios explicativos** inline
- ✅ **Formato responsive** (SVG escalable)

## 📝 Uso en el Apunte

Estos diagramas se referencian en el archivo `3_estructuras.md` usando la sintaxis de MyST:

```markdown
```{figure} ./3_estructuras/nombre_diagrama.svg
:name: fig-nombre
:align: center
:width: 90%

Descripción del diagrama
```
```

## 🔧 Actualización

Si necesitás modificar algún diagrama:
1. Editá el archivo SVG correspondiente
2. Los cambios se reflejarán automáticamente en el documento compilado
3. Mantené la paleta de colores consistente:
   - Listas: Azul (#3498db)
   - Tuplas: Morado (#8e44ad)
   - Diccionarios: Naranja (#f39c12)
   - Sets: Verde (#27ae60)
   - Strings: Cyan (#16a085)

## Filosofía "Explain Like I'm Five"

Todos los diagramas siguen el enfoque pedagógico del apunte:
- Usan **analogías del mundo real**
- Muestran **el antes y el después**
- Incluyen **casos de error comunes**
- Proveen **ejemplos prácticos inmediatos**

## 📊 Estadísticas

- **Total de diagramas:** 14
- **Tamaño aproximado:** ~90 KB
- **Formato:** SVG (vectorial escalable)
- **Compatibilidad:** Todos los navegadores modernos
