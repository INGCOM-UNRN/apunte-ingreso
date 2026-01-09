---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
#header: 'Manejo de Excepciones en Python'
footer: 'Crear programas robustos y confiables'

---

<!-- _paginate: false -->
<!-- _header: '' -->

# Manejo de Excepciones en Python

**Aprende a manejar errores como un profesional**

<!--
¡Hola a todos! Hoy vamos a hablar de un tema crucial para cualquier programador que quiera salir del jardín de infantes: el Manejo de Excepciones. Hasta ahora, cuando algo salía mal, nuestro programa explotaba y nos mostraba un mensaje rojo horrible. Hoy vamos a aprender a atajar esos errores, manejarlos con elegancia y hacer que nuestros programas sean a prueba de balas.
-->
---

## ¿Qué vas a aprender?

* Qué son las **excepciones** y por qué ocurren
* Usar **`try-except`** para capturar errores
* Cláusulas **`else`** y **`finally`**
* **Lanzar** tus propias excepciones
* **Crear excepciones personalizadas**
* **Buenas prácticas** para código robusto

<!--
¿Qué tenemos en el menú? Vamos a entender qué son realmente las excepciones (spoiler: no son el fin del mundo). Vamos a aprender la estructura `try-except`, que es nuestro escudo protector. También vamos a ver cláusulas avanzadas como `else` y `finally`. Y para los que quieran ir más allá, vamos a ver cómo crear nuestros propios errores y las mejores prácticas para no meter la pata.
-->
---

## Los Errores son Parte del Juego

Imagina construir un puente 🌉. ¿Qué pasa si viene:
- Un terremoto?
- Una inundación?
- Mucho tráfico?

**Un buen ingeniero planifica qué hacer cuando las cosas salen mal**

En programación es igual. Tu código puede enfrentar:
- 🔢 Usuarios que ingresan datos incorrectos
- 📁 Archivos que no existen
- 🌐 Conexiones de red que fallan
- 💾 Memoria que se agota

<!--
Piensen en esto como ingeniería civil. Cuando diseñás un puente, no asumís que siempre va a haber sol y viento calmo. Planificás para terremotos, huracanes y sobrecarga. En software es igual. El usuario va a meter el dedo donde no debe, el archivo que buscás no va a estar, internet se va a cortar. Si tu programa no está listo para eso, es un programa frágil.
-->
---

## Sin vs Con Manejo de Excepciones

**Sin manejo:**
```python
edad = int(input("Edad: "))
# Usuario escribe "abc"
# ¡Boom! 💀 Programa termina
```

**Con manejo:**
```python
try:
    edad = int(input("Edad: "))
except ValueError:
    print("❌ Eso no es un número")
    edad = 0
# ✅ Programa sigue funcionando
```

<!--
Miren este ejemplo clásico. Le pedís la edad al usuario. Esperás un número. El usuario escribe 'veinte'. ¡Pum! `ValueError` y el programa se cierra. Con manejo de excepciones, podemos detectar ese error, decirle amablemente 'Che, poné un número' y seguir adelante o poner un valor por defecto. Esa es la diferencia entre un script de juguete y una aplicación profesional.
-->
---

<!-- _class: lead -->

# ¿Qué es una Excepción?

<!--
Entonces, ¿qué es una excepción? Es una señal, una alarma. No es un error de sintaxis (eso es escribir mal el código). Es un error en tiempo de ejecución. El código está bien escrito, pero algo en el entorno o en los datos hizo que la operación sea imposible. Dividir por cero es el ejemplo de libro.
-->
---

## Excepción = Alarma de Seguridad

Imagina que tu casa tiene una alarma:

1. **Try** = Intentar hacer algo (entrar a casa)
2. **Excepción** = Alarma que se dispara si algo sale mal
3. **Except** = Protocolo de qué hacer si suena la alarma

```python
def dividir_pizza(porciones, personas):
    return porciones / personas

# ¡Ups! No hay personas
resultado = dividir_pizza(8, 0)
# ZeroDivisionError: division by zero
```

<!--
Acá se ve clara la diferencia. El error de sintaxis es como escribir mal una palabra; Python no te entiende. La excepción es como pedirle a alguien que vuele; te entiende, pero no puede hacerlo. Python levanta la mano y dice '¡Excepción!', y ahí es donde entramos nosotros para manejarla.
-->
---

