---
title: Manejo de Excepciones
short_title: 0x0002h - Excepciones
subtitle: Aprende a manejar errores como un profesional
---

Este tema no es fundamental para aprobar el curso de ingreso, está para ayudarlos a lograr el mejor código.

(excepciones-capitulo)=
#  Manejo de Excepciones

::::{grid} 1 1 2 2

:::{grid-item-card} ¿Qué aprenderás?
Dominarás el arte de manejar errores en Python para crear programas robustos y confiables.
:::

:::{grid-item-card} ⏱️ Tiempo estimado
60-90 minutos de lectura y práctica
:::
::::

##  Introducción: Los errores son parte del juego

````{margin}
```{tip}
Los errores no son tus enemigos, ¡son oportunidades para hacer tu código más robusto!
```
````

Imagina que estás construyendo un puente 🌉. ¿Qué pasa si viene un terremoto? ¿Una inundación? ¿Mucho tráfico? Un buen ingeniero no solo construye el puente, sino que también planifica qué hacer cuando las cosas salen mal.

En programación es igual. Tu código puede enfrentar:
-  Usuarios que ingresan datos incorrectos
-  Archivos que no existen
-  Conexiones de red que fallan
-  Memoria que se agota

Las **excepciones** son la forma de Python de decir: "¡Oye, algo salió mal!" Y con `try-except` podemos decir: "No te preocupes, yo me encargo".

::::{grid} 1 1 2 2

:::{grid-item-card} Sin manejo de excepciones
```python
edad = int(input("Edad: "))
# Usuario escribe "abc"
# ¡Boom! Programa sale directamente.
```
**Resultado:**💀 Programa terminado abruptamente
:::

:::{grid-item-card} ✅ Con manejo de excepciones
```python
try:
    edad = int(input("Edad: "))
except ValueError:
    print("Eso no es un número")
    edad = 0
#  ¡Programa sigue funcionando!
```
**Resultado:**Usuario puede reintentar
:::
::::

---

(que-son-excepciones)=
## ¿Qué es una Excepción?

```{figure} ./6_excepciones/try_except_flujo.svg
:name: fig-flujo-excepciones
:align: center
:width: 90%

Flujo de ejecución cuando usamos try-except
```

### Pensemos con una analogía

**Excepción = Alarma de seguridad**

Imagina que tu casa tiene una alarma de seguridad:
1. **Try** = Intentar hacer algo (entrar a casa)
2. **Excepción** = Alarma que se dispara si algo sale mal
3. **Except** = Protocolo de qué hacer si suena la alarma

```{code-cell} ipython3
# Veamos una excepción en acción
def dividir_pizza(porciones, personas):
    """Divide la pizza entre personas"""
    return porciones / personas

# ¡Ups! No hay personas
resultado = dividir_pizza(8, 0)
```

```{error}
ZeroDivisionError: division by zero

¡Python nos está diciendo que algo imposible pasó!
```

###  Excepciones versus Errores de Sintaxis

::::{tab-set}

:::{tab-item} Error de Sintaxis
```python
# ❌ Python ni siquiera puede leer esto
if x = 5:  # SyntaxError
    print(x)
```
Es como escribir una oración con palabras incorrectas.
Python dice: "No entiendo lo que escribiste".
:::

:::{tab-item} Excepción
```python
# ✓ Python entiende el código...
x = 5
y = 0
resultado = x / y  # ZeroDivisionError
# ...pero la operación es imposible
```
Es como pedir una receta válida pero con ingredientes imposibles.
Python dice: "Entiendo, pero no puedo hacer eso".
:::

::::

```{admonition} Diferencia clave
:class: note

- **Error de sintaxis**: Python no puede ni empezar
- **Excepción**: Python intenta, pero algo sale mal 
```

###  Anatomía de una Excepción (el Traceback)

Cuando ocurre una excepción, Python nos da un **traceback** (rastreo). Es como una pista de cómo llegamos al error:

```{code-cell} ipython3
def hacer_cafe():
    return moler_granos()

def moler_granos():
    return usar_molino(0)

def usar_molino(velocidad):
    return 100 / velocidad  # 

# Intentemos hacer café
hacer_cafe()
```

````{dropdown} Ver el Traceback completo
```
Traceback (most recent call last):          ← Empieza aquí
  File "cafe.py", line 10, in <module>      
    hacer_cafe()                            ← 1° llamada
  File "cafe.py", line 2, in hacer_cafe    
    return moler_granos()                   ← 2° llamada  
  File "cafe.py", line 5, in moler_granos  
    return usar_molino(0)                   ← 3° llamada
  File "cafe.py", line 8, in usar_molino   
    return 100 / velocidad                  ← ¡AQUÍ está el problema!
ZeroDivisionError: division by zero         ← Tipo de error + mensaje
```

**¿Cómo leerlo?**
1. Lee de **abajo hacia arriba** para encontrar el error
2. La última línea dice **qué**pasó
3. Las líneas superiores dicen **dónde**pasó
````

---

(tipos-excepciones)=
##  Tipos Comunes de Excepciones

Python tiene una familia de excepciones. Conocerlas es como conocer las señales de tránsito.

```{figure} ./6_excepciones/jerarquia_excepciones.svg
:name: fig-jerarquia-excepciones
:align: center
:width: 95%

Jerarquía de excepciones en Python
```

### Las "Top 10" Excepciones

::::{tab-set}

:::{tab-item} ValueError 
**Problema:**El valor es del tipo correcto, pero no tiene sentido

