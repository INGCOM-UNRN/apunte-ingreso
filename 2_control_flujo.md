---
title: Control de Flujo
short_title: 2 - Control de Flujo
subtitle: Condicionales y estructuras de repetición en Python.
---

(control-flujo)=
# Control de Flujo

::::{tip} Mapa del Capítulo
:class: dropdown

Este capítulo te enseña a hacer que tus programas **piensen** y **repitan** acciones tomando decisiones. ¡Es donde tu código cobra vida!

```{mermaid}
graph TD
    A[Introducción] --> B[Condicionales if/elif/else]
    B --> C[Lazos while]
    C --> D[Lazos for]
    D --> E[Control de Lazos]
    E --> F[Patrones Comunes]
    
    style A fill:#e3f2fd
    style B fill:#fff9c4
    style C fill:#e1bee7
    style D fill:#e1bee7
    style E fill:#ffccbc
    style F fill:#c8e6c9
```

**⏱️ Tiempo estimado:** 5-7 horas

**Lo que vas a aprender:**
- Cómo hacer que tu programa tome decisiones (`if`, `elif`, `else`)
- Repetir acciones con `while` y `for`
- Controlar lazos con `break` y `continue`
- Patrones comunes de programación

**Al final podrás:**
- Crear programas que reaccionan a diferentes situaciones
- Evitar repetir código usando lazos
- Construir menús interactivos y validaciones
::::

## Introducción y Motivación

### ¿Qué es el Control de Flujo?

Hasta ahora, tus programas han sido como seguir una receta paso a paso: hacés **una cosa tras otra**, siempre en el mismo orden. Pero los programas reales necesitan ser **inteligentes**:

:::::{grid} 1 1 2 2

::::{grid-item-card} Sin Control de Flujo
```python
# Programa "tonto"
print("Buenos días")
print("Buenas tardes")
print("Buenas noches")
# Siempre saluda igual...
```
::::

::::{grid-item-card} Con Control de Flujo
```python
# Programa "inteligente"
hora = 14
if hora < 12:
    print("Buenos días")
elif hora < 20:
    print("Buenas tardes")
else:
    print("Buenas noches")
# ¡Saluda según la hora! 
```
::::

:::::

### Analogía del Semáforo 🚦

Imaginate que sos un auto en una intersección:

```{mermaid}
graph LR
    A[Llego al semáforo] --> B{¿Qué color?}
    B -->|🟢 Verde| C[Paso]
    B -->|🟡 Amarillo| D[Freno con cuidado]
    B -->|🔴 Rojo| E[Me detengo]
    
    style A fill:#e3f2fd
    style B fill:#fff9c4
    style C fill:#c8e6c9
    style D fill:#fff3e0
    style E fill:#ffcdd2
```

Eso es **{term}`control de flujo`**: tu programa "mira" la situación y **decide** qué hacer, como vos decidís según el color del semáforo.

:::{important} ¿Por qué es tan importante?
El {term}`control de flujo` es lo que convierte una secuencia fija de instrucciones en un programa que puede:

- **Tomar decisiones** basadas en datos.
- **Evitar repetir código** (no copies y pegues 100 veces).
- **Crear programas interactivos** que responden al usuario.
- **Manejar diferentes escenarios** en el mismo programa.
:::

### Ejemplos del Mundo Real

Todos estos usan {term}`control de flujo`:

:::::{grid} 1 1 2 2

::::{grid-item-card} 🏧 Cajero Automático
- **Decisión:** ¿El PIN es correcto?
- **Repetición:** Permitir 3 intentos.
- **Menú:** Repetir hasta que elija "Salir".
::::

::::{grid-item-card} 🎮 Videojuego
- **Decisión:** ¿El jugador chocó?
- **Repetición:** Lazo principal del juego.
- **Validación:** ¿Quedan vidas?
::::

::::{grid-item-card} 🌡️ Termostato
- **Decisión:** ¿Temperatura baja?
- **Repetición:** Revisar cada minuto.
- **Acción:** Encender/apagar calefacción.
::::

::::{grid-item-card} 📱 Aplicación de Mensajes
- **Decisión:** ¿Hay conexión?
- **Repetición:** Revisar nuevos mensajes.
- **Validación:** ¿Mensaje válido?
::::

:::::

### ¿Qué Vas a Aprender?

```{mermaid}
mindmap
  root((Control<br/>de Flujo))
    Decisiones
      if simple
      if-else
      if-elif-else
    Repetición
      while
      for
      range
    Control
      break
      continue
      pass
    Patrones
      Validación
      Menús
      Banderas
```

¡Empecemos! 

---

(condicionales)=
## Estructuras Condicionales

### ¿Qué son las Condicionales? 

Las **condicionales** son como las bifurcaciones en un camino: según la situación, tu programa toma un camino u otro.

```{mermaid}
%%{init: {'theme':'base', 'themeVariables': { 'primaryColor':'#e3f2fd','primaryTextColor':'#1565c0','primaryBorderColor':'#1976d2','lineColor':'#1976d2','secondaryColor':'#fff3e0','tertiaryColor':'#f3e5f5','noteBkgColor':'#fff9c4','noteTextColor':'#333'}}}%%
flowchart TD
    inicio([Inicio])
    condicion{edad >= 18?}
    accion[print: Sos mayor de edad<br/>print: Podés votar]
    fin([Fin])
    
    inicio --> condicion
    condicion -->|Verdadero| accion
    condicion -->|Falso| fin
    accion ---> fin
    
    style inicio fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style condicion fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style accion fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    style fin fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
```

::::{tip} Analogía: El Guardia de Seguridad

Imaginate un guardia en la entrada de un boliche:

```python
edad = 17

if edad >= 18:
    print("¡Bienvenido! Pasá")  # Solo si cumple la condición
    
print("Que tengas buen día")  # Esto se ejecuta siempre
```

- **Si** tenés 18+ → te deja pasar Y te saluda.
- **Si** tenés menos → solo te saluda.

El guardia **decide** basándose en tu edad. ¡Eso es una condicional!
::::

---

### La Estructura `if` Simple

La forma más básica: "Si se cumple esto, hacé aquello".

```{code-cell} ipython3
edad = 18

if edad >= 18:
    print("Sos mayor de edad")
    print("Podés votar")
    
print("Este mensaje se muestra siempre")
```

#### Anatomía del `if`

:::::{grid} 1 1 2 2

::::{grid-item}
```python
if edad >= 18:
    print("Mayor")
    print("Votar")
print("Fin")
```
::::

::::{grid-item}
1. **`if`** → palabra clave.
2. **`edad >= 18`** → condición (True/False).
3. **`:`** → dos puntos (obligatorio).
4. **Indentación** → define el bloque.
5. **Sin indentar** → fuera del if.
::::

:::::

:::{important} Indentación: ¡La Clave en Python!

Python es **especial**: usa **espacios** para definir {term}`bloques <Bloque>` de código (no llaves `{}` como otros lenguajes).

Esto significa que:

1. Si no hay indentación, hay un error de sintaxis.
2. Si hay indentación, pero no en todas las instrucciones que queremos agrupar, nos vamos a encontrar con algo que anda, ¡pero no como esperamos!

![Indentación](./2_control_flujo/indentacion.svg)

**Reglas:**
- ✅ Usá **4 espacios** por nivel.
- ✅ Sé **consistente** (siempre 4).
- ✅ Revisá que las instrucciones que deben ir juntas en el bloque, _lo están_.
- ❌ NO mezcles espacios con tabuladores (esto no es un problema en el JupyterLab).
- ❌ NO olvidar los dos puntos `: `.

```python
# ✓ CORRECTO
if edad >= 18:
    print("Mayor de edad")  # 4 espacios
    print("Podés votar")    # 4 espacios

# ✗ ERROR: Sin indentación
if edad >= 18:
print("Mayor de edad")  # IndentationError!

# ✗ ERROR: Inconsistente
if edad >= 18:
  print("Esto")    # 2 espacios
    print("Malo")  # 4 espacios - ¡No funciona!
```

> Aunque los editores de texto para programar nos ayudan con este tema, es importante para que no nos encontremos con sorpresas al copiar y pegar, o si por alguna razón no tenemos acceso a un editor de textos apropiado.

:::

**Experimentá con `if`:**