## Excepción vs Error de Sintaxis

**Error de Sintaxis:**
```python
# ❌ Python ni siquiera puede leer esto
if x = 5:  # SyntaxError
    print(x)
```
Python dice: **"No entiendo lo que escribiste"**

**Excepción:**
```python
# ✓ Python entiende el código...
x = 5
y = 0
resultado = x / y  # ZeroDivisionError
# ...pero la operación es imposible
```
Python dice: **"Entiendo, pero no puedo hacer eso"**

<!--
Cuando el programa explota, Python nos tira un 'Traceback'. No se asusten, es un mapa. Les dice exactamente dónde ocurrió el problema y qué camino tomó el código para llegar ahí. Leer tracebacks es una habilidad fundamental. La última línea suele tener la posta: qué error fue y por qué.
-->
---

## El Traceback (Rastreo)

Cuando ocurre una excepción, Python nos da pistas:

```python
def hacer_cafe():
    return moler_granos()

def moler_granos():
    return usar_molino(0)

def usar_molino(velocidad):
    return 100 / velocidad  # ZeroDivisionError aquí

hacer_cafe()
```

**Traceback:**
```
Traceback (most recent call last):
  File "script.py", line 9, in <module>
    hacer_cafe()
  File "script.py", line 2, in hacer_cafe
    return moler_granos()
  File "script.py", line 5, in moler_granos
    return usar_molino(0)
  File "script.py", line 8, in usar_molino
    return 100 / velocidad
ZeroDivisionError: division by zero
```

<!--
Hay un zoológico de excepciones, pero estas son las que van a ver el 90% del tiempo. `ValueError` para datos que no tienen sentido. `TypeError` para mezclar peras con manzanas. `ZeroDivisionError`... bueno, se explica solo. `FileNotFoundError` para cuando el archivo no está. Conocerlas es el primer paso para atraparlas.
-->
---

<!-- _class: lead -->

# Tipos Comunes de Excepciones

<!--
Vamos a ver ejemplos concretos. `ValueError` aparece mucho cuando convertimos tipos. Si trato de convertir 'hola' a entero, explota. Si capturo la excepción, puedo avisarle al usuario y el programa no se rompe.
-->
---

## Excepciones Más Frecuentes

| Excepción | Cuándo Ocurre | Ejemplo |
|
---
---
-----|
---
---
---
---
---|
---
---
---|
| `ValueError` | Valor inválido | `int("abc")` |
| `TypeError` | Tipo incorrecto | `"5" + 3` |
| `ZeroDivisionError` | División por cero | `10 / 0` |
| `FileNotFoundError` | Archivo no existe | `open("x.txt")` |
| `KeyError` | Clave no existe | `dict["key"]` |
| `IndexError` | Índice fuera de rango | `lista[100]` |

<!--
`TypeError` es cuando intentás hacer algo con un tipo de dato que no corresponde. Sumar texto y número, o intentar llamar a un número como si fuera una función. Python es estricto con los tipos, y eso es bueno.
-->
---

## `ValueError` - Valor Incorrecto

```python
# Convertir string a número
try:
    edad = int("veinticinco")  # ValueError
except ValueError:
    print("❌ No se puede convertir a número")

# Otro ejemplo
try:
    numero = int("123abc")  # ValueError
except ValueError:
    print("❌ Contiene caracteres no numéricos")
```

<!--
`ZeroDivisionError`. Matemáticamente imposible. Si están calculando promedios o porcentajes, siempre hay riesgo de que el denominador sea cero. Atrápenlo antes de que rompa todo.
-->
---

## `TypeError` - Tipo Incorrecto

```python
# Sumar tipos incompatibles
try:
    resultado = "5" + 3  # TypeError
except TypeError:
    print("❌ No se puede sumar string con int")

# Llamar no-función
try:
    x = 5
    x()  # TypeError: 'int' object is not callable
except TypeError:
    print("❌ No es una función")
```

<!--
Archivos. El usuario te dice que el archivo estátá ahí, pero lo borró o le cambió el nombre. `FileNotFoundError` es tu amigo. En lugar de crashear, podés crear el archivo o pedirle al usuario que verifique la ruta.
-->
---

## `ZeroDivisionError` - División por Cero