```{code-cell} ipython3
# Ejemplos de ValueError
numero = int("abc")  # ❌ "abc" no es un número
edad = int("25.5")   # ❌ tiene punto decimal
```

**Analogía:**Es como pedirle a alguien un número entre `1` y `10`, y te dicen `"banana"`.
:::

:::{tab-item} `TypeError`
**Problema:**Usaste el tipo de dato equivocado

```{code-cell} ipython3
# Ejemplos de TypeError
resultado = "5" + 3        # ❌ texto + número
longitud = len(42)         # ❌ los números no tienen longitud
lista[1.5]                 # ❌ índice debe ser entero
```

**Analogía:**Es como intentar usar un destornillador para clavar un clavo.
:::

:::{tab-item} `KeyError` 
**Problema:**Buscaste una clave que no existe en un diccionario

```{code-cell} ipython3
persona = {"nombre": "Ana", "edad": 20}
ciudad = persona["ciudad"]  # ❌ no existe "ciudad"
```

**Analogía:**Buscas la llave de un cuarto que no existe en tu casa.
:::

:::{tab-item} `IndexError` 📍
**Problema:**Intentaste acceder a una posición que no existe en una lista

```{code-cell} ipython3
frutas = ["🍎", "🍌", "🍊"]
fruta = frutas[10]  # ❌ solo hay 3 elementos (0, 1, 2)
```

**Analogía:**Intentas ir al piso 20 de un edificio de 5 pisos.
:::

:::{tab-item} `FileNotFoundError `
**Problema:**El archivo que buscas no existe

```{code-cell} ipython3
archivo = open("datos_secretos.txt")  # ❌ archivo no existe
```

**Analogía:**Buscas un libro en la biblioteca que nunca fue comprado.
:::

:::{tab-item} `ZeroDivisionError`
**Problema:**Intentaste dividir por cero (¡matemáticamente imposible!)

```{code-cell} ipython3
resultado = 10 / 0   # ❌ división por cero
resto = 10 % 0       # ❌ módulo por cero
```

**Analogía:**Intentas repartir `10` pizzas entre `0` personas.
:::

:::{tab-item} `AttributeError`
**Problema:**El objeto no tiene ese atributo o método

```{code-cell} ipython3
texto = "hola"
texto.append("!")  # ❌ strings no tienen .append()

numero = 42
numero.upper()     # ❌ números no tienen .upper()
```

**Analogía:**Le pides a un gato que ladre.
:::

:::{tab-item} `ImportError` 
**Problema:**No se puede importar el módulo

```{code-cell} ipython3
import modulo_magico  # ❌ ese módulo no existe
from math import funcion_secreta  # ❌ no está en math
```

**Analogía:**Intentas usar una herramienta que no está en tu caja.
:::

::::

### La Familia de Excepciones

Las excepciones están organizadas en una jerarquía (familia):

```{mermaid}
graph TD
    A[BaseException<br/>Bisabuelo] --> B[Exception<br/>Abuelo]
    A --> C[SystemExit]
    A --> D[KeyboardInterrupt]
    B --> E[ValueError<br/>]
    B --> F[TypeError<br/>]
    B --> G[LookupError<br/>]
    B --> H[ArithmeticError<br/>]
    G --> I[KeyError ]
    G --> J[IndexError]
    H --> K[ZeroDivisionError]
    
    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#bbf,stroke:#333,stroke-width:3px
    style E fill:#bfb,stroke:#333,stroke-width:2px
    style F fill:#bfb,stroke:#333,stroke-width:2px
    style I fill:#ffb,stroke:#333,stroke-width:1px
    style J fill:#ffb,stroke:#333,stroke-width:1px
    style K fill:#ffb,stroke:#333,stroke-width:1px
```

```{tip}
¿Por qué importa la jerarquía? Porque puedes capturar "familias" completas:
- `except LookupError` captura `IndexError` y `KeyError`
- `except ArithmeticError` captura `ZeroDivisionError`, `OverflowError`, etc.
```

---

(try-except)=
##  Try-Except: Tu Escudo Protector

`try-except` es como un paracaídas 🪂: esperas no necesitarlo, pero te salva cuando las cosas salen mal.

### 🎮 Sintaxis Básica

```python
try:
    # Código que PUEDE fallar (zona de riesgo)
    numero = int(input("Número: "))
    resultado = 10 / numero
except:
    # Código que se ejecuta SI falla
    print("¡Algo salió mal!")
```

````{warning} ¡No captures TODO!
Usar `except` sin especificar el tipo es como poner una red para capturar cualquier cosa:

```python
# ❌ MAL: Oculta todos los errores
try:
    codigo_peligroso()
except:
    pass  # ¿Qué pasó? ¡No sabemos!

# ✅ BIEN: Específico y claro
try:
    codigo_peligroso()
except ValueError:
    print("Error de valor específico")
```
````

### Capturar Excepciones Específicas

:::::{tab-set}

::::{tab-item} Un tipo de error
```{code-cell} ipython3
try:
    edad = int(input("¿Cuántos años tienes? "))
    print(f"En 10 años tendrás {edad + 10}")
except ValueError:
    print("❌ Eso no parece un número")
    print("Intenta escribir solo dígitos: 25")
```

**¿Cuándo se ejecuta `except`?**
- ✅ Si el usuario escribe "veinte" → ValueError
- ❌ Si el usuario escribe "20" → No hay error, salta el except
::::