```{code-cell} ipython3
# Probá cambiando los valores
temperatura = 25

if temperatura > 30:
    print("🔥 Hace mucho calor!")
    print("   Mejor quedarse adentro")

if temperatura < 10:
    print("🥶 Hace mucho frío!")
    print("   Abrigate bien")

if temperatura >= 10 and temperatura <= 30:
    print("Temperatura agradable")
    print("   Buen día para salir")

print(f"Temperatura actual: {temperatura}°C")
```

### La Estructura `if-else`: Dos Caminos

A veces necesitás hacer **una cosa** si se cumple, y **otra cosa diferente** si no se cumple. Ahí usás `if-else`.

```{mermaid}
%%{init: {'theme':'base', 'themeVariables': { 'primaryColor':'#e3f2fd','primaryTextColor':'#1565c0','primaryBorderColor':'#1976d2','lineColor':'#1976d2','secondaryColor':'#fff3e0','tertiaryColor':'#f3e5f5','noteBkgColor':'#fff9c4','noteTextColor':'#333'}}}%%
flowchart TD
    inicio([Inicio])
    condicion{edad >= 18?}
    si[/print: Sos mayor de edad<br/>print: Podés votar/]
    no[/print: Sos menor de edad<br/>print: Todavía no podés votar/]
    fin([Fin])
    
    inicio --> condicion
    condicion -->|Verdadero| si
    condicion -->|Falso| no
    si ---> fin
    no ---> fin
    
    style inicio fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style condicion fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style si fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    style no fill:#ffccbc,stroke:#e64a19,stroke-width:2px
    style fin fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
```

::::{tip} Analogía: Moneda al Aire

Tirás una moneda:
- **Si** sale cara → ganás
- **Si** sale cruz (`else`) → perdés

```python
moneda = "cara"

if moneda == "cara":
    print("¡Ganaste!")
else:
    print("Perdiste")
```

**Siempre pasa UNA de las dos cosas**, nunca ambas.
::::

```{code-cell} ipython3
edad = 16

if edad >= 18:
    print("Sos mayor de edad")
    print("Podés votar")
else:
    print("Sos menor de edad")
    print("Todavía no podés votar")
    
print("Gracias por consultar")
```

:::{note} ¿Cuándo usar `if-else`?
Usá `if-else` cuando:
- Hay **exactamente 2 opciones** (blanco o negro, sí o no).
- **Siempre** querés hacer algo (una cosa u otra).
- Las opciones son **excluyentes** (no pueden pasar las dos).

**Ejemplos:**
- Aprobar/Reprobar un examen.
- Día/Noche.
- Par/Impar.
- Usuario logueado / No logueado.
:::

**Comparación visual:**

:::::{grid} 1 1 2 2

::::{grid-item-card} Solo `if`
```python
if soleado:
    print("¡Vamos al parque!")
# Si no es soleado, no pasa nada
```
**Problema:** ¿Y si llueve? 🤷
::::

::::{grid-item-card} Con `if-else`
```python
if soleado:
    print("¡Vamos al parque!")
else:
    print("Nos quedamos en casa")
# Siempre hacemos algo ✓
```
**Mejor:** Cubrimos ambos casos ✅
::::

:::::

### La Estructura `if-elif-else`: Múltiples Caminos 

Cuando tenés **más de 2 opciones** a elegir, usás `elif` (abreviación de "else if").

```{mermaid}
%%{init: {'theme':'base', 'themeVariables': { 'primaryColor':'#e3f2fd','primaryTextColor':'#1565c0','primaryBorderColor':'#1976d2','lineColor':'#1976d2','secondaryColor':'#fff3e0','tertiaryColor':'#f3e5f5','noteBkgColor':'#fff9c4','noteTextColor':'#333'}}}%%
flowchart TD
    inicio([Inicio])
    var[/input nota/]
    cond1{nota >= 90?}
    cond2{nota >= 70?}
    cond3{nota >= 60?}
    cond4{nota >= 40?}
    excelente[/print: Excelente - A/]
    muybueno[/print: Muy Bueno - B/]
    bueno[/print: Bueno - C/]
    regular[/print: Regular - D/]
    insuficiente[/print: Insuficiente - F/]
    fin([Fin])
    
    inicio --> var
    var --> cond1
    cond1 -->|Verdadero| excelente
    cond1 -->|Falso| cond2
    cond2 -->|Verdadero| muybueno
    cond2 -->|Falso| cond3
    cond3 -->|Verdadero| bueno
    cond3 -->|Falso| cond4
    cond4 -->|Verdadero| regular
    cond4 -->|Falso| insuficiente
    
    excelente ---> fin
    muybueno ---> fin
    bueno ---> fin
    regular ---> fin
    insuficiente ---> fin
    
    style inicio fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style cond1 fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style cond2 fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style cond3 fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style cond4 fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style excelente fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    style muybueno fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    style bueno fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    style regular fill:#ffe0b2,stroke:#f57c00,stroke-width:2px
    style insuficiente fill:#ffccbc,stroke:#e64a19,stroke-width:2px
    style fin fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
```

::::{tip} Analogía: El Semáforo de 4 Luces

Imaginate un semáforo especial con 4 luces que indica velocidades:

```python
velocidad = 80

if velocidad > 120:
    print("🔴 ¡Peligro! Muy rápido")
elif velocidad > 80:
    print("🟡 Cuidado, reducí velocidad")
elif velocidad > 40:
    print("🟢 Velocidad normal, bien")
else:
    print("🔵 Muy lento, podés acelerar")
```

Python revisa **en orden** hasta encontrar la primera que es verdadera. Una vez que encuentra una, **se detiene y no revisa las demás**.
::::

#### Ejemplo Completo: Sistema de Calificaciones

```{code-cell} ipython3
nota = 85

if nota >= 90:
    print("Excelente - Calificación: A")     # 1️⃣ 🟡
    print("   ¡Felicitaciones!")
elif nota >= 70:
    print("Muy Bueno - Calificación: B")     # 2️⃣ ✅
    print("   Buen trabajo")
elif nota >= 60:
    print("Bueno - Calificación: C")         # 3️⃣ 🔴
    print("   Aprobado")
elif nota >= 40:
    print("Regular - Calificación: D")       # 4️⃣ 🔴
    print("   Necesitás mejorar")
else:
    print("Insuficiente - Calificación: F")  # 5️⃣ 🔴
    print("   Reprobado")

print(f"\nTu nota fue: {nota}")
```

#### ¿Cómo Funciona?

**Flujo de evaluación para `nota = 85`**

- 1️⃣ ¿`nota >= 90`? → *No* (85 < 90)
   🟡 Pasa a la siguiente

- 2️⃣ ¿`nota >= 70`? → **¡Sí!** (85 >= 70)  
   ✅ Ejecuta este bloque  
   🛑 **Se detiene acá**, NO se evalúa el resto

- 3️⃣ ~~ ¿`nota >= 60`? ~~ → No se evalúa 🔴
- 4️⃣ ~~ ¿`nota >= 40`? ~~ → No se evalúa 🔴
- 5️⃣ ~~ `else` ~~ → No se ejecuta 🔴

::::

:::::

````{danger} ¡Cuidado con el orden!
El **orden es fundamental**. Python evalúa de arriba hacia abajo y ejecuta **solo la primera** condición verdadera:

:::::{grid} 1 1 2 2

::::{grid-item-card} ✅ CORRECTO
```python
numero = 85

# Orden: más restrictivo → menos
if numero >= 90:
    print("A")
elif numero >= 80:
    print("B")  # ✓ Esta se ejecuta
elif numero >= 70:
    print("C")
else:
    print("F")
```

**Funciona bien:** 85 no pasa el primer filtro, pero sí el segundo.
::::

::::{grid-item-card} ❌ INCORRECTO
```python
numero = 85

# Con el orden invertido, obtenemos el resultado incorrecto
if numero >= 70:
    print("C+")  # ✗ ¡Siempre gana!
elif numero >= 80:
    print("B")   # Nunca se alcanza
elif numero >= 90:
    print("A")   # Nunca se alcanza
```

**Problema:** La primera condición "atrapa" todos los números >= 70, las siguientes nunca se ejecutan.
::::

:::::

````

**Regla de oro:** Siempre ordená de **más específico/restrictivo** a **menos específico**.

#### Comparación: `if` múltiple vs `if`-`elif`-`else`

:::::{grid} 1 1 2 2

::::{grid-item-card} Múltiples `if` separados
```python
edad = 25

if edad >= 18:
    print("Adulto")
if edad >= 13:
    print("Adolescente")
if edad >= 0:
    print("Persona")
```

**Resultado:**
```
Adulto
Adolescente
Persona
```

**Se ejecutan TODAS las que sean `True`**