```python
def dividir_seguro(a, b):
    """División con manejo de error."""
    try:
        resultado = a / b
        return resultado
    except ZeroDivisionError:
        print("❌ No se puede dividir por cero")
        return None

print(dividir_seguro(10, 2))  # 5.0
print(dividir_seguro(10, 0))  # None
```

<!--
Diccionarios. Buscás una clave que no existe: `KeyError`. Es súper común. Podés usar `try-except` o el método `.get()` que es más seguro. Ambas son válidas, pero el `try-except` es más explícito sobre el error.
-->
---

## `FileNotFoundError` - Archivo No Existe

```python
try:
    with open("archivo_inexistente.txt", "r") as archivo:
        contenido = archivo.read()
except FileNotFoundError:
    print("❌ El archivo no existe")
    print("Creando archivo...")
    with open("archivo_inexistente.txt", "w") as archivo:
        archivo.write("Contenido inicial\n")
```

<!--
Listas. Querés el elemento 10 de una lista de 3. `IndexError`. Siempre validen los índices o manejen esta excepción. Es típico en bucles o cuando procesamos datos que vienen de afuera.
-->
---

## `KeyError` - Clave No Existe

```python
estudiante = {
    "nombre": "Ana",
    "edad": 20
}

try:
    carrera = estudiante["carrera"]  # KeyError
except KeyError:
    print("❌ La clave 'carrera' no existe")
    carrera = "No especificada"

# Mejor: usar get()
carrera = estudiante.get("carrera", "No especificada")
```

<!--
Ahora sí, la herramienta principal: `try-except`. Es como un seguro. En el bloque `try` ponés el código peligroso, el que puede fallar. En el `except` ponés el plan de contingencia. Si todo va bien, el `except` se ignora. Si algo falla, saltamos directo al `except`.
-->
---

## `IndexError` - Índice Fuera de Rango

```python
lista = [10, 20, 30]

try:
    elemento = lista[10]  # IndexError
except IndexError:
    print(f"❌ Índice fuera de rango")
    print(f"La lista tiene {len(lista)} elementos")

# Mejor: verificar longitud
indice = 10
if indice < len(lista):
    elemento = lista[indice]
else:
    print("❌ Índice inválido")
```

<!--
Miren qué lindo queda. Intento convertir y dividir. Si falla la conversión (`ValueError`), le digo que ponga un número. Si falla la división (`ZeroDivisionError`), le digo que no ponga cero. Cubro todas las bases.
-->
---

<!-- _class: lead -->

# Try-Except Básico

<!--
El orden importa. Python va probando los `except` de arriba a abajo. El primero que coincida con el error gana. Si tenés un error genérico y uno específico, poné el específico primero.
-->
---

## Sintaxis Básica

```python
try:
    # Código que puede fallar
    resultado = operacion_peligrosa()
except TipoDeError:
    # Qué hacer si ocurre el error
    print("❌ Algo salió mal")
```

**Flujo:**
1. Python intenta ejecutar el código en `try`
2. Si ocurre el error especificado, ejecuta `except`
3. Si NO ocurre error, salta el `except`
4. Continúa con el resto del programa

<!--
A veces querés tratar varios errores igual. 'Si falla, avisá'. Podés agrupar excepciones en una tupla `(Error1, Error2)`. También podés capturar la instancia del error con `as error` para imprimir el mensaje técnico o loguearlo.
-->
---

## Ejemplo Simple

```python
try:
    numero = int(input("Ingrese un número: "))
    resultado = 100 / numero
    print(f"Resultado: {resultado}")
except ValueError:
    print("❌ Debe ingresar un número válido")
except ZeroDivisionError:
    print("❌ No se puede dividir por cero")
```

**Si el usuario ingresa "abc"** → ValueError
**Si el usuario ingresa "0"** → ZeroDivisionError
**Si el usuario ingresa "5"** → ✅ Todo bien

<!--
Capturar el objeto de excepción es muy útil para debugging. Te da detalles del error que podés guardar en un log o mostrar (con cuidado) al usuario. `e` o `error` es la convención para nombrarlo.
-->
---

## Múltiples Except

```python
try:
    archivo = open("datos.txt", "r")
    numero = int(archivo.read())
    resultado = 100 / numero
except FileNotFoundError:
    print("❌ Archivo no existe")
except ValueError:
    print("❌ El archivo no contiene un número")
except ZeroDivisionError:
    print("❌ El número es cero")
```