::::{tab-item} Múltiples errores (separados)
```{code-cell} ipython3
try:
    numero = int(input("Número: "))
    resultado = 10 / numero
    archivo = open("datos.txt")
except ValueError:
    print("❌ Número inválido")
except ZeroDivisionError:
    print("❌ No puedes dividir por cero")
except FileNotFoundError:
    print("❌ Archivo no encontrado")
```

Python prueba cada `except` en orden hasta encontrar el correcto.
::::

::::{tab-item} Múltiples errores (agrupados)
```{code-cell} ipython3
try:
    numero = int(input("Número: "))
    resultado = 10 / numero
except (ValueError, ZeroDivisionError) as error:
    print(f"❌ Error en el cálculo: {error}")
```

Útil cuando quieres manejar varios errores de la misma forma.
::::

:::::

### Capturar el Objeto Excepción

Puedes "atrapar" la excepción en una variable para obtener más información:

```{code-cell} ipython3
try:
    numero = int(input("Escribe un número: "))
except ValueError as error:
    print(f" Mensaje del error: {error}")
    print(f"🏷️  Tipo de error: {type(error)}")
    print(f" Argumentos: {error.args}")
```

````{dropdown} 👁️ Ver ejemplo de salida
Si el usuario escribe "abc":
```
 Mensaje del error: invalid literal for int() with base 10: 'abc'
🏷️  Tipo de error: <class 'ValueError'>
 Argumentos: ("invalid literal for int() with base 10: 'abc'",)
```
````

###  Ejemplo Práctico: Calculadora Robusta

```{code-cell} ipython3
def calculadora_segura():
    """Una calculadora que no se rompe nunca"""
    print(" Calculadora Super Segura")
    print("=" * 30)
    
    while True:
        try:
            # Solicitar números
            num1 = float(input("\n1° número (o 'salir'): "))
            num2 = float(input("2° número: "))
            
            # Solicitar operación
            op = input("Operación (+, -, *, /): ")
            
            # Calcular
            if op == '+':
                resultado = num1 + num2
            elif op == '-':
                resultado = num1 - num2
            elif op == '*':
                resultado = num1 * num2
            elif op == '/':
                resultado = num1 / num2
            else:
                print("❌ Operación no válida")
                continue
            
            # Mostrar resultado
            print(f"✅ Resultado: {num1} {op} {num2} = {resultado}")
            
        except ValueError:
            # Usuario escribió texto en vez de número
            print("❌ Por favor ingresa números válidos")
            
        except ZeroDivisionError:
            # Intentó dividir por cero
            print("❌ ¡No puedes dividir por cero!")
            print("En matemáticas, esto es indefinido")
            
        except KeyboardInterrupt:
            # Usuario presionó Ctrl+C
            print("\n👋 ¡Hasta luego!")
            break

# Prueba la calculadora
# calculadora_segura()
```

---

(try-except-else-finally)=
## Try-Except-Else-Finally: El Combo Completo

Python ofrece 4 cláusulas para control total. Es como tener un plan A, B, C y D:

```{figure} ./6_excepciones/try_except_else_finally.svg
:name: fig-try-except-else-finally
:align: center
:width: 95%

Flujo completo de Try-Except-Else-Finally
```

### Las 4 Cláusulas

::::{grid} 1 1 2 2

:::{grid-item-card} 🔵 try
**Siempre se ejecuta primero**

Intenta ejecutar código que puede fallar
:::

:::{grid-item-card} 🔴 except
**Solo si hay error**

Maneja el error específico
:::

:::{grid-item-card} 🟢 else
**Solo si NO hay error**

Código para cuando todo salió bien
:::

:::{grid-item-card} 🟡 finally
**SIEMPRE se ejecuta**

Limpieza, cerrar archivos, etc.
:::

::::

### Ejemplo Completo

```{code-cell} ipython3
def procesar_archivo(nombre):
    """Procesa un archivo con manejo completo de errores"""
    print(f"📂 Procesando: {nombre}")
    print("-" * 40)
    
    archivo = None  # Importante inicializar
    
    try:
        print("1️⃣ Intentando abrir archivo...")
        archivo = open(nombre, 'r')
        
        print("2️⃣ Leyendo contenido...")
        contenido = archivo.read()
        
        print("3️⃣ Procesando datos...")
        lineas = contenido.split('\n')
        
    except FileNotFoundError:
        print("❌ ERROR: El archivo no existe")
        return None
        
    except PermissionError:
        print("❌ ERROR: Sin permisos para leer")
        return None
        
    else:
        # Solo se ejecuta si TODO salió bien
        print(f"✅ ÉXITO: {len(lineas)} líneas procesadas")
        return lineas
        
    finally:
        # SIEMPRE se ejecuta (haya error o no)
        if archivo:
            archivo.close()
            print("Archivo cerrado correctamente")
        print("4️⃣ Limpieza completada")

# Prueba
resultado = procesar_archivo("datos.txt")
```

````{dropdown} 👁️ Ver flujo de ejecución
**Caso 1: Archivo existe y todo sale bien**
```
1️⃣ Intentando abrir archivo...
2️⃣ Leyendo contenido...
3️⃣ Procesando datos...
✅ ÉXITO: 10 líneas procesadas
Archivo cerrado correctamente
4️⃣ Limpieza completada
```

**Caso 2: Archivo no existe**
```
1️⃣ Intentando abrir archivo...
❌ ERROR: El archivo no existe
4️⃣ Limpieza completada
```