Como son tres estructura{s} {term}`condicional{es} <Condicional>` separadas, obtenemos tres resultados diferentes.
::::

::::{grid-item-card} Con `if-elif-else`
```python
edad = 25

if edad >= 18:
    print("Adulto")
elif edad >= 13:
    print("Adolescente")
elif edad >= 0:
    print("Persona")
```

**Resultado:**
```
Adulto
```

**Se ejecuta SOLO LA PRIMERA `True`**

Como es una única estructura condicional, obtenemos un solo resultado, el primero que coincida.
::::

:::::

**Experimentá con diferentes valores:**

```{code-cell} ipython3
# Programa: Recomendación de actividad según la temperatura
temperatura = 25

if temperatura >= 35:
    print("🥵 ¡Mucho calor!")
    print("   Recomendación: Quedáte en casa con AC")
elif temperatura >= 25:
    print("☀️ Clima cálido")
    print("   Recomendación: Playa o pileta")
elif temperatura >= 15:
    print(" Clima agradable")
    print("   Recomendación: Caminar o hacer deporte")
elif temperatura >= 5:
    print("🧥 Hace frío")
    print("   Recomendación: Abrigate bien")
else:
    print("🥶 ¡Mucho frío!")
    print("   Recomendación: Quedáte adentro")

print(f"\nTemperatura actual: {temperatura}°C")
```

### Condiciones Anidadas: `if` dentro de `if`

A veces necesitás verificar **una cosa dentro de otra**, como muñecas rusas. Eso se llama **anidamiento**.

::::{tip} Analogía: Seguridad del Banco

Para entrar a la bóveda de un banco:
1. **Primero** verifican tu ID.
2. **Si** tu ID es correcta, **entonces** verifican tu huella.
3. **Si** ambas son correctas → Acceso permitido.

```python
id_correcta = True
huella_correcta = True

if id_correcta:
    print("✓ ID verificada")
    if huella_correcta:
        print("✓ Huella verificada")
        print("   Acceso permitido a la bóveda")
    else:
        print("✗ Huella incorrecta - Acceso denegado")
else:
    print("✗ ID incorrecta - Acceso denegado")
```
::::

**Ejemplo clásico:**

```{code-cell} ipython3
edad = 20
tiene_licencia = True

if edad >= 18:
    print("✓ Tenés la edad mínima")
    if tiene_licencia:
        print("✓ Tenés licencia")
        print("¡Podés manejar!")
    else:
        print("✗ No tenés licencia")
        print(" Necesitás obtener la licencia primero")
else:
    print("✗ Sos menor de edad")
    print("Sos muy chico para manejar")
```

#### Simplificación con Operadores Lógicos

Es común que podamos **simplificar** usando `and` en lugar de anidar cuando la cantidad de resultados posibles es reducida.

:::::{grid} 1 1 2 2

::::{grid-item-card} Anidado (más detallado)
```python
if edad >= 18:
    if tiene_licencia:
        print("Podés manejar")
else:
    print("No podes manejar")
```

Cuando solo necesitamos dos salidas, no es necesario utilizar un segundo `if`.
::::

::::{grid-item-card} Con `and` (más simple)
```python
if edad >= 18 and tiene_licencia:
    print("Podés manejar")
else:
    print("No podes manejar")
```

Al unificar las dos condiciones, simplificamos el código a un único nivel de {term}`indentación`.
::::

:::::

:::{tip} ¿Cuándo anidar vs cuándo usar `and`?

**Usá anidamiento cuando:**
- Querés mostrar mensajes diferentes en ambas partes del condicional.
- La lógica de cada nivel es independiente.
- Necesitás hacer acciones diferentes en cada paso.

**Usá `and` cuando:**
- Todas las condiciones deben ser `True` al mismo tiempo.
- Solo necesitas dos caminos en una condición múltiple.
- Querés código más simple y legible.

**Regla general:** Si podés usar `and`, mejor; hará que el código sea más simple.
:::

**Ejemplo combinado:**

```{code-cell} ipython3
# Sistema de acceso a un club
edad = 21
es_socio = True
tiene_invitacion = False

if edad >= 18:
    if es_socio:
        print("Bienvenido, socio!")
        print("   Entrada gratuita")
    elif tiene_invitacion:
        print("Entrada con invitación")
        print("   Acceso permitido")
    else:
        print("Entrada: $50000")
        print("   Podés pagar en la entrada")
else:
    print("Lo sentimos, solo mayores de 18")
    print("   No podés ingresar")
```

:::{note} Condicionales complejos

No lo hemos explorado en los ejemplos, pero los condicionales lógicos, ¡pueden ser realmente complicados!

Por ejemplo:
```python
puede_acceder = (es_mayor or tiene_permiso) and tiene_dinero and en_bariloche
# Puede entrar si: 
#    - tiene la edad o está autorizado, 
#    - aparte de tambien:
#    - tiene que tener plata y 
#    - tiene que estar en Bariloche.
```

Y tan complicado como sea necesario, pero la clave acá está en que **el resultado final** es un "sí" o un "no". Este condicional no nos indicaría *la razón* por la cual entró o no, solo el resultado final.

:::

### Valores "Truthy" y "Falsy"

En Python, ciertos valores se consideran "falsos" en un contexto booleano:
- `False`, `None`, `0`, `0.0`.
- [Secuencias](./3_estructuras.md) vacías: `""`, `[]`, `{}`, `()`.

Todos los demás valores se consideran "verdaderos". Sin embargo, según las buenas prácticas, es preferible ser **explícito**:

```{code-cell} ipython3
nombre = ""

# Menos claro (aunque funciona)
if nombre:
    print("Tiene nombre")

# ✓ Más claro y explícito
if len(nombre) > 0:
    print("Tiene nombre")

# O mejor aún
if nombre != "":
    print("Tiene nombre")
# Pero documentalo si no es obvio
```

---

(ejemplos-condicionales)=
## Ejemplos Prácticos con Condicionales

A continuación, unos ejemplos de uso de condicionales `if-elif` para clasificación.

### Ejemplo 1: Calculadora de Descuento



En este ejemplo, mostramos cómo aplicar diferentes niveles de descuento basándonos en el monto total de una compra. Usamos una estructura `if-elif-else` para verificar los rangos de precios, empezando por el monto más alto para asegurar que se aplique el mejor descuento posible.



```python

"""Programa que calcula descuento según el monto de compra."""

DESCUENTO_BASICO = 0.05      # 5%
DESCUENTO_INTERMEDIO = 0.10  # 10%
DESCUENTO_PREMIUM = 0.15     # 15%

monto = float(input("Ingrese el monto de compra: $"))

if monto >= 10000:
    descuento = monto * DESCUENTO_PREMIUM
    print(f"Descuento Premium: {DESCUENTO_PREMIUM * 100}%")
elif monto >= 5000:
    descuento = monto * DESCUENTO_INTERMEDIO
    print(f"Descuento Intermedio: {DESCUENTO_INTERMEDIO * 100}%")
elif monto >= 1000:
    descuento = monto * DESCUENTO_BASICO
    print(f"Descuento Básico: {DESCUENTO_BASICO * 100}%")
else:
    descuento = 0
    print("No hay descuento para este monto")

total = monto - descuento
print(f"Monto original: ${monto:.2f}")
print(f"Descuento: ${descuento:.2f}")
print(f"Total a pagar: ${total:.2f}")
```

### Ejemplo 2: Clasificación de Temperatura

Este es un ejemplo de clasificación tradicional en el que se muestra un mensaje diferente por rango de temperatura.

```python
"""Clasifica la temperatura y da recomendaciones."""

temperatura = float(input("Ingrese la temperatura en °C: "))

if temperatura >= 35:
    print("Extremadamente caluroso - Evitá la exposición al sol")
elif temperatura >= 25:
    print("Caluroso - Mantenete hidratado")
elif temperatura >= 15:
    print("Agradable - Clima óptimo")
elif temperatura >= 5:
    print("Fresco - Llevá una campera")
else:
    print("Frío - Abrigate bien")
```

### Ejemplo 3: Segmentación por Edad

En este ejemplo, también usamos condicionales compuestos con operadores lógicos, que nos ayudan a descartar los valores que sabemos que son imposibles primero.

```python
"""Valida si una persona puede acceder a cierto contenido."""

edad = int(input("Ingrese su edad: "))

if edad < 0 or edad > 120:
    print("Error: Edad inválida")
elif edad < 13:
    print("Contenido no disponible para menores de 13 años")
elif edad < 18:
    print("Acceso permitido con supervisión de un adulto")
else:
    print("Acceso completo permitido")
```

