---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Excepciones - Parte 4/4' -->

# <!-- fit --> Buenas Prácticas
## Excepciones profesionales
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: 'Regla 1' -->

# Ser específico

**❌ Capturar todo:**
```python
try:
    operacion()
except:  # Captura TODO (incluso KeyboardInterrupt)
    print("Error")
```

**✅ Capturar específico:**
```python
try:
    operacion()
except ValueError:
    print("Error de valor")
except TypeError:
    print("Error de tipo")
```

---

<!-- _header: 'Regla 2' -->

# No silenciar errores

**❌ Ocultar problema:**
```python
try:
    operacion_critica()
except Exception:
    pass  # ¡Silencia el error!
```

**✅ Al menos registrar:**
```python
try:
    operacion_critica()
except Exception as e:
    print(f"Error crítico: {e}")
    # O logging.error(e)
```

---

<!-- _header: 'Regla 3' -->

# Mensajes descriptivos

**❌ Mensaje genérico:**
```python
raise ValueError("Error")
```

**✅ Mensaje útil:**
```python
raise ValueError(
    f"Edad {edad} debe estar entre 0 y 120"
)
```

**El mensaje debe ayudar a entender**

---

<!-- _header: 'Regla 4' -->

# Scope mínimo

**❌ try demasiado amplio:**
```python
try:
    # 50 líneas de código
    # Solo 1 puede fallar
except ValueError:
    print("Error")
```

**✅ try mínimo:**
```python
configurar()
preparar()
try:
    operacion_riesgosa()
except ValueError:
    print("Error")
finalizar()
```

---

<!-- _header: 'Regla 5' -->

# Orden de except

**❌ Genérico primero:**
```python
try:
    operacion()
except Exception:  # Captura todo
    print("Error general")
except ValueError:  # Nunca se ejecuta
    print("Error específico")
```

**✅ Específico primero:**
```python
try:
    operacion()
except ValueError:
    print("Error de valor")
except Exception:
    print("Error general")
```

---

<!-- _header: 'Patrón: Reintentos' -->

# Reintentar operación

```python
def operacion_con_reintentos(max_intentos=3):
    """Reintenta operación si falla."""
    for intento in range(max_intentos):
        try:
            return operacion_riesgosa()
        except ErrorTemporal as e:
            if intento == max_intentos - 1:
                raise  # Último intento, propagar error
            print(f"Intento {intento + 1} falló, reintentando...")
            time.sleep(1)
```

---

<!-- _header: 'Patrón: Valor por defecto' -->

# Default cuando falla

```python
def obtener_configuracion(clave, default=None):
    """Obtiene config o devuelve default."""
    try:
        return config[clave]
    except KeyError:
        return default

# Uso
puerto = obtener_configuracion("puerto", 8080)
host = obtener_configuracion("host", "localhost")
```

---

<!-- _header: 'Patrón: Validación acumulativa' -->

# Acumular errores

```python
def validar_formulario(datos):
    """Valida y acumula errores."""
    errores = []
    
    if not datos.get("nombre"):
        errores.append("Nombre requerido")
    
    if not datos.get("email"):
        errores.append("Email requerido")
    
    if datos.get("edad", 0) < 18:
        errores.append("Debe ser mayor de edad")
    
    if errores:
        raise ValidationError(errores)
    
    return True
```

---

<!-- _header: 'Logging' -->

# Registrar errores

```python
import logging

logging.basicConfig(level=logging.INFO)

def procesar_archivo(nombre):
    """Procesa archivo con logging."""
    try:
        with open(nombre) as f:
            datos = f.read()
        logging.info(f"Archivo {nombre} procesado")
        return datos
    except FileNotFoundError:
        logging.error(f"Archivo {nombre} no encontrado")
        raise
    except Exception as e:
        logging.exception("Error inesperado")
        raise
```

---

<!-- _header: 'Context managers' -->

# with: Manejo automático

```python
# ❌ Manual (propenso a errores)
archivo = open("datos.txt")
try:
    contenido = archivo.read()
finally:
    archivo.close()

# ✅ Con context manager
with open("datos.txt") as archivo:
    contenido = archivo.read()
# Se cierra automáticamente
```

**with maneja cleanup automáticamente**

---

<!-- _header: 'Excepciones en APIs' -->

# Documentar excepciones

```python
def dividir(a, b):
    """
    Divide dos números.
    
    Args:
        a: Dividendo
        b: Divisor
        
    Returns:
        float: Resultado de a/b
        
    Raises:
        ValueError: Si b es 0
        TypeError: Si a o b no son números
    """
    if b == 0:
        raise ValueError("Divisor no puede ser 0")
    if not isinstance(a, (int, float)):
        raise TypeError("a debe ser número")
    if not isinstance(b, (int, float)):
        raise TypeError("b debe ser número")
    return a / b
```

---

<!-- _header: 'Testing con excepciones' -->

# Probar que lance error

```python
import pytest

def test_dividir_por_cero():
    """Verifica que lance ValueError."""
    with pytest.raises(ValueError):
        dividir(10, 0)

def test_tipo_incorrecto():
    """Verifica que lance TypeError."""
    with pytest.raises(TypeError):
        dividir("10", 5)
```

---

<!-- _header: 'Ejemplo completo' -->

# Sistema robusto

```python
class Usuario:
    def __init__(self, nombre, edad):
        self.validar_nombre(nombre)
        self.validar_edad(edad)
        self.nombre = nombre
        self.edad = edad
    
    def validar_nombre(self, nombre):
        if not isinstance(nombre, str):
            raise TypeError("Nombre debe ser string")
        if not nombre or len(nombre) < 2:
            raise ValueError("Nombre muy corto")
    
    def validar_edad(self, edad):
        if not isinstance(edad, int):
            raise TypeError("Edad debe ser entero")
        if edad < 0 or edad > 120:
            raise ValueError(f"Edad {edad} inválida")

# Uso
try:
    usuario = Usuario("Ana", 20)
except (ValueError, TypeError) as e:
    print(f"Error creando usuario: {e}")
```

---

<!-- _header: 'Checklist' -->

# Antes de lanzar a producción

**Verifica:**
- [ ] Excepciones específicas (no bare except)
- [ ] Mensajes descriptivos
- [ ] No silenciar errores importantes
- [ ] Logging de errores críticos
- [ ] Documentar excepciones en docstrings
- [ ] Try-catch en scope mínimo
- [ ] Cleanup con finally o with
- [ ] Tests para casos de error
- [ ] Validar entradas críticas

---

<!-- _class: inverse -->

# <!-- fit --> ¡Excepciones completas!
## Código robusto y profesional

---

<!-- _header: 'Resumen completo' -->

# Lo que aprendiste

**Conceptos:**
* Qué son excepciones
* Tipos comunes
* Flujo de ejecución

**Técnicas:**
* try-except-else-finally
* raise y re-raise
* Excepciones custom

**Buenas prácticas:**
* Ser específico
* No silenciar
* Logging
* Patrones comunes

---

<!-- _header: 'Habilidades' -->

# Ahora podés

**Crear:**
* Programas robustos
* Validaciones profesionales
* Excepciones custom

**Aplicar:**
* Manejo de errores elegante
* Logging efectivo
* Patrones de reintentos

**Próxima sección:**
* Módulos y organización

---

<!-- _class: centered -->

# ¡Felicitaciones!
## Excepciones completadas

---

<!-- _class: centered -->

# ¿Preguntas?