Nota: `finally` siempre se ejecuta 
````

### ¿Cuándo usar cada uno?

```{list-table}
:header-rows: 1

* - Cláusula
  - ¿Cuándo?
  - Ejemplo de uso
* - `try`
  - Siempre (es obligatorio)
  - Código que puede fallar
* - `except`
  - Cuando esperas errores
  - Validar entrada de usuario
* - `else`
  - Código que solo corre si todo salió bien
  - Guardar resultados exitosos
* - `finally`
  - Limpieza que DEBE ocurrir siempre
  - Cerrar archivos, conexiones
```

---

(raise-excepciones)=
## Raise: Lanzar Tus Propias Excepciones

A veces TÚ quieres lanzar una excepción. Es como decir: "¡Alto! Esto no debería pasar".

```{figure} ./6_excepciones/raise_excepcion.svg
:name: fig-raise-excepcion
:align: center
:width: 90%

Cómo funciona raise para validar datos
```

### ¿Por qué lanzar excepciones?

**Analogía:**Eres un guardia de seguridad 💂. Si alguien intenta entrar sin credenciales, ¡activas la alarma!

```{code-cell} ipython3
def validar_edad(edad):
    """Valida que la edad sea razonable"""
    if edad < 0:
        raise ValueError("La edad no puede ser negativa")
    if edad > 150:
        raise ValueError("Edad demasiado alta")
    if not isinstance(edad, int):
        raise TypeError("La edad debe ser un número entero")
    
    return edad

# Uso
try:
    edad = validar_edad(-5)
except ValueError as e:
    print(f"❌ Error de validación: {e}")
```

###  Ejemplos Prácticos

:::::{tab-set}

::::{tab-item} Validar parámetros
```{code-cell} ipython3
def calcular_raiz_cuadrada(numero):
    """Calcula la raíz cuadrada"""
    if numero < 0:
        raise ValueError(
            f"No puedo calcular √{numero}. "
            "Los números negativos no tienen raíz real."
        )
    
    return numero **0.5

# Uso seguro
try:
    resultado = calcular_raiz_cuadrada(-25)
except ValueError as e:
    print(f"❌ {e}")
    print("Usa números positivos")
```
::::

::::{tab-item} Validar precondiciones
```{code-cell} ipython3
def dividir_pizza(porciones, personas):
    """Divide pizza entre personas"""
    # Validar precondiciones
    if personas <= 0:
        raise ValueError("Debe haber al menos 1 persona")
    if porciones <= 0:
        raise ValueError("Debe haber al menos 1 porción")
    if personas > porciones:
        raise ValueError(
            f"No hay suficiente pizza: "
            f"{porciones} porciones para {personas} personas"
        )
    
    return porciones / personas

# Uso
try:
    por_persona = dividir_pizza(8, 0)
except ValueError as e:
    print(f"❌ {e}")
```
::::

::::{tab-item} Validar estado
```{code-cell} ipython3
class CuentaBancaria:
    def __init__(self, saldo_inicial):
        self.saldo = saldo_inicial
    
    def retirar(self, monto):
        """Retira dinero de la cuenta"""
        if monto <= 0:
            raise ValueError("El monto debe ser positivo")
        
        if monto > self.saldo:
            raise ValueError(
                f"Fondos insuficientes. "
                f"Saldo: ${self.saldo}, Intentó retirar: ${monto}"
            )
        
        self.saldo -= monto
        return self.saldo

# Uso
cuenta = CuentaBancaria(100)
try:
    cuenta.retirar(150)
except ValueError as e:
    print(f"❌ {e}")
```
::::

:::::

### Re-lanzar Excepciones

A veces quieres capturar, hacer algo, y luego re-lanzar:

```{code-cell} ipython3
def procesar_datos(datos):
    try:
        # Procesar
        resultado = calcular(datos)
        return resultado
    except ValueError as e:
        # Registrar el error
        print(f"Error registrado: {e}")
        # Re-lanzar para que el llamador también lo maneje
        raise

# Uso
try:
    procesar_datos(datos_invalidos)
except ValueError:
    print("El código superior también puede manejar el error")
```

---

(excepciones-personalizadas)=
##  Excepciones Personalizadas

Puedes crear tus propias excepciones para situaciones específicas de tu programa.

### 🏗️ Creando Excepciones Personalizadas

```{code-cell} ipython3
# Excepción básica
class EdadInvalidaError(Exception):
    """Se lanza cuando la edad no es válida"""
    pass

# Excepción con información adicional
class SaldoInsuficienteError(Exception):
    """Se lanza cuando no hay suficiente saldo"""
    def __init__(self, saldo, monto_requerido):
        self.saldo = saldo
        self.monto_requerido = monto_requerido
        self.faltante = monto_requerido - saldo
        super().__init__(
            f"Saldo insuficiente: tienes ${saldo}, "
            f"necesitas ${monto_requerido} "
            f"(faltan ${self.faltante})"
        )

# Excepción con contexto
class ErrorDeValidacion(Exception):
    """Error genérico de validación"""
    def __init__(self, campo, valor, mensaje):
        self.campo = campo
        self.valor = valor
        super().__init__(f"{campo}: {mensaje} (valor: {valor})")
```

### Ejemplo Completo: Sistema de Usuarios