**Python evalúa los `except` en orden y ejecuta el primero que coincida**

<!--
El `try-except` tiene dos hermanos menos conocidos pero muy útiles: `else` y `finally`. `else` corre si NO hubo errores en el `try`. `finally` corre SIEMPRE, haya error o no. Es el lugar perfecto para limpiar el desastre.
-->
---

## Capturar Múltiples en Uno

```python
# Manejar varios errores de la misma forma
try:
    resultado = operacion_compleja()
except (ValueError, TypeError, ZeroDivisionError):
    print("❌ Error en el cálculo")

# Con la excepción
try:
    resultado = operacion_compleja()
except (ValueError, TypeError) as error:
    print(f"❌ Error: {error}")
```

<!--
Este es el flujo completo. Intento abrir (try). Si falla, aviso (except). Si funciona, digo cuántos caracteres leí (else). Y pase lo que pase, cierro el archivo (finally). Es un patrón muy robusto.
-->
---

## Capturar el Objeto Excepción

```python
try:
    numero = int(input("Número: "))
except ValueError as error:
    print(f"📋 Mensaje: {error}")
    print(f"🏷️ Tipo: {type(error)}")
    print(f"📦 Args: {error.args}")
```

**Si el usuario escribe "abc":**
```
📋 Mensaje: invalid literal for int() with base 10: 'abc'
🏷️ Tipo: <class 'ValueError'>
📦 Args: ("invalid literal for int() with base 10: 'abc'",)
```

<!--
Acá vemos un ejemplo más realista. Procesar un archivo. Manejamos que no exista, que no tengamos permisos. Si todo sale bien, devolvemos las líneas. Y siempre, siempre, cerramos el archivo en el `finally`.
-->
---

<!-- _class: lead -->

# Try-Except-Else-Finally

<!--
Para resumir: `try` es obligatorio. `except` maneja el problema. `else` es para la lógica que depende del éxito del `try` (separar lo riesgoso de lo seguro). `finally` es para limpieza garantizada (cerrar conexiones, borrar temporales).
-->
---

## Las 4 Cláusulas

| Cláusula | Cuándo se Ejecuta | Para Qué Sirve |
|
---
---
----|
---
---
---
---
---
----|
---
---
---
---
----|
| `try` | Siempre primero | Código que puede fallar |
| `except` | Solo si hay error | Manejar el error |
| `else` | Solo si NO hay error | Código de éxito |
| `finally` | SIEMPRE | Limpieza (cerrar archivos) |

<!--
Hasta ahora solo atajamos penales. Pero a veces queremos patearlos nosotros. `raise` nos permite generar una excepción intencionalmente. Es útil para validar reglas de negocio. 'Si la edad es negativa, esto es un error grave, ¡lanzá una excepción!'.
-->
---

## Flujo Completo

```python
try:
    # 1. Intenta esto
    archivo = open("datos.txt", "r")
    contenido = archivo.read()
except FileNotFoundError:
    # 2. Si no existe el archivo
    print("❌ Archivo no existe")
else:
    # 3. Si todo salió bien
    print(f"✅ Leído: {len(contenido)} caracteres")
finally:
    # 4. SIEMPRE ejecuta esto
    if 'archivo' in locals():
        archivo.close()
        print("🔒 Archivo cerrado")
```

<!--
Validar datos es el uso número 1 de `raise`. Si la función espera un nombre y recibe vacío, no tiene sentido seguir. Lanzamos `ValueError` con un mensaje claro. Quien llame a la función tendrá que manejar ese error.
-->
---

## Ejemplo: Procesar Archivo

```python
def procesar_archivo(nombre):
    archivo = None
    
    try:
        print("📂 Abriendo archivo...")
        archivo = open(nombre, 'r')
        
        print("📄 Leyendo contenido...")
        contenido = archivo.read()
        
        print("⚙️ Procesando...")
        lineas = contenido.split('\n')
        
    except FileNotFoundError:
        print("❌ Archivo no existe")
        return None
    
    except PermissionError:
        print("❌ Sin permisos")
        return None
    
    else:
        print(f"✅ Procesado: {len(lineas)} líneas")
        return lineas
    
    finally:
        if archivo:
            archivo.close()
            print("🔒 Archivo cerrado")

lineas = procesar_archivo("datos.txt")
```