---

(while-lazos)=
## Lazos indefinidos - `while`: Mientras que...

Un **lazo** (también llamado bucle) permite ejecutar un bloque de código repetidamente. El lazo `while` continúa ejecutándose mientras una condición sea verdadera.

### Sintaxis Básica

```{code-cell} ipython3
while condicion:
    # Bloque de código que se repite
    # mientras la condición sea True
```

### Ejemplo Simple

```{code-cell} ipython3
contador = 1

while contador <= 5:
    print(f"Contador: {contador}")
    contador = contador + 1

print("Fin del lazo")
```

**Salida:**
```
Contador: 1
Contador: 2
Contador: 3
Contador: 4
Contador: 5
Fin del lazo
```

**Diagrama de flujo:**

```{mermaid}
flowchart TD
    inicio --> A
    A[contador = 1] --> B{contador <= 5?}
    B -->|True| C[print contador]
    C --> D[contador = contador + 1]
    D --> B
    B --->|False| E[Fin]
```

````{danger} 🚨 ¡Cuidado con los Lazos Infinitos!

Si la condición **nunca** se vuelve `False`, el lazo se ejecutará **para siempre**:

:::::{grid} 1 1 2 2

::::{grid-item-card} Lazo Infinito (¡Ooops!)

```python
contador = 1
while contador <= 5:
    print(contador)
    # ¡Olvidamos incrementar!
```

**Problema:** `contador` siempre vale 1  
**Resultado:** Imprime "1" infinitamente 😱
**Solución:** Utilizá el botón para detener la celda en Jupyter.
::::

::::{grid-item-card} ✅ Lazo Correcto
```python
contador = 1
while contador <= 5:
    print(contador)
    contador = contador + 1 # ✓ Incrementa
```

**Funciona:** `contador` cambia  
**Resultado:** Imprime 1, 2, 3, 4, 5 y termina ✓
::::

:::::

**Checklist anti-lazos-infinitos:**
- [ ] ¿La condición puede volverse `False`?
- [ ] ¿Modifico las variables de la condición dentro del lazo?
- [ ] ¿Hay una forma de salir del lazo?

**Tip:** Si tu programa "se colgó", probablemente tenés un lazo infinito. Presioná **Ctrl+C** para detenerlo.

````

### Patrones de lazos `while`

Los patrones son fragmentos de código con estructuras comunes. Estos mismos patrones también se aplican a lazos `for`, como veremos más adelante en la sección {ref}`patrones-comunes`.

:::{important} Patrones universales
Estos patrones son **independientes del tipo de lazo**. Lo que importa es la lógica del patrón, no si usás `while` o `for`. Aprendé a reconocer el patrón y luego elegí el lazo más apropiado para tu problema.
:::

(while-acumulador)= 
#### Patrón 1: Acumulador (Sumar números)

Este patrón se utiliza cuando necesitás **acumular** un resultado a través de múltiples iteraciones. La clave es tener una variable externa que guarda el "total" hasta el momento.

Por ejemplo, si querés calcular la suma total de una serie de números, necesitás una variable (el acumulador) que empiece en cero y vaya sumando cada nuevo número que procesás.

**Cómo funciona:**
1.  **Inicialización:** Creás una variable acumuladora con un valor neutro (0 para suma, 1 para multiplicación, "" para cadenas).
2.  **Proceso:** En cada vuelta del lazo, actualizás el acumulador agregándole el valor actual.
3.  **Resultado:** Al finalizar el lazo, la variable contiene el resultado total.

```{code-cell} ipython3
# Calcular la suma de los primeros 10 números
suma = 0  # Acumulador (empieza en 0)
contador = 1

while contador <= 10:
    suma = suma + contador  # Acumula el valor
    contador = contador + 1

print(f"La suma de 1 a 10 es: {suma}")
```

:::{tip} Patrón Acumulador
**Estructura:**
1. Inicializar {term}`acumulador` en 0.
2. En cada vuelta, sumar al {term}`acumulador`.
3. Al final, el {term}`acumulador` tiene el total.

**Usos:** Sumar números, contar elementos, promedios.
:::


(while-contador)= 
#### Patrón 2: Contador clásico y reverso

A veces no querés sumar los valores en sí, sino simplemente saber **cuántas veces** ocurre algo o en qué paso estás. Para esto sirve el patrón contador.

Este patrón utiliza una variable de control que se incrementa (o decrementa) en cada iteración. Es fundamental para controlar lazos `while` que deben ejecutarse un número específico de veces.

**Tipos:**
*   **Ascendente:** Empieza en un valor bajo y sube hasta un límite. Útil para recorrer índices o contar pasos.
*   **Descendente:** Empieza en un valor alto y baja hasta cero. Útil para cuentas regresivas o cuando necesitás procesar algo en orden inverso.

```{code-cell} ipython3
print("Contador ascendente:")
TOPE = 5
posicion = 1

while posicion < TOPE:
    faltantes = TOPE - posicion
    print(f" {posicion} / {faltantes}...")
    posicion = posicion + 1

print("Listo! ")
```

:::{note} Sobre `TOPE`

Aunque no es estrictamente necesario usar una variable en mayúsculas para el valor límite, su uso facilita la lectura al evitar los llamados {term}`números mágicos`.

Además, si tenemos que cambiar el límite, es mucho más fácil hacerlo en un solo lugar.
:::


```{code-cell} ipython3
print("Cuenta regresiva para despegue:")
numero = 10

while numero > 0:
    print(f"   {numero}...")
    numero = numero - 1

print("   ¡DESPEGUE! ")
```

(while-compuesto)= 
#### Patrón 3: Validación con Repetición (Condiciones compuestas)

Este es uno de los usos más potentes del `while`: **garantizar que un dato sea válido**.

A diferencia de un `if` que solo chequea una vez, el `while` chequea **mientras** el dato sea incorrecto. Esto obliga al programa a detenerse y pedir el dato nuevamente hasta que el usuario ingrese algo válido o se cumpla una condición de salida (como agotar intentos).

**Lógica:** "Mientras el dato sea inválido, volvé a pedirlo".

```{code-cell} ipython3
# Pedir contraseña hasta que sea correcta
PASSWORD_CORRECTA = "python123"

# Inicializamos con un valor incorrecto para entrar al lazo
contraseña = input("Ingrese la contraseña: ")

# Este lazo se lee: "Mientras la contraseña sea incorrecta..."
while contraseña != PASSWORD_CORRECTA:
    print(f"❌ Contraseña incorrecta.")
    contraseña = input("Ingrese la contraseña: ")

print("✅ ¡Acceso concedido!")
```

Para evitar quedarnos atrapados en un lazo infinito si el usuario no sabe la contraseña, podemos combinar condiciones lógicas (usando `and`). Así, el lazo continúa solo si la contraseña es incorrecta **Y** todavía quedan intentos disponibles.

```{code-cell} ipython3
# Pedir contraseña hasta que sea correcta O se acaben los intentos
PASSWORD_CORRECTA = "python123"
intentos = 0
MAX_INTENTOS = 3

contraseña = input("Ingrese la contraseña: ")
intentos = intentos + 1

# Este lazo se lee:
# "Mientras la contraseña sea incorrecta Y queden intentos..."
while contraseña != PASSWORD_CORRECTA and intentos < MAX_INTENTOS:
    print(f"❌ Contraseña incorrecta. Te quedan {MAX_INTENTOS - intentos} intentos.")
    contraseña = input("Ingrese la contraseña: ")
    intentos = intentos + 1

if contraseña == PASSWORD_CORRECTA:
    print("✅ ¡Acceso concedido!")
else:
    print("Cuenta bloqueada por seguridad")
```

:::{note} Patrón Validación
Este patrón es **muy común** en programación:
- Sistemas de login.
- Validación de datos.
- Menús interactivos.
- Juegos (seguir jugando mientras...). 
:::

---

## Cadenas como secuencias de caracteres

Hasta ahora hemos usado cadenas de texto ({term}`string`) simplemente como "bloques" de información para mostrar mensajes. Sin embargo, en Python, una cadena es en realidad una **secuencia ordenada de caracteres**.

Esto significa que:
1. Cada caracter tiene una posición única.
2. Podemos acceder a cada caracter individualmente.
3. Podemos recorrer la cadena caracter por caracter.

### Acceso por índice

Al igual que un edificio tiene pisos numerados, una cadena tiene caracteres numerados llamados **índices**.