```{code-cell} ipython3
# Definir excepciones personalizadas
class UsuarioError(Exception):
    """Clase base para errores de usuario"""
    pass

class NombreInvalidoError(UsuarioError):
    """Nombre de usuario inválido"""
    pass

class EdadInvalidaError(UsuarioError):
    """Edad inválida"""
    pass

class EmailInvalidoError(UsuarioError):
    """Email inválido"""
    pass

# Clase Usuario con validación
class Usuario:
    def __init__(self, nombre, edad, email):
        self.nombre = self._validar_nombre(nombre)
        self.edad = self._validar_edad(edad)
        self.email = self._validar_email(email)
    
    def _validar_nombre(self, nombre):
        if not nombre:
            raise NombreInvalidoError("El nombre no puede estar vacío")
        if len(nombre) < 2:
            raise NombreInvalidoError("El nombre debe tener al menos 2 caracteres")
        if not nombre.replace(" ", "").isalpha():
            raise NombreInvalidoError("El nombre solo puede contener letras")
        return nombre.title()
    
    def _validar_edad(self, edad):
        if not isinstance(edad, int):
            raise EdadInvalidaError("La edad debe ser un número entero")
        if edad < 0:
            raise EdadInvalidaError("La edad no puede ser negativa")
        if edad > 120:
            raise EdadInvalidaError("La edad parece incorrecta")
        return edad
    
    def _validar_email(self, email):
        if "@" not in email or "." not in email:
            raise EmailInvalidoError("Formato de email inválido")
        return email.lower()
    
    def __str__(self):
        return f"Usuario({self.nombre}, {self.edad}, {self.email})"

# Función para crear usuario con manejo de errores
def crear_usuario_seguro(nombre, edad, email):
    """Crea un usuario con manejo completo de errores"""
    try:
        usuario = Usuario(nombre, edad, email)
        print(f"✅ Usuario creado: {usuario}")
        return usuario
        
    except NombreInvalidoError as e:
        print(f"❌ Error en el nombre: {e}")
        
    except EdadInvalidaError as e:
        print(f"❌ Error en la edad: {e}")
        
    except EmailInvalidoError as e:
        print(f"❌ Error en el email: {e}")
        
    except UsuarioError as e:
        # Captura cualquier otro error de usuario
        print(f"❌ Error de usuario: {e}")
        
    return None

# Pruebas
print("Prueba 1: Datos válidos")
crear_usuario_seguro("Juan Pérez", 25, "juan@email.com")

print("\nPrueba 2: Nombre inválido")
crear_usuario_seguro("A", 25, "juan@email.com")

print("\nPrueba 3: Edad inválida")
crear_usuario_seguro("Juan Pérez", -5, "juan@email.com")

print("\nPrueba 4: Email inválido")
crear_usuario_seguro("Juan Pérez", 25, "email_sin_arroba")
```

### 🌳 Jerarquía de Excepciones Personalizadas

```{code-cell} ipython3
# Crear una jerarquía de excepciones
class AppError(Exception):
    """Clase base para todas las excepciones de la app"""
    pass

class ErrorDeBaseDatos(AppError):
    """Errores relacionados con la base de datos"""
    pass

class ErrorDeConexion(ErrorDeBaseDatos):
    """No se puede conectar a la base de datos"""
    pass

class ErrorDeConsulta(ErrorDeBaseDatos):
    """Error en una consulta SQL"""
    pass

class ErrorDeAutenticacion(AppError):
    """Errores de autenticación"""
    pass

class CredencialesInvalidasError(ErrorDeAutenticacion):
    """Usuario o contraseña incorrectos"""
    pass

class TokenExpiradoError(ErrorDeAutenticacion):
    """El token de sesión expiró"""
    pass

# Ahora puedes capturar por categorías
try:
    # código que puede fallar
    pass
except ErrorDeBaseDatos:
    # Captura TODOS los errores de BD
    print("Error en la base de datos")
except ErrorDeAutenticacion:
    # Captura TODOS los errores de autenticación
    print("Error de autenticación")
except AppError:
    # Captura cualquier error de la app
    print("Error general de la aplicación")
```

---

(debugging)=
##  Debugging: Encontrar y Arreglar Errores

El debugging es el arte de encontrar por qué tu código no funciona.

### Técnicas de Debugging

::::{tab-set}

:::{tab-item} 1. Print Debugging
```{code-cell} ipython3
def calcular_promedio(numeros):
    print(f"Debug: numeros = {numeros}")
    print(f"Debug: tipo = {type(numeros)}")
    
    total = sum(numeros)
    print(f"Debug: total = {total}")
    
    cantidad = len(numeros)
    print(f"Debug: cantidad = {cantidad}")
    
    promedio = total / cantidad
    print(f"Debug: promedio = {promedio}")
    
    return promedio

# Usar
calcular_promedio([10, 20, 30])
```

**Ventajas:**Simple y rápido
**Desventajas:**Hay que borrar los prints después
:::

:::{tab-item} 2. Logging
```{code-cell} ipython3
import logging

# Configurar logging
logging.basicConfig(
    level=logging.DEBUG,
    format='%(levelname)s - %(message)s'
)

def procesar_datos(datos):
    logging.debug(f"Procesando {len(datos)} elementos")
    
    try:
        resultado = operacion_compleja(datos)
        logging.info("Operación exitosa")
        return resultado
    except Exception as e:
        logging.error(f"Error en procesamiento: {e}")
        logging.debug("Datos que causaron el error:", exc_info=True)
        raise

# Niveles de logging:
logging.debug("Información detallada para debugging")
logging.info("Información general")
logging.warning("Advertencia")
logging.error("Error")
logging.critical("Error crítico")
```