<!--
A veces capturamos un error, hacemos algo (como loguearlo) y queremos que el error siga subiendo para que lo maneje otro nivel superior. Para eso usamos `raise` solito, sin argumentos. Re-lanza la excepción activa.
-->
---

## ¿Cuándo usar cada cláusula?

**`try`:** Siempre (necesario)

**`except`:** Para manejar errores específicos

**`else`:** Código que solo debe ejecutarse si no hubo error
```python
else:
    print("✅ Todo salió bien")
```

**`finally`:** Limpieza que SIEMPRE debe ocurrir
```python
finally:
    cerrar_conexion()
    liberar_recursos()
```

<!--
Python nos deja crear nuestros propios tipos de error. Es tan simple como crear una clase que herede de `Exception`. Esto hace que tu código sea mucho más expresivo. `NombreVacioError` se entiende mucho más que un `ValueError` genérico.
-->
---

<!-- _class: lead -->

# Lanzar Excepciones

<!--
Podés hacer excepciones tan complejas como quieras. Agregarles atributos, métodos... Imaginense un `ErrorDePago` que guarde el monto y el usuario que falló. Súper útil para el equipo de soporte.
-->
---

## `raise` - Lanzar Excepciones

A veces TÚ querés generar un error:

```python
def dividir(a, b):
    """Divide dos números."""
    if b == 0:
        raise ValueError("El divisor no puede ser cero")
    
    if not isinstance(a, (int, float)):
        raise TypeError("Los argumentos deben ser números")
    
    return a / b

# Usar
try:
    resultado = dividir(10, 0)
except ValueError as e:
    print(f"❌ {e}")
```

<!--
En sistemas grandes, organizamos las excepciones en jerarquías. `ErrorDeBaseDatos` puede ser el padre de `ErrorDeConexion` y `ErrorDeConsulta`. Así podés capturar todos los de base de datos juntos, o ser específico si querés.
-->
---

## Validar Entradas

```python
def crear_usuario(nombre, edad):
    """Crea un usuario validando datos."""
    if not nombre:
        raise ValueError("El nombre no puede estar vacío")
    
    if not isinstance(edad, int):
        raise TypeError("La edad debe ser un número entero")
    
    if edad < 0 or edad > 120:
        raise ValueError(f"Edad inválida: {edad}")
    
    return {"nombre": nombre, "edad": edad}

# Usar
try:
    usuario = crear_usuario("", 25)
except ValueError as e:
    print(f"❌ Error de validación: {e}")
```

<!--
Volvemos a los archivos. Abrir y cerrar a mano es propenso a errores. Si hay una excepción antes del `close()`, el archivo queda abierto. Eso es una fuga de recursos.
-->
---

## Re-Lanzar Excepciones

```python
def procesar_datos(datos):
    try:
        # Procesar
        resultado = operacion_compleja(datos)
    except ValueError as e:
        print("⚠️ Advertencia: error de valor")
        raise  # Re-lanza la misma excepción
    
    return resultado

try:
    procesar_datos(datos_invalidos)
except ValueError:
    print("❌ Error en nivel superior")
```

**`raise` sin argumentos re-lanza la excepción actual**

<!--
La solución mágica: Context Managers (`with`). Hacen lo mismo que el `try-finally` pero en una línea. Abren el recurso y te garantizan que se va a cerrar al salir del bloque, pase lo que pase. Úsenlo siempre.
-->
---

<!-- _class: lead -->

# Excepciones Personalizadas

<!--
Miren la diferencia. `leer_archivo_seguro` usa `with` y `try-except`. Es código profesional. Maneja codificación, permisos, existencia. Así se escribe software de verdad.
-->
---

## Crear Tus Propias Excepciones

```python
class EdadInvalidaError(Exception):
    """Excepción para edad inválida."""
    pass

class NombreVacioError(Exception):
    """Excepción para nombre vacío."""
    pass

def crear_persona(nombre, edad):
    if not nombre:
        raise NombreVacioError("El nombre no puede estar vacío")
    
    if edad < 0 or edad > 120:
        raise EdadInvalidaError(f"Edad inválida: {edad}")
    
    return {"nombre": nombre, "edad": edad}

try:
    persona = crear_persona("", 25)
except NombreVacioError as e:
    print(f"❌ Error de nombre: {e}")
except EdadInvalidaError as e:
    print(f"❌ Error de edad: {e}")
```

<!--
Para escribir es lo mismo. El `with` asegura que los datos se guarden y el archivo se cierre. Capturamos errores de permisos o de sistema operativo (disco lleno). Retornamos `True` o `False` para indicar éxito.
-->
---

## Excepciones con Información Extra

```python
class ErrorDePago(Exception):
    """Error en procesamiento de pago."""
    
    def __init__(self, monto, mensaje):
        self.monto = monto
        self.mensaje = mensaje
        super().__init__(f"Error al procesar ${monto}: {mensaje}")

def procesar_pago(monto):
    if monto <= 0:
        raise ErrorDePago(monto, "El monto debe ser positivo")
    
    if monto > 10000:
        raise ErrorDePago(monto, "Monto excede el límite")

try:
    procesar_pago(15000)
except ErrorDePago as e:
    print(f"❌ {e}")
    print(f"💰 Monto problemático: ${e.monto}")
```

<!--
Buenas prácticas. Regla 1: Sean específicos. `except Exception:` o `except:` (bare except) es una mala práctica conocida como 'Pokémon Exception Handling' (atraparlos a todos). Oculta bugs reales. Solo capturen lo que saben manejar.
-->
---

## Jerarquía de Excepciones

```python
class AppError(Exception):
    """Error base de la aplicación."""
    pass

class ErrorDeBaseDatos(AppError):
    """Errores de base de datos."""
    pass

class ErrorDeConexion(ErrorDeBaseDatos):
    """Error de conexión a BD."""
    pass

class ErrorDeConsulta(ErrorDeBaseDatos):
    """Error en consulta SQL."""
    pass

# Capturar por categorías
try:
    operacion_bd()
except ErrorDeBaseDatos:
    # Captura TODOS los errores de BD
    print("❌ Error en la base de datos")
except AppError:
    # Captura cualquier error de la app
    print("❌ Error general")
```

<!--
Regla 2: No silencien errores. Un `except: pass` es lo peor que pueden hacer. El error ocurre y el programa sigue como si nada, probablemente con datos corruptos. Como mínimo, logueen el error.
-->
---

<!-- _class: lead -->

# Context Managers (with)

<!--
Regla 3: El bloque `try` debe ser chiquito. Si ponen 100 líneas en el `try`, y salta un `ValueError`, no saben cuál de las 20 líneas posibles lo causó. Solo envuelvan la parte peligrosa.
-->
---

## El Problema: Fugas de Recursos

```python
# ❌ PELIGROSO: Si hay error, el archivo queda abierto
archivo = open("datos.txt", "r")
contenido = archivo.read()
procesar(contenido)  # ¿Y si esto falla?
archivo.close()  # ¡Nunca llega aquí!
```

**Problemas:**
- 💾 Fuga de memoria
- 🔒 Archivo bloqueado
- ⚠️ Límite de archivos abiertos
- 📉 Pérdida de datos

<!--
Regla 4: Los mensajes de error son para humanos. 'Error 504' no ayuda. 'El archivo tiene un formato inválido' sí. Ayuden a su usuario (y a ustedes mismos cuando tengan que debuggear).
-->
---

## Solución: Context Manager (with)

```python
# ✅ MEJOR: Automático y limpio
with open("datos.txt", "r") as archivo:
    contenido = archivo.read()
    procesar(contenido)
# ✅ El archivo se cierra automáticamente
```

**Ventajas:**
- Se cierra incluso si hay error
- Código más limpio
- No te olvidás de cerrar

<!--
Regla 5: Limpien. Si abrieron algo, ciérrenlo. Si crearon un temporal, bórrenlo. El `finally` o el `with` son obligatorios para recursos del sistema.
-->
---

## Lectura Segura de Archivos

```python
def leer_archivo_seguro(nombre):
    """Lee un archivo con manejo completo."""
    try:
        with open(nombre, 'r', encoding='utf-8') as archivo:
            contenido = archivo.read()
            lineas = contenido.split('\n')
            
            print(f"✅ Leído: {len(lineas)} líneas")
            return lineas
            
    except FileNotFoundError:
        print(f"❌ '{nombre}' no existe")
        return None
        
    except PermissionError:
        print(f"❌ Sin permisos para '{nombre}'")
        return None
        
    except UnicodeDecodeError:
        print(f"❌ Problema de codificación")
        return None

lineas = leer_archivo_seguro("datos.txt")
```

<!--
Regla 6: No capturen `Exception` a menos que sea en el nivel más alto del programa (para loguear un crash y salir). Capturar `Exception` puede ocultar errores de sintaxis o `KeyboardInterrupt` (Ctrl+C).
-->
---

## Escritura Segura

```python
def guardar_datos(nombre, datos):
    """Guarda datos de forma segura."""
    try:
        with open(nombre, 'w', encoding='utf-8') as archivo:
            if isinstance(datos, list):
                archivo.write('\n'.join(map(str, datos)))
            else:
                archivo.write(str(datos))
        
        print(f"✅ Guardado en '{nombre}'")
        return True
        
    except PermissionError:
        print(f"❌ Sin permisos para escribir")
        return False
        
    except OSError as e:
        print(f"❌ Error de sistema: {e}")
        return False

datos = ["línea 1", "línea 2", "línea 3"]
guardar_datos("salida.txt", datos)
```

<!--
Regla 7: Documenten qué excepciones lanza su función. Es parte de la interfaz. El que usa tu función necesita saber qué errores esperar para poder manejarlos.
-->
---

<!-- _class: lead -->

# Buenas Prácticas

<!--
Resumiendo: Las excepciones son amigas. Nos permiten manejar lo inesperado. `try-except` es la estructura base. `finally` asegura limpieza.
-->
---

## 1. Específico, No Genérico

```python
# ❌ MAL: Captura TODOS los errores
try:
    codigo()
except:
    pass  # ¿Qué error ocurrió?

# ✅ BIEN: Captura errores específicos
try:
    codigo()
except ValueError:
    manejar_valor_invalido()
except FileNotFoundError:
    manejar_archivo_faltante()
```

<!--
`raise` nos da control para hacer cumplir nuestras reglas. `with` es la forma moderna y segura de manejar recursos.
-->
---

## 2. No Ocultar Errores

```python
# ❌ MAL: Silencia el error
try:
    codigo()
except Exception:
    pass  # El error desaparece

# ✅ BIEN: Al menos registra el error
try:
    codigo()
except Exception as e:
    print(f"⚠️ Error: {e}")
    # O usar logging
    logging.error(f"Error: {e}")
```

<!--
Tengan esta lista a mano. Son los sospechosos de siempre. Conocerlos les va a ahorrar mucho tiempo de búsqueda en Google.
-->
---

## 3. Mantener Try Pequeño

```python
# ❌ MAL: Try muy grande
try:
    datos = cargar_datos()
    validar_datos(datos)
    procesar_datos(datos)
    guardar_resultados(datos)
except Exception:
    print("Error en algún lado...")

# ✅ BIEN: Try específico
datos = cargar_datos()
validar_datos(datos)

try:
    procesar_datos(datos)
except ValueError as e:
    print(f"Error en procesamiento: {e}")

guardar_resultados(datos)
```

<!--
Si se llevan algo de hoy: Sean específicos, no oculten basura bajo la alfombra (`pass`), y usen `with`. Con eso ya están por encima del promedio.
-->
---

## 4. Mensajes Descriptivos

```python
# ❌ MAL: Mensaje vago
except ValueError:
    print("Error")

# ✅ BIEN: Mensaje útil
except ValueError as e:
    print(f"❌ Error de validación: {e}")
    print("Sugerencia: Verifica los datos de entrada")
```

<!--
Este patrón de `operacion_segura` es una plantilla que pueden usar. Validación al principio (Guard Clauses), operación peligrosa en `try`, manejo de errores específicos, mensaje de éxito en `else` y limpieza en `finally`.
-->
---

## 5. Limpiar Recursos

```python
# ❌ MAL: Puede no cerrar
archivo = open("datos.txt")
try:
    procesar(archivo.read())
finally:
    archivo.close()

# ✅ MEJOR: Context manager
with open("datos.txt") as archivo:
    procesar(archivo.read())
# Se cierra automáticamente
```