:::{danger} Importante
En programación, **siempre** empezamos a contar desde el **0**.
- El primer caracter está en la posición 0.
- El segundo caracter está en la posición 1.
- Y así sucesivamente...
:::

```python
palabra = "Python"
# P  y  t  h  o  n
# 0  1  2  3  4  5

print(palabra[0])  # Imprime 'P'
print(palabra[2])  # Imprime 't'
```

Podemos usar esto dentro de un lazo `while` para recorrer una cadena:

```{code-cell} ipython3
mensaje = "Hola"
indice = 0
largo = len(mensaje)  # len() nos dice cuántos caracteres tiene

while indice < largo:
    letra = mensaje[indice]
    print(f"En la posición {indice} está la letra: {letra}")
    indice = indice + 1
```

Aunque esto funciona, Python nos ofrece una herramienta mucho más elegante y directa para hacer esto: el lazo `for`.

(banderas-control)= 
## Banderas de Control

A veces, la condición para detener un lazo no es simple (como llegar a un número) sino que depende de que ocurra un evento específico (encontrar un dato, que el usuario cancele, que ocurra un error).

El patrón de **bandera** (flag) utiliza una variable booleana (True/False) para señalar si ese evento ha ocurrido. El lazo continúa ejecutándose mientras la bandera esté en un estado (ej: `no_encontrado`) y se detiene cuando cambia.

Según la regla de estilo {ref}`0x0006h`, en lugar de usar `break` y `continue` para salir abruptamente de lazos complejos, es preferible usar **banderas**. Esto hace que la lógica de salida sea explícita en la condición del `while`, facilitando la lectura.

### Patrón 4: Bandera Simple

En este ejemplo, usamos la bandera `encontrado` para controlar el lazo. Inicialmente es `False`. Si encontramos el objetivo, la cambiamos a `True`, lo que hará que el `while` termine limpiamente en la próxima evaluación.

```{code-cell} ipython3
"""Búsqueda con bandera de control."""

texto = "Hola Mundo"
objetivo = "M"
encontrado = False
i = 0

while i < len(texto) and not encontrado:
    if texto[i] == objetivo:
        encontrado = True
        print(f"Encontrado en posición {i}")
    i = i + 1

if not encontrado:
    print("No se encontró el caracter")
```

### Patrón 5: Múltiples Banderas

Las banderas brillan cuando tenés múltiples razones para detenerte. En lugar de tener `break` esparcidos por todo el código, combinás las condiciones en el encabezado del `while`.

Aquí el lazo continúa solo si: la entrada NO es válida **Y** los intentos son menores al máximo.

```python
"""Validación de entrada con múltiples condiciones."""

entrada_valida = False
intentos = 0
MAX_INTENTOS = 3

while not entrada_valida and intentos < MAX_INTENTOS:
    edad = int(input("Ingrese su edad (18-100): "))
    intentos = intentos + 1
    
    if edad >= 18 and edad <= 100:
        entrada_valida = True
        print("Edad válida registrada")
    else:
        print(f"Edad inválida. Intentos restantes: {MAX_INTENTOS - intentos}")

if not entrada_valida:
    print("Demasiados intentos inválidos")
```

### Ventajas de las Banderas

1. **Claridad:** El código es más fácil de entender.
2. **Mantenibilidad:** Es fácil agregar condiciones adicionales.
3. **Debugging:** Podés inspeccionar el estado de las banderas.
4. **Testeo:** Las banderas facilitan las pruebas unitarias.


---

(for-lazos)= 
## Lazos definidos - `for`: Para Cada Elemento...

El lazo `for` se usa cuando querés hacer algo **con cada elemento** de una secuencia (como un texto o un rango de números). Es como decir: "**Para cada** cosa en este grupo, hacé esto".

```{mermaid}
%%{init: {'theme':'base', 'themeVariables': { 'primaryColor':'#e3f2fd','primaryTextColor':'#1565c0','primaryBorderColor':'#1976d2','lineColor':'#1976d2','secondaryColor':'#fff3e0','tertiaryColor':'#f3e5f5','noteBkgColor':'#fff9c4','noteTextColor':'#333'}}}%%
flowchart TD
    inicio([Inicio])
    iniciar[secuencia = 'Hola']
    bucle{¿Hay más<br/>elementos?}
    procesar[caracter = siguiente elemento<br/>print: caracter]
    fin([Fin])
    
    inicio --> iniciar
    iniciar --> bucle
    bucle -->|Sí| procesar
    bucle -->|No| fin
    procesar --> bucle
    
    style inicio fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style iniciar fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
    style bucle fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style procesar fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    style fin fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
```

::::{tip} Analogía: Deletrear una Palabra

Imaginate que tenés que deletrear una palabra letra por letra:

```python
palabra = "Hola"

for letra in palabra:
    print(f"Letra: {letra}")
```

**Salida:**
```
Letra: H
Letra: o
Letra: l
Letra: a
```

Python **automáticamente** toma cada caracter del texto, uno por uno, y ejecuta el código para cada uno. ¡No necesitás {term}`contador` ni incremento manual!
::::

:::{note} Cláusula `else` en lazos `for`
Al igual que con los lazos `while`, los lazos `for` también pueden tener una cláusula `else` que se ejecuta cuando el lazo termina normalmente (sin ser interrumpido por un `break`).
:::

---

### Diferencia: `while` vs `for`

La elección entre `while` y `for` depende de si conocés de antemano cuántas veces necesitás repetir el código. El lazo `while` es ideal cuando la cantidad de iteraciones depende de una condición dinámica, mientras que `for` es perfecto para secuencias conocidas o rangos definidos.

:::::{grid} 1 1 2 2

::::{grid-item-card} {term}`while` (Mientras...)
```python
# Usar cuando NO sabés
# cuántas veces repetir

contraseña = ""
while contraseña != "abc123":
    contraseña = input("Contraseña: ")
```

**Cuándo usarlo:**
- Login (hasta que acierte).
- Menús (hasta que salga).
- Validaciones.
::::

::::{grid-item-card} {term}`for` (Para cada...)
```python
# Usar cuando SÍ sabés
# cuántas veces repetir

palabra = "Python"
for letra in palabra:
    print(letra)
```

**Cuándo usarlo:**
- Recorrer textos.
- Repetir N veces (con range).
- Procesar secuencias de datos.
::::

:::::

---

### Iterando sobre un Rango

La función {term}`range()` genera una secuencia de números que podemos usar en lazos `for`. Es útil para repetir una acción un número específico de veces.

```{code-cell} ipython3
# Contar del 0 al 4
for i in range(5):
    print(f"Número: {i}")
```

**La función {term}`range()`** acepta tres argumentos: inicio (opcional), fin (obligatorio, **exclusivo**) y paso (opcional).

```{code-cell} ipython3
# range(stop) - desde 0 hasta stop-1
for i in range(5):
    print(i)  # 0, 1, 2, 3, 4

# range(start, stop) - desde start hasta stop-1 (el 'stop' NO se incluye)
for i in range(2, 6):
    print(i)  # 2, 3, 4, 5

# range(start, stop, step) - con incremento personalizado
for i in range(0, 10, 2):
    print(i)  # 0, 2, 4, 6, 8

# Contando hacia atrás
for i in range(5, 0, -1):
    print(i)  # 5, 4, 3, 2, 1
```

### Iterando sobre Strings

Las cadenas de texto también son secuencias y son el ejemplo perfecto para empezar a iterar:

```{code-cell} ipython3
mensaje = "Python es genial"

for letra in mensaje:
    print(letra, end="-")
# P-y-t-h-o-n- -e-s- -g-e-n-i-a-l-
```

:::{important} Estilo Pythonic
Según la regla {ref}`0x0007h`, en Python es preferible iterar directamente sobre elementos en lugar de usar índices:

```{code-cell} ipython3
palabra = "Programar"

# ❌ Menos Pythonico (estilo C/Java antiguo)
for i in range(len(palabra)):
    print(palabra[i])

# ✓ Pythonico (elegante y directo)
for letra in palabra:
    print(letra)
```
:::

### Usando `enumerate()` cuando necesitás índices

A veces necesitamos tanto el elemento como su posición. `enumerate()` nos da ambos, evitando contadores manuales.

```{code-cell} ipython3
palabra = "Hola"

for indice, letra in enumerate(palabra):
    print(f"Posición {indice}: {letra}")

# Salida:
# Posición 0: H
# Posición 1: o
# Posición 2: l
# Posición 3: a
```