**Ventajas:**Profesional, se puede activar/desactivar
**Desventajas:**Más complejo de configurar
:::

:::{tab-item} 3. Assertions
```{code-cell} ipython3
def calcular_factorial(n):
    # Validar precondiciones
    assert n >= 0, "n debe ser no negativo"
    assert isinstance(n, int), "n debe ser entero"
    
    if n == 0:
        return 1
    
    resultado = 1
    for i in range(1, n + 1):
        resultado *= i
        # Validar invariantes
        assert resultado > 0, "El resultado debe ser positivo"
    
    return resultado

# Usar
try:
    calcular_factorial(-5)
except AssertionError as e:
    print(f"❌ Assertion falló: {e}")
```

**Ventajas:**Documenta suposiciones en el código
**Desventajas:**Se desactivan con `python -O`
:::

:::{tab-item} 4. Traceback
```{code-cell} ipython3
import traceback

def funcion_problematica():
    try:
        # Código que puede fallar
        resultado = operacion_riesgosa()
    except Exception as e:
        # Obtener el traceback completo
        tb_string = traceback.format_exc()
        
        print("=" * 50)
        print("ERROR DETALLADO:")
        print("=" * 50)
        print(tb_string)
        print("=" * 50)
        
        # También puedes registrarlo
        with open("errores.log", "a") as log:
            log.write(f"\n{tb_string}\n")
```

**Ventajas:**Información completa del error
**Desventajas:**Puede ser verboso
:::

::::

### Estrategia de Debugging

```{mermaid}
graph TD
    A[¿Hay un error?] --> B[Leer el traceback]
    B --> C[Identificar la línea del error]
    C --> D[¿Entiendes el error?]
    D -->|No| E[Buscar en Google]
    D -->|Sí| F[Agregar prints]
    F --> G[Ejecutar de nuevo]
    G --> H{¿Se resolvió?}
    H -->|No| I[Simplificar el problema]
    I --> F
    H -->|Sí| J[✅ ¡Listo!]
    E --> F
    
    style A fill:#ffebee
    style J fill:#e8f5e9
```

---

(validacion-datos)=
## ✅ Validación de Datos

La validación es el arte de asegurarte de que los datos sean correctos ANTES de usarlos.

### Principios de Validación

```{admonition} Regla de Oro
:class: tip
**Nunca confíes en los datos de entrada**

- Usuarios cometen errores
- APIs pueden cambiar
- Archivos pueden corromperse
- Siempre valida ✅
```

###  Validador Genérico

```{code-cell} ipython3
class Validador:
    """Clase helper para validaciones comunes"""
    
    @staticmethod
    def validar_entero(valor, nombre="valor", minimo=None, maximo=None):
        """Valida que sea un entero en rango"""
        if not isinstance(valor, int):
            raise TypeError(f"{nombre} debe ser entero, no {type(valor).__name__}")
        
        if minimo is not None and valor < minimo:
            raise ValueError(f"{nombre} debe ser >= {minimo}, es {valor}")
        
        if maximo is not None and valor > maximo:
            raise ValueError(f"{nombre} debe ser <= {maximo}, es {valor}")
        
        return valor
    
    @staticmethod
    def validar_texto(valor, nombre="texto", min_largo=None, max_largo=None):
        """Valida que sea texto con largo apropiado"""
        if not isinstance(valor, str):
            raise TypeError(f"{nombre} debe ser texto, no {type(valor).__name__}")
        
        if min_largo is not None and len(valor) < min_largo:
            raise ValueError(
                f"{nombre} debe tener al menos {min_largo} caracteres, "
                f"tiene {len(valor)}"
            )
        
        if max_largo is not None and len(valor) > max_largo:
            raise ValueError(
                f"{nombre} debe tener máximo {max_largo} caracteres, "
                f"tiene {len(valor)}"
            )
        
        return valor.strip()
    
    @staticmethod
    def validar_email(email):
        """Valida formato básico de email"""
        email = email.strip().lower()
        
        if "@" not in email:
            raise ValueError("Email debe contener @")
        
        if "." not in email.split("@")[1]:
            raise ValueError("Email debe tener dominio válido")
        
        partes = email.split("@")
        if len(partes[0]) == 0:
            raise ValueError("Email debe tener usuario antes de @")
        
        return email
    
    @staticmethod
    def validar_opciones(valor, opciones, nombre="opción"):
        """Valida que el valor esté en las opciones permitidas"""
        if valor not in opciones:
            opciones_str = ", ".join(map(str, opciones))
            raise ValueError(
                f"{nombre} debe ser una de: {opciones_str}. "
                f"Recibido: {valor}"
            )
        
        return valor

# Ejemplos de uso
try:
    edad = Validador.validar_entero(150, "edad", minimo=0, maximo=120)
except ValueError as e:
    print(f"❌ {e}")

try:
    nombre = Validador.validar_texto("Ab", "nombre", min_largo=3)
except ValueError as e:
    print(f"❌ {e}")

try:
    email = Validador.validar_email("correo_invalido")
except ValueError as e:
    print(f"❌ {e}")

try:
    color = Validador.validar_opciones("verde", ["rojo", "azul"], "color")
except ValueError as e:
    print(f"❌ {e}")
```

---

(buenas-practicas-excepciones)=
##  Buenas Prácticas

### Reglas de Oro

::::{grid} 1 1 2 2

:::{grid-item-card} 1️⃣ Específico, no genérico
```python
# ❌ MAL
try:
    codigo()
except:
    pass

# ✅ BIEN
try:
    codigo()
except ValueError:
    manejar_error()
```
:::

:::{grid-item-card} 2️⃣ No silencies errores
```python
# ❌ MAL
except Exception:
    pass  # Oculta todo

# ✅ BIEN
except Exception as e:
    logging.error(f"Error: {e}")
    raise
```
:::

:::{grid-item-card} 3️⃣ Captura lo más específico primero
```python
# ✅ BIEN: del más específico al más general
try:
    codigo()
except FileNotFoundError:
    ...
except OSError:
    ...
except Exception:
    ...
```
:::

:::{grid-item-card} 4️⃣ Usa context managers
```python
# ✅ BIEN
with open("archivo.txt") as f:
    contenido = f.read()
# Se cierra automáticamente
```
:::

:::{grid-item-card} 5️⃣ Documenta excepciones
```python
def dividir(a, b):
    """Divide a entre b.
    
    Raises:
        ZeroDivisionError: Si b es 0
        TypeError: Si a o b no son números
    """
    return a / b
```
:::

:::{grid-item-card} 6️⃣ Valida temprano
```python
# ✅ BIEN: Valida al inicio
def procesar(datos):
    if not datos:
        raise ValueError("datos no puede estar vacío")
    # ... resto del código
```
:::

::::

---

## Resumen del Capítulo

::::{grid} 1

:::{grid-item-card} Conceptos Clave
- Las excepciones son eventos que interrumpen el flujo normal
- `try-except` permite capturar y manejar errores
- `else` ejecuta si NO hay error, `finally` SIEMPRE
- `raise` permite lanzar tus propias excepciones
- Las excepciones personalizadas ayudan a organizar errores
- Los context managers (`with`) garantizan limpieza de recursos
:::

:::{grid-item-card} ✅ Checklist de Buenas Prácticas
- [ ] Capturo excepciones específicas, no genéricas
- [ ] No silencio errores con `pass`
- [ ] Uso `with` para archivos y recursos
- [ ] Valido datos de entrada
- [ ] Documento qué excepciones puede lanzar mi código
- [ ] Uso excepciones personalizadas para mi dominio
- [ ] Registro errores con logging
- [ ] Limpio recursos en `finally` o `with`
:::

::::

---

## 💪 Ejercicios

### Ejercicio 1: Calculadora Segura
Crea una calculadora que maneje todos los errores posibles.

### Ejercicio 2: Validador de Formulario
Implementa un validador completo para un formulario de registro.

---

##  Referencias

- [Documentación oficial de Excepciones](https://docs.python.org/3/tutorial/errors.html)
- [PEP 8 - Guía de estilo](https://pep8.org/)
- [Built-in Exceptions](https://docs.python.org/3/library/exceptions.html)

---

(glosario-excepciones)=
## Glosario de Terminología 📖

Este glosario contiene los términos clave sobre manejo de excepciones y programación defensiva que se trataron en este capítulo.

:::{admonition} 💡 Cómo usar este glosario
:class: tip

- **Consultalo cuando necesites refrescar un concepto**
- Los términos pueden referenciarse en el texto usando la sintaxis especial
- Incluye terminología de manejo robusto de errores
- **Repasá los términos clave antes de los ejercicios**
:::

```{glossary}
Excepción
: Evento que interrumpe el flujo normal de ejecución cuando ocurre un error. Python crea un objeto de excepción con información del error. Si no se maneja, el programa termina. También conocida como **exception** en inglés.

Error
: Problema que impide la ejecución correcta del programa. Puede ser de {term}`sintaxis` (código mal escrito) o de {term}`tiempo de ejecución` (runtime). Las excepciones manejan errores de runtime.

Error de sintaxis
: Error en la escritura del código que Python detecta antes de ejecutar. Ejemplo: `if x = 5:` (debería ser `==`). Python no ejecuta código con errores de sintaxis.

Error de tiempo de ejecución
: Error que ocurre durante la ejecución del programa, no al escribirlo. Ejemplo: dividir por cero, archivo no encontrado. Estos generan {term}`excepciones <excepción>`.

try
: Bloque donde se coloca código que podría generar una {term}`excepción`. Python intenta ejecutarlo y si hay error, salta al bloque {term}`except` correspondiente.

except
: Bloque que captura y maneja  {term}`excepciones<excepción>`. Se ejecuta solo si ocurre el tipo de error especificado en el `try`. Sintaxis: `except TipoError:`.

try-except
: Estructura para manejar excepciones. `try` contiene código riesgoso, `except` maneja el error. Evita que el programa termine abruptamente. Permite recuperación elegante de errores.

else (en try)
: Bloque opcional que se ejecuta solo si NO hubo ninguna **excepción** en `try`. Útil para código que solo debe ejecutarse tras éxito. Diferente del `else` en bucles.

finally
: Bloque que SIEMPRE se ejecuta después de `try-except`, haya o no excepción. Usado para limpieza: cerrar archivos, liberar recursos, desconectar BD. Garantiza ejecución.

raise
: Palabra clave para lanzar (generar) una {term}`excepción` manualmente. Sintaxis: `raise TipoError("mensaje")`. Útil para validación y reportar condiciones de error en funciones propias.

Traceback
: Informe detallado del error que muestra: tipo de excepción, mensaje, y la cadena de llamadas que llevó al error. Lee desde abajo hacia arriba. También conocido como **stack trace**.

ValueError
: Excepción lanzada cuando una función recibe argumento del tipo correcto pero valor inapropiado. Ejemplo: `int("abc")`, `math.sqrt(-1)`. Valor fuera del dominio válido.

TypeError
: Excepción lanzada cuando se usa un tipo de dato incorrecto. Ejemplo: `"texto" + 5`, `len(5)`. Operación no soportada para ese tipo.

ZeroDivisionError
: Excepción lanzada al dividir o hacer módulo por cero. Ejemplo: `5 / 0`. Error matemático común que debe manejarse en calculadoras.

FileNotFoundError
: Excepción lanzada cuando se intenta abrir archivo que no existe. Común con `open()`. Debe manejarse o verificar existencia con `os.path.exists()` antes.

IndexError
: Excepción lanzada al acceder a índice que no existe en lista/tupla. Ejemplo: `lista[10]` cuando lista tiene 5 elementos. Índice fuera de rango.

KeyError
: Excepción lanzada al acceder a clave que no existe en diccionario. Ejemplo: `dict["clave_inexistente"]`. Usar `dict.get()` o `in` para evitarla.

AttributeError
: Excepción lanzada al acceder a atributo/método inexistente de un objeto. Ejemplo: `"texto".append()` (strings no tienen append). Atributo no existe.

ImportError
: Excepción lanzada cuando falla un import. `ImportError` es genérico, `ModuleNotFoundError` (más específico) cuando módulo no existe. Común con bibliotecas no instaladas.

NameError
: Excepción lanzada al usar variable no definida. Ejemplo: usar `resultado` antes de asignarle valor. Variable no existe en el {term}`scope` actual.

SyntaxError
: **Error de sintaxis**. `SyntaxError` por código mal escrito. Python no ejecuta código con estos errores.

IndentationError
: Es un tipo de {term}`SyntaxError` provocado por indentación incorrecta.

Excepción personalizada
: Clase de excepción creada por el programador, heredando de `Exception`. Permite errores específicos del dominio. Por ejemplo: `class EdadInvalidaError(ValueError):`.

assert
: Declaración que verifica una condición debe ser verdadera. Si es falsa, lanza `AssertionError`. Sintaxis: `assert condicion, "mensaje"`. Usado para debugging y validación.

AssertionError
: Excepción lanzada cuando un {term}`assert` falla (condición es falsa). Indica que una suposición del código no se cumplió. Útil para detectar bugs.

Manejo de excepciones
: Técnica de capturar y gestionar errores con **try-except** en lugar de dejar que terminen el programa. Permite recuperación elegante y mensajes útiles.

Atajar excepción
: Detectar y manejar una {term}`excepción` con un bloque {term}`except`. "atajar" = "catch" en inglés. Previene terminación abrupta del programa.

Lanzar excepción
: Generar una **excepción** con **raise**. "Lanzar" = "throw" (otros lenguajes) o "raise" (Python). Señala condición de error.

Jerarquía de excepciones
: Estructura de clases de excepciones en Python. Todas heredan de `BaseException`. `Exception` es padre de mayoría. Capturar padre captura también hijos.

BaseException
: Clase raíz de todas las excepciones en Python. `Exception` hereda de ella. Capturarla captura TODAS las excepciones (mala práctica, incluye `KeyboardInterrupt`).

Exception (clase)
: Clase base de todas las excepciones de usuario (no del sistema). Hereda de `BaseException`. Tus excepciones personalizadas deben heredar de esta o sus subclases.

Bare except
: Usar `except:` sin especificar tipo de excepción. **Mala práctica** porque captura TODO (incluso Ctrl+C). Siempre especificar qué capturar.

Context manager
: Objeto que gestiona recursos automáticamente con {term}`with`. Garantiza limpieza (cierre) incluso si hay error. Implementa métodos `__enter__` y `__exit__`.

with
: Palabra clave para usar {term}`context manager`. Asegura que el recurso se cierre/limpie correctamente, haya o no excepción.

Programación defensiva
: Estilo de programación que anticipa y previene errores. Incluye validación de entrada, manejo de excepciones, aserciones. Hace código más robusto.

Validación de entrada
: Verificar que datos de usuario/externa sean correctos antes de procesarlos. Previene errores y vulnerabilidades. Usar {term}`excepciones <excepción>` o condicionales.

LBYL
: "Look Before You Leap" (Mira antes de saltar). Estilo que verifica condiciones ANTES de actuar. Usa `if` para prevenir errores. Opuesto a {term}`EAFP`.

EAFP
: "Easier to Ask Forgiveness than Permission" (Más fácil pedir perdón que permiso). Estilo Python: intenta la acción, maneja error si ocurre. Usa {term}`try-except`.

Logging
: Registrar eventos y errores en archivos/consola para debugging y monitoreo. Usa módulo `logging`. Mejor que `print()` para producción. Niveles: DEBUG, INFO, WARNING, ERROR, CRITICAL.

Debugging
: Proceso de encontrar y corregir errores (bugs) en código. Técnicas: print(), debugger, logging, dividir y conquistar. También conocido como **depuración**.

Stack
: Estructura que registra funciones activas. Al llamar función, se apila; al retornar, se desapila. El {term}`traceback` muestra esta pila cuando hay error.

Reraise
: Relanzar una excepción es, su captura, hacer algo (ej: logging), y lanzarla de nuevo con `raise` (sin argumentos) para que suba por la pila. Permite manejo multinivel.
```