<!--
Checklist final. Si pueden hacer todo esto, ya dominan el manejo de errores. Su código va a ser mucho más estable y profesional.
-->
---

## 6. No Capturar Exception

```python
# ❌ MAL: Captura demasiado
try:
    codigo()
except Exception:  # Captura TODOS los errores
    pass

# ✅ BIEN: Captura solo lo necesario
try:
    codigo()
except (ValueError, TypeError) as e:
    print(f"Error esperado: {e}")
```

<!--
¡Eso es todo! No le tengan miedo a los errores, ténganle miedo a no manejarlos. Practiquen romper su código y arreglarlo con excepciones. ¡Nos vemos la próxima!
-->
---

## 7. Documentar Excepciones

```python
def dividir(a, b):
    """Divide dos números.
    
    Args:
        a: Dividendo.
        b: Divisor.
    
    Returns:
        El resultado de a/b.
    
    Raises:
        ValueError: Si b es cero.
        TypeError: Si los argumentos no son números.
    """
    if b == 0:
        raise ValueError("Divisor no puede ser cero")
    
    if not isinstance(a, (int, float)):
        raise TypeError("Argumentos deben ser números")
    
    return a / b
```

<!--
NO MORE NOTES
-->
---

<!-- _class: lead -->

# Resumen

<!--
NO MORE NOTES
-->
---

## Conceptos Clave

**Excepciones:**
- Errores que ocurren durante la ejecución
- Se pueden **capturar** y **manejar**
- Hacen el código más **robusto**

**Try-Except:**
- `try`: Código que puede fallar
- `except`: Qué hacer si falla
- `else`: Si no falla
- `finally`: Siempre se ejecuta

<!--
NO MORE NOTES
-->
---

## Conceptos Clave (cont.)

**Lanzar excepciones:**
- `raise` para generar errores
- Validar entradas
- Crear excepciones personalizadas

**Context Managers:**
- `with` para manejo automático
- Garantiza limpieza de recursos
- Especialmente para archivos

<!--
NO MORE NOTES
-->
---

## Excepciones Comunes

| Excepción | Cuándo |
|
---
---
-----|
---
-----|
| `ValueError` | Valor incorrecto |
| `TypeError` | Tipo incorrecto |
| `ZeroDivisionError` | División por cero |
| `FileNotFoundError` | Archivo no existe |
| `KeyError` | Clave no existe |
| `IndexError` | Índice fuera de rango |

<!--
NO MORE NOTES
-->
---

## Buenas Prácticas Esenciales

1. ✅ Ser **específico** con los except
2. ✅ **No ocultar** errores (no usar `pass`)
3. ✅ Mantener bloques `try` **pequeños**
4. ✅ Usar **mensajes descriptivos**
5. ✅ **Limpiar recursos** (usar `with`)
6. ✅ **Documentar** excepciones que se lanzan
7. ✅ No capturar `Exception` genérico

<!--
NO MORE NOTES
-->
---

## Patrón Típico

```python
def operacion_segura(datos):
    """Procesa datos de forma segura."""
    # 1. Validar
    if not datos:
        raise ValueError("Datos vacíos")
    
    # 2. Procesar con manejo
    try:
        with open("archivo.txt", "w") as f:
            f.write(datos)
    except PermissionError:
        print("❌ Sin permisos")
        return False
    except OSError as e:
        print(f"❌ Error de sistema: {e}")
        return False
    else:
        print("✅ Procesado exitosamente")
        return True
    finally:
        print("🔒 Limpieza completa")
```

<!--
NO MORE NOTES
-->
---

## Checklist

✅ Entender qué son las excepciones
✅ Usar `try-except` correctamente
✅ Conocer excepciones comunes
✅ Lanzar excepciones con `raise`
✅ Crear excepciones personalizadas
✅ Usar `with` para archivos
✅ Aplicar buenas prácticas
✅ Escribir código robusto

<!--
NO MORE NOTES
-->
---

<!-- _paginate: false -->

# ¡Gracias!

**Ahora a practicar 🚀**

Las excepciones no son tus enemigos, son oportunidades para hacer tu código más robusto y profesional.

**Recordá:**
- Capturá errores específicos
- Usá `with` para recursos
- Validá entradas
- Mensajes claros y útiles

¡Tu código será más confiable y profesional!