**Empezar desde un índice diferente (ej. para mostrar al usuario):**

```{code-cell} ipython3
palabra = "Python"

for indice, letra in enumerate(palabra, start=1):
    print(f"Letra {indice}: {letra}")
```

### Ejemplo: Tabla de Multiplicar

Este programa toma un número ingresado por el usuario y utiliza un lazo `for` junto con `range()` para generar su tabla de multiplicar del 1 al 10. Es un ejemplo clásico de cómo iterar una cantidad definida de veces para realizar cálculos repetitivos.

```python
"""Genera la tabla de multiplicar de un número."""

numero = int(input("Ingrese un número: "))

print(f"\nTabla de multiplicar del {numero}:")
print("-" * 30)

for i in range(1, 11):
    resultado = numero * i
    print(f"{numero} x {i:2d} = {resultado:3d}")
```

### Ejemplo: Contar Vocales

Aquí vemos cómo recorrer una cadena de texto caracter por caracter. Usamos un lazo `for` para examinar cada letra y un condicional `if` para verificar si es una vocal, incrementando un contador si la condición se cumple.

```{code-cell} ipython3
"""Cuenta las vocales en una frase."""

frase = "Aprender a programar es divertido"
vocales = "aeiouAEIOU"
contador_vocales = 0

for letra in frase:
    if letra in vocales:
        contador_vocales += 1

print(f"La frase tiene {contador_vocales} vocales.")
```

---

(while-vs-for)= 
## `while` vs `for`: ¿Cuándo usar cada uno?

La decisión entre `while` y `for` es fundamental para escribir código claro.

### Usar `while` cuando:

