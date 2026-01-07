---
marp: true
theme: default
paginate: true
header: 'Manejo de Excepciones en Python'
footer: 'Crear programas robustos y confiables'
style: |
  section {
    font-size: 26px;
  }
  h1 {
    color: #1976d2;
  }
  code {
    background-color: #f5f5f5;
  }
---

<!-- _paginate: false -->
<!-- _header: '' -->

# Manejo de Excepciones en Python

**Aprende a manejar errores como un profesional**

---

## ¿Qué vas a aprender?

* Qué son las **excepciones** y por qué ocurren
* Usar **`try-except`** para capturar errores
* Cláusulas **`else`** y **`finally`**
* **Lanzar** tus propias excepciones
* **Crear excepciones personalizadas**
* **Buenas prácticas** para código robusto

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

---

<!-- _class: lead -->

# ¿Qué es una Excepción?

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

---

<!-- _class: lead -->

# Tipos Comunes de Excepciones

---

## Excepciones Más Frecuentes

| Excepción | Cuándo Ocurre | Ejemplo |
|-----------|---------------|---------|
| `ValueError` | Valor inválido | `int("abc")` |
| `TypeError` | Tipo incorrecto | `"5" + 3` |
| `ZeroDivisionError` | División por cero | `10 / 0` |
| `FileNotFoundError` | Archivo no existe | `open("x.txt")` |
| `KeyError` | Clave no existe | `dict["key"]` |
| `IndexError` | Índice fuera de rango | `lista[100]` |

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

---

<!-- _class: lead -->

# Try-Except Básico

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

---

<!-- _class: lead -->

# Try-Except-Else-Finally

---

## Las 4 Cláusulas

| Cláusula | Cuándo se Ejecuta | Para Qué Sirve |
|----------|-------------------|----------------|
| `try` | Siempre primero | Código que puede fallar |
| `except` | Solo si hay error | Manejar el error |
| `else` | Solo si NO hay error | Código de éxito |
| `finally` | SIEMPRE | Limpieza (cerrar archivos) |

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

---

<!-- _class: lead -->

# Lanzar Excepciones

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

---

<!-- _class: lead -->

# Excepciones Personalizadas

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

---

<!-- _class: lead -->

# Context Managers (with)

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

---

<!-- _class: lead -->

# Buenas Prácticas

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

---

<!-- _class: lead -->

# Resumen

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

---

## Excepciones Comunes

| Excepción | Cuándo |
|-----------|--------|
| `ValueError` | Valor incorrecto |
| `TypeError` | Tipo incorrecto |
| `ZeroDivisionError` | División por cero |
| `FileNotFoundError` | Archivo no existe |
| `KeyError` | Clave no existe |
| `IndexError` | Índice fuera de rango |

---

## Buenas Prácticas Esenciales

1. ✅ Ser **específico** con los except
2. ✅ **No ocultar** errores (no usar `pass`)
3. ✅ Mantener bloques `try` **pequeños**
4. ✅ Usar **mensajes descriptivos**
5. ✅ **Limpiar recursos** (usar `with`)
6. ✅ **Documentar** excepciones que se lanzan
7. ✅ No capturar `Exception` genérico

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