1. **No conocés de antemano cuántas iteraciones necesitás.**
   
   Ejemplo: [patrón de validación de entrada](#while-compuesto), donde seguimos pidiendo datos hasta que el usuario ingrese algo válido.

2. **La condición de parada es compleja.**
   
   Cuando múltiples condiciones determinan si continuar.

3. **El lazo puede no ejecutarse ninguna vez.**
   
   Si la condición inicial es falsa, el bloque `while` se salta por completo.

### Usar `for` cuando:

1. **Iterás sobre una secuencia conocida.**
   Como una cadena de texto o un rango de números. Es la forma *pythonic*.

2. **Conocés exactamente cuántas iteraciones necesitás.**
   Usando `range()`.

3. **Necesitás procesar cada elemento de una colección.**

### Tabla Comparativa

| Aspecto | `while` | `for` |
|---------|---------|-------|
| **Iteraciones**| Número desconocido | Número conocido o secuencia |
| **Condición**| Puede ser compleja | Implícita (hasta terminar secuencia) |
| **Uso típico**| Validaciones, menús | Procesar textos, rangos |
| **Riesgo**| Lazo infinito si no hay cuidado | Menor riesgo |

---

(manipulacion-lazos)= 
## Manipulación de lazos

Python proporciona instrucciones para alterar el flujo dentro de los lazos: `break` y `continue`.

### La instrucción `break`

`break` **termina inmediatamente** el lazo, saltando a la primera instrucción después del mismo.

```{code-cell} ipython3
"""Búsqueda de un caracter usando break."""

texto = "Hola Mundo"
objetivo = "M"

for i in range(len(texto)):
    if texto[i] == objetivo:
        print(f"Encontrado en posición {i}")
        break  # Termina el lazo inmediatamente
    print(f"Revisando posición {i}: {texto[i]}")
else:
    # Este bloque se ejecuta solo si NO se usó break
    print("No se encontró el caracter")
```

:::{note}
El `else` de un lazo `for` o `while` se ejecuta solo si el lazo **termina normalmente**, es decir, sin usar `break`.
:::

### La instrucción `continue`

`continue` **salta el resto de la iteración actual** y pasa a la siguiente vuelta del lazo.

```{code-cell} ipython3
"""Imprimir solo consonantes usando continue."""

frase = "Hola Mundo"
vocales = "aeiouAEIOU "  # Incluimos espacio para saltarlo también

print("Consonantes:", end=" ")
for letra in frase:
    if letra in vocales:
        continue  # Salta vocales y espacios
    
    # Solo procesa consonantes
    print(letra, end="")
# Salida: HlMnd
```

### Comparación: `break` vs `continue`

```{code-cell} ipython3
"""Demostración de break vs continue."""

print("Ejemplo con break (para en 3):")
for i in range(5):
    if i == 3:
        break  # Termina el lazo completamente
    print(f"Valor: {i}")

print("\nEjemplo con continue (salta el 3):")
for i in range(5):
    if i == 3:
        continue  # Salta solo esta iteración
    print(f"Valor: {i}")
```

### `break` y `continue` en lazos anidados

:::{important}
Tanto `break` como `continue` **solo afectan al lazo más interno** donde se encuentran. Para controlar lazos externos, necesitamos usar {ref}`banderas de control <banderas-control>`.
:::

```{code-cell} ipython3
"""break solo termina el lazo interno."""

for i in range(3):
    print(f"Lazo externo: i = {i}")
    for j in range(3):
        if j == 1:
            break  # Solo termina el lazo interno
        print(f"  Lazo interno: j = {j}")
```

Para terminar ambos lazos, usamos una {term}`bandera`:

```{code-cell} ipython3
"""Terminar lazos anidados con bandera."""

terminar = False

for i in range(3):
    print(f"Lazo externo: i = {i}")
    for j in range(3):
        if i == 1 and j == 1:
            terminar = True
            break  # Termina lazo interno
        print(f"  Lazo interno: j = {j}")
    
    if terminar:
        break  # Termina lazo externo

print("Terminado")
```

### ¿Cuándo usar `break` y `continue`?

:::{tip} Preferencia por claridad
Según la regla {ref}`0x0006h`, es preferible usar {ref}`banderas de control <banderas-control>` en lugar de `break` y `continue` cuando el flujo es complejo, porque hace el código más fácil de entender y mantener.
:::

**Casos apropiados para `break`:**
- Búsquedas simples donde querés terminar al encontrar algo.
- Validación de entrada donde querés salir tras validar.

**Casos apropiados para `continue`:**
- Filtrar elementos ("saltar basura") sin anidar condiciones excesivamente.

**Preferir banderas cuando:**
- El lazo tiene múltiples condiciones de salida.
- Necesitás controlar lazos anidados.
- La lógica es compleja y requiere claridad.

(lazos-anidados)= 
## Lazos Anidados

Podés colocar lazos dentro de otros lazos. Cada {term}`iteración` del lazo externo ejecuta completamente el lazo interno.

### Ejemplo: Tabla de Multiplicar Completa

Al anidar dos lazos `for`, podemos generar una tabla de multiplicar completa. El lazo externo controla qué número estamos multiplicando (del 1 al 5), mientras que el interno genera los multiplicadores (del 1 al 10) para cada uno de esos números.

```{code-cell} ipython3
"""Genera tablas de multiplicar del 1 al 5."""

for numero in range(1, 6):
    print(f"\nTabla del {numero}:")
    for multiplicador in range(1, 11):
        resultado = numero * multiplicador
        print(f"{numero} x {multiplicador:2d} = {resultado:3d}")
```

### Ejemplo: Patrón de Asteriscos

Los lazos anidados son ideales para trabajar con coordenadas o estructuras visuales 2D. En este caso, el lazo externo maneja las filas y el interno controla cuántos asteriscos se imprimen en cada fila, creando un patrón triangular.

```{code-cell} ipython3
"""Imprime un triángulo de asteriscos."""

altura = 5

for fila in range(1, altura + 1):
    for columna in range(fila):
        print("*", end="")
    print()  # Nueva línea
```

### Ejemplo: Validación de Múltiples Credenciales

Este ejemplo combina lazos anidados con banderas para un control de flujo robusto.

```{code-cell} ipython3
"""Verificar usuario y contraseña con múltiples intentos permitidos."""

# Credenciales correctas (simuladas)
usuario_valido = "admin"
password_valida = "python123"

# Configuración
max_intentos_usuario = 3
max_intentos_password = 3
acceso_concedido = False

print("=== SISTEMA DE ACCESO ===")

# Lazo externo: intentos de usuario
for intento_usuario in range(1, max_intentos_usuario + 1):
    print(f"\n[Intento de usuario {intento_usuario}/{max_intentos_usuario}]")
    usuario = input("Usuario: ")
    
    if usuario == usuario_valido:
        print("✓ Usuario correcto")
        
        # Lazo interno: intentos de contraseña
        for intento_password in range(1, max_intentos_password + 1):
            print(f"[Intento de contraseña {intento_password}/{max_intentos_password}]")
            password = input("Contraseña: ")
            
            if password == password_valida:
                print("\n✓ ACCESO CONCEDIDO")
                acceso_concedido = True
                break  # Salir del lazo de contraseñas
            else:
                print("✗ Contraseña incorrecta")
        
        # Si encontró la contraseña, salir del lazo de usuarios también
        if acceso_concedido:
            break
        else:
            print("\n✗ Contraseña bloqueada")
            break
    else:
        print("✗ Usuario incorrecto")

if not acceso_concedido:
    print("\n✗ ACCESO DENEGADO - Cuenta bloqueada")
```

:::{warning} Cuidado con la complejidad
Los lazos anidados multiplican las iteraciones:
- Lazo externo: 100 iteraciones
- Lazo interno: 100 iteraciones
- Total: 100 × 100 = 10,000 iteraciones

Usalos con precaución.
:::

---

(errores-comunes-control)= 
## Consejos para errores (y problemas) comunes

### 1. Olvidar la indentación

El error más frecuente al empezar con Python es olvidar los espacios al inicio de las líneas dentro de un bloque. Recordá que Python usa la indentación para saber qué código pertenece al `if` o al lazo.

```python
# ❌ Error de sintaxis
if edad >= 18:
print("Mayor de edad")  # IndentationError

# ✓ Correcto
if edad >= 18:
    print("Mayor de edad")
```

### 2. Usar `=` en lugar de `==`

Es fácil confundir el operador de asignación (`=`) con el de comparación (`==`). Si usás un solo igual en una condición `if` o `while`, Python te dará un error de sintaxis porque estás intentando guardar un valor en lugar de comparar.

```python
# ❌ Asignación en lugar de comparación
if edad = 18:  # SyntaxError
    print("Tiene 18")

# ✓ Correcto
if edad == 18:
    print("Tiene 18")
```

### 3. Lazo infinito

En los lazos `while`, es crucial asegurarse de que la condición eventualmente se vuelva falsa. Si olvidás actualizar la variable que controla el lazo (como un contador), el programa se quedará "colgado" ejecutando el mismo código eternamente.

```python
# ❌ Lazo infinito
contador = 0
while contador < 10:
    print(contador)
    # Olvidamos incrementar contador

# ✓ Correcto
contador = 0
while contador < 10:
    print(contador)
    contador = contador + 1
```

### 4. Condiciones incorrectas en rangos

Cuando clasificamos valores en rangos (como notas o edades), el orden importa mucho. Si chequeamos rangos intermedios antes que los extremos, o si usamos operadores incorrectos, podemos dejar casos sin cubrir o clasificarlos mal. Siempre ordená de más específico a más general.

```python
# ❌ Lógica incorrecta
nota = 85
if nota >= 60 and nota < 90:  # No captura 60-69
    print("Bueno")
elif nota >= 70 and nota < 90:  # Nunca se alcanza
    print("Muy Bueno")

# ✓ Correcto - orden de más específico a general
if nota >= 90:
    print("Excelente")
elif nota >= 70:
    print("Muy Bueno")
elif nota >= 60:
    print("Bueno")
```

### 5. Modificar la variable de control dentro del lazo `for`

Intentar cambiar manualmente el valor de la variable iteradora (la `i` en `for i in...`) dentro del lazo suele ser mala idea en Python. El lazo `for` reasigna la variable automáticamente en cada vuelta, por lo que tus cambios manuales se perderán o crearán confusión.

```{code-cell} ipython3
# ❌ Confuso y propenso a errores
for i in range(5):
    print(i)
    i = 10  # Esto NO afecta la siguiente iteración del for en Python como esperás
            # En la siguiente vuelta, i tomará el siguiente valor del range

# ✓ Correcto: Dejar que el for controle la variable o usar while si necesitás control manual
i = 0
while i < 5:
    print(i)
    if condicion_especial:
        i = 10  # Acá sí afectás el flujo
    i += 1
```

---

(buenas-practicas-control)=
## Buenas Prácticas

### 1. Nombres Descriptivos para Banderas

Las variables booleanas (banderas) deben tener nombres que indiquen claramente qué estado representan, usualmente como una afirmación (ej. `es_valido`, `tiene_acceso`). Evitá nombres genéricos como `flag` o letras sueltas.

```{code-cell} ipython3
# ❌ Poco claro
flag = True
x = False

# ✓ Descriptivo
usuario_autenticado = True
datos_validos = False
```

### 2. Condiciones Legibles

Si tenés un `if` con muchas condiciones unidas por `and` u `or`, es difícil de leer y entender. Es mejor asignar esas condiciones a variables booleanas con nombres explicativos antes del `if`.

```{code-cell} ipython3
# ❌ Difícil de leer
if a > 18 and b == True and c != 0 and (d == "admin" or d == "superuser"):
    hacer_algo()

# ✓ Más claro: asignar condiciones a variables explicativas
es_mayor_edad = a > 18
esta_activo = b == True
tiene_saldo = c != 0
es_administrador = d == "admin" or d == "superuser"

if es_mayor_edad and esta_activo and tiene_saldo and es_administrador:
    hacer_algo()
```

### 3. Evitar Anidación Excesiva

Tener muchos `if` dentro de otros `if` (código "flecha") hace que el programa sea difícil de seguir. A menudo podés simplificar combinando condiciones con `and` o usando "cláusulas de guarda" (retornar o usar `continue` temprano).

```{code-cell} ipython3
# ❌ Muy anidado (Spaghetti code)
if condicion1:
    if condicion2:
        if condicion3:
            if condicion4:
                hacer_algo()

# ✓ Utilizá condiciones combinadas
if condicion1 and condicion2 and condicion3 and condicion4:
    hacer_algo()
```

### 4. Constantes para Valores Mágicos

Evitá usar números sueltos en tus condiciones (como `18` o `65`) porque nadie sabrá qué significan si leen tu código después. Definí constantes con nombres claros en mayúsculas al principio de tu programa.

```{code-cell} ipython3
# ❌ "Números mágicos" (18 y 65 aparecen de la nada)
if edad >= 18 and edad <= 65:
    calcular_descuento()

# ✓ Constantes descriptivas
EDAD_MINIMA = 18
EDAD_MAXIMA = 65

if edad >= EDAD_MINIMA and edad <= EDAD_MAXIMA:
    calcular_descuento()
```

---

(uso-ia-control-flujo)= 
## Uso Ético y Efectivo de la IA en Control de Flujo

:::{important} La IA: Tu Asistente de Aprendizaje, No Tu Reemplazo
Aprender {term}`control de flujo` es aprender a **pensar algorítmicamente**. La IA puede ayudarte a refinar tu lógica, pero no puede desarrollar esta habilidad por vos. **Vos debés ser quien diseñe la solución.**
:::

### Buenas Prácticas para Control de Flujo

#### Generar Ejercicios Adicionales

- "Genera cinco ejercicios sobre condicionales `if-elif-else` que involucren validación de rangos de números".
- "Crea ejercicios de lazos `while` que requieran el uso de banderas de control".

#### Obtener Pistas sobre Lógica

- "Tengo un programa que debe verificar si un número está entre 10 y 20. Mi condición es `if numero > 10 and numero < 20:` pero falla con 10 y 20. ¿Por qué?"
- "Estoy escribiendo un lazo para pedir números hasta que el usuario ingrese 0, pero no sé cómo estructurarlo. ¿Cuál sería el esqueleto básico?"

#### Refactorizar Condiciones Complejas

- "Esta condición es muy larga y difícil de leer: `if (edad >= 18 and tiene_dni and (es_estudiante or es_empleado)) or es_admin:`. ¿Cómo puedo mejorarla?"

### Errores Comunes en este Módulo

:::{warning} No pidas que la IA diseñe tu algoritmo
El diseño del algoritmo (decidir qué condiciones usar, cómo estructurar el lazo, cuándo terminar) es **la habilidad que estás aprendiendo**. Si la IA lo hace por vos, no estás aprendiendo nada.

**Desarrollá tu algoritmo primero**, luego pedí ayuda para refinarlo.
:::

### Ejercicio de Reflexión

Antes de pedir ayuda a la IA sobre un ejercicio de {term}`control de flujo`, preguntate:

1. ¿Cuál es la condición que quiero verificar?
2. ¿Qué debe pasar si es verdadera? ¿Y si es falsa?
3. ¿Necesito repetir algo? ¿Cuántas veces? ¿Hasta cuándo?

Si podés responder estas preguntas, **ya sabés cómo resolver el ejercicio**. La IA solo debería ayudarte con detalles de sintaxis o refinamiento.

---

## Resumen Visual del Capítulo 

### Mapa Mental Completo

```{mermaid}
mindmap
  root((Control<br/>de Flujo))
    Condicionales
      if simple
        Una decisión
        Puede no ejecutarse
      if-else
        Dos caminos
        Siempre uno se ejecuta
      if-elif-else
        Múltiples opciones
        Solo una se ejecuta
      Anidadas
        if dentro de if
        Simplificar con and/or
    Bucles
      while
        Mientras condición True
        Puede nunca ejecutarse
        Usar para validaciones
      for
        Para cada elemento
        Sobre listas strings range
        Más seguro que while
      Anidados
        Lazo dentro de lazo
        Cuidado con complejidad
    Control
      break
        Sale del bucle
        Para búsquedas
      continue
        Salta esta vuelta
        Para filtrar
      pass
        Placeholder
        Para código futuro
    Patrones
      Acumulador
        Sumar valores
      Contador
        Contar elementos
      Validación
        Repetir hasta correcto
      Menú
        Lazo hasta salir
```

---


### Tabla de Referencia Rápida

| Concepto | Cuándo Usarlo | Ejemplo | Salida |
|----------|---------------|---------|---------|
| **if**| Una decisión | `if x > 0: print("+")`  | Puede no mostrar nada |
| **if-else**| Dos caminos | `if par: ... else: ...` | Siempre ejecuta uno |
| **if-elif-else**| 3+ opciones | Notas A/B/C/D | Solo ejecuta uno |
| **while**| No sabés cuántas veces | Login, menú | Hasta que condición cambie |
| **for**| Sabés la secuencia | Procesar lista | Una vez por elemento |
| **{term}`break`**| Salir ya | Encontraste algo | Sale del bucle |
| **{term}`continue`**| Saltar esta vez | Ignorar elemento | Pasa al siguiente |

---

### Lo Más Importante 

:::{important} Los 3 Conceptos Clave
1. **Condicionales**→ Tu programa **decide** qué hacer
2. **Bucles**→ Tu programa **repite** sin copiar código
3. **Control**→ Tu programa **responde** a situaciones diferentes
:::

---

### Próximos Pasos 

**¡Felicitaciones! Ya podés:**
- ✅ Crear programas que toman decisiones
- ✅ Repetir acciones eficientemente
- ✅ Validar entrada del usuario
- ✅ Crear menús interactivos
- ✅ Resolver problemas más complejos

**En el Capítulo 3: Listas aprenderás:**
- 📋 Crear y manipular listas de datos
- 🔍 Acceder y modificar elementos
- ➕ Agregar y eliminar elementos
- 🔄 Iterar sobre listas con `for`
- 🎯 Combinar listas con {term}`control de flujo` para resolver problemas reales

:::{tip} 💪 La Práctica Hace al Maestro
El {term}`control de flujo` **se domina practicando**. 

**Tu plan de acción:**
1. ✍️ Hacé todos los ejercicios del capítulo
2. Repasá los ejemplos y modificalos
3. 🎮 Creá tus propios programas pequeños
4.  Debuggeá errores (aprendés mucho así)
5. Combiná condicionales y bucles creativamente

**Recordá:** Cada programador empezó donde estás vos ahora. ¡Seguí adelante!
:::


---

(glosario-control-flujo)=
## Glosario 

```{glossary}
Control de flujo
: Capacidad de un programa para tomar decisiones y repetir acciones según condiciones. Permite que el código no solo ejecute instrucciones secuencialmente, sino que "piense" y se adapte.

Condicional
: Instrucción que ejecuta código diferente según si una condición es verdadera o falsa. Las principales son {term}`if`, {term}`if-else` y {term}`if-elif-else`.

if
: Estructura {term}`condicional` básica que ejecuta un bloque de código solo si una condición es `True`. Sintaxis: `if condicion:`. Si la condición es `False`, el bloque se salta.

if-else
: Estructura {term}`condicional` con dos caminos: uno si la condición es `True` (bloque `if`) y otro si es `False` (bloque `else`). Siempre ejecuta exactamente uno de los dos bloques.

if-elif-else
: Estructura {term}`condicional` con múltiples opciones. Evalúa condiciones en orden y ejecuta el bloque del primer `True` encontrado. El `else` final es opcional y captura todos los casos no contemplados.

Condición anidada
: Estructura {term}`condicional` dentro de otra. Se usa para verificar múltiples condiciones en secuencia. Puede simplificarse usando {term}`operadores lógicos <operador lógico>`.

Bloque
: Conjunto de instrucciones agrupadas por indentación (4 espacios). En Python, la indentación define qué código pertenece a una estructura de control.

Indentación
: Espacios al inicio de una línea que definen la estructura del código. Python requiere indentación consistente (4 espacios es el estándar). Errores de indentación causan `IndentationError`.

Lazo
: Estructura que repite un bloque de código múltiples veces. Los dos tipos principales son **while** y **for**. También conocido como **loop** o **bucle**.

while
: Tipo de {term}`lazo` que repite código mientras una condición sea `True`. Se evalúa la condición antes de cada iteración. Si la condición nunca se vuelve `False`, resulta en un {term}`lazo infinito`.

for
: Tipo de {term}`lazo` que itera sobre una secuencia (lista, string, {term}`range()`, etc.). Ejecuta el bloque una vez por cada elemento. No necesita contador manual como {term}`while`.

range()
: Función que genera una secuencia de números. Formas: `range(n)` (0 a n-1), `range(inicio, fin)` (inicio a fin-1), `range(inicio, fin, paso)` (con incremento personalizado).

Iteración
: Una ejecución del bloque de código dentro de un {term}`lazo`. "Primera iteración" es la primera vez, "segunda iteración" es la segunda, etc.

Variable de control
: Variable que controla cuándo termina un . En `while`, se actualiza manualmente. En `for`, se actualiza automáticamente con cada elemento de la secuencia.

Lazo infinito
: {term}`Lazo<lazo>` que nunca termina porque su condición siempre es `True`. Error común al olvidar actualizar la {term}`variable de control` en un {term}`while`.

break
: Palabra clave que **sale inmediatamente** de un bucle, sin importar la condición. Útil para terminar un bucle cuando se encuentra lo que se busca.

continue
: Palabra clave que **salta** el resto de la iteración actual y pasa a la siguiente. No sale del bucle, solo ignora el código restante de esa iteración.

pass
: Palabra clave que no hace nada. Se usa como marcador de posición en bloques vacíos que serán completados después. Sintaxis válida que Python acepta sin error.

Bandera
: Variable booleana usada para controlar el flujo de un programa. Se inicializa (ej: `encontrado = False`) y se cambia cuando ocurre un evento (ej: `encontrado = True`). Se puede utilizar para substituir {term}`break` y {term}`continue`.

Bucle anidado
: {term}`Lazo` dentro de otro bucle. El bucle interno se ejecuta completamente por cada iteración del bucle externo. Útil para procesar estructuras bidimensionales.

Acumulador
: Patrón donde una variable suma valores en cada {term}`iteración` de un bucle. Se inicializa en 0 antes del bucle: `suma = 0`, luego se actualiza: `suma = suma + valor`.

Contador
: Patrón donde una variable cuenta cuántas veces ocurre algo en un bucle. Se inicializa en 0: `contador = 0`, luego se incrementa: `contador = contador + 1` o `contador += 1`.

Operador lógico
: Operador que combina o modifica expresiones booleanas. Los tres principales son `and` (ambos True), `or` (al menos uno True), `not` (invierte el valor).

Números mágicos
: Valores literales numéricos en el código sin explicación de su significado. Dificultan la lectura y el mantenimiento. Ejemplo: `if edad >= 18` (¿por qué 18?). Mejor usar constantes descriptivas: `EDAD_MINIMA = 18`.

Cortocircuito
: Optimización donde Python deja de evaluar una expresión con {term}`operadores lógicos <operador lógico>` cuando ya conoce el resultado. En `and`, si el primero es `False`, no evalúa el segundo. (Conocido en inglés como "Short-circuit")

else en lazos
: Cláusula opcional en {term}`lazos<lazo>` que se ejecuta solo si el bucle termina **normalmente** (sin {term}`break`). Si se usa `break`, el `else` no se ejecuta.
```