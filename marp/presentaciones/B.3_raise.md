---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Excepciones - Parte 3/4' -->

# <!-- fit --> raise
## Lanzar excepciones
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: 'Lanzar excepciones' -->

# Sentencia raise

**raise = lanzar/disparar excepción**

```python
def dividir(a, b):
    if b == 0:
        raise ValueError("El divisor no puede ser 0")
    return a / b

# Uso
try:
    resultado = dividir(10, 0)
except ValueError as e:
    print(f"Error: {e}")
```

**Vos decidís cuándo hay error**

---

<!-- _header: '¿Por qué raise?' -->

# Validar entrada

```python
def crear_usuario(nombre, edad):
    """Crea usuario validando datos."""
    if not nombre or len(nombre) < 2:
        raise ValueError("Nombre muy corto")
    
    if edad < 0 or edad > 120:
        raise ValueError("Edad inválida")
    
    # Si llegó acá, datos válidos
    return {"nombre": nombre, "edad": edad}
```

**Fallar rápido es mejor que dato malo**

---

<!-- _header: 'Tipos de excepciones' -->

# Elegir el tipo correcto

**ValueError:**
```python
raise ValueError("Valor incorrecto")
```

**TypeError:**
```python
raise TypeError("Tipo incorrecto")
```

**RuntimeError:**
```python
raise RuntimeError("Error en tiempo de ejecución")
```

**Exception (genérico):**
```python
raise Exception("Error general")
```

---

<!-- _header: 'Re-lanzar' -->

# Re-raise: propagar error

```python
def procesar_datos(datos):
    try:
        resultado = operacion_compleja(datos)
    except ValueError as e:
        print(f"Advertencia: {e}")
        raise  # Re-lanza la misma excepción

# Uso
try:
    procesar_datos(datos_malos)
except ValueError:
    print("Error manejado en nivel superior")
```

**raise solo = re-lanzar**

---

<!-- _header: 'Excepciones personalizadas' -->

# Crear tus propias excepciones

```python
class EdadInvalidaError(Exception):
    """Excepción para edad inválida."""
    pass

class NombreVacioError(Exception):
    """Excepción para nombre vacío."""
    pass

def validar_usuario(nombre, edad):
    if not nombre:
        raise NombreVacioError("Nombre no puede estar vacío")
    if edad < 0:
        raise EdadInvalidaError(f"Edad {edad} es negativa")
```

---

<!-- _header: 'Usar excepciones propias' -->

# Capturar excepciones custom

```python
try:
    validar_usuario("", -5)
except NombreVacioError:
    print("Error: Debe ingresar un nombre")
except EdadInvalidaError:
    print("Error: La edad debe ser positiva")
```

**Más específico y claro**

---

<!-- _header: 'Herencia' -->

# Jerarquía de excepciones

```python
class ErrorValidacion(Exception):
    """Base para errores de validación."""
    pass

class ErrorEmail(ErrorValidacion):
    """Error específico de email."""
    pass

class ErrorTelefono(ErrorValidacion):
    """Error específico de teléfono."""
    pass

# Capturar todos los de validación
except ErrorValidacion:
    print("Error de validación")
```

---

<!-- _header: 'Excepciones con datos' -->

# Agregar información

```python
class ErrorRango(Exception):
    """Error de valor fuera de rango."""
    def __init__(self, valor, minimo, maximo):
        self.valor = valor
        self.minimo = minimo
        self.maximo = maximo
        mensaje = f"{valor} fuera de rango [{minimo}, {maximo}]"
        super().__init__(mensaje)

# Uso
try:
    raise ErrorRango(150, 0, 100)
except ErrorRango as e:
    print(f"Error: {e}")
    print(f"Valor: {e.valor}")
```

---

<!-- _header: 'Cuándo usar raise' -->

# Buenas prácticas

**✅ Usar raise para:**
* Validar parámetros de funciones
* Indicar condiciones imposibles
* Errores de lógica de negocio
* Precondiciones no cumplidas

**❌ No usar para:**
* Control de flujo normal
* Casos esperados (usar if)
* Ocultar bugs

---

<!-- _header: 'Ejemplo práctico' -->

# Validador de contraseña

```python
class ContraseñaDebiError(Exception):
    """Contraseña no cumple requisitos."""
    pass

def validar_contraseña(password):
    """Valida contraseña."""
    if len(password) < 8:
        raise ContraseñaDebiError(
            "Mínimo 8 caracteres"
        )
    
    if not any(c.isupper() for c in password):
        raise ContraseñaDebiError(
            "Debe tener mayúsculas"
        )
    
    if not any(c.isdigit() for c in password):
        raise ContraseñaDebiError(
            "Debe tener números"
        )
    
    return True
```

---

<!-- _header: 'Usar validador' -->

# Manejo completo

```python
while True:
    try:
        password = input("Contraseña: ")
        validar_contraseña(password)
        print("✅ Contraseña válida")
        break
    except ContraseñaDebiError as e:
        print(f"❌ {e}")
    except KeyboardInterrupt:
        print("\n⚠️ Operación cancelada")
        break
```

---

<!-- _header: 'Ejercicio' -->

# Validador de rango

**Crea una función que:**
1. Se llame `validar_rango`
2. Reciba `valor`, `minimo`, `maximo`
3. Lance excepción si está fuera de rango
4. Devuelva True si es válido
5. Pruébala con try-except

---

<!-- _header: 'Ejercicio - Solución' -->

# Posible solución

```python
class ErrorRango(Exception):
    """Valor fuera del rango permitido."""
    pass

def validar_rango(valor, minimo, maximo):
    """Valida que valor esté en rango."""
    if valor < minimo:
        raise ErrorRango(
            f"{valor} es menor que {minimo}"
        )
    if valor > maximo:
        raise ErrorRango(
            f"{valor} es mayor que {maximo}"
        )
    return True

# Probar
try:
    validar_rango(15, 0, 10)
except ErrorRango as e:
    print(f"Error: {e}")
```

---

<!-- _header: 'Resumen' -->

# Para recordar

**raise:**
* Lanzar excepción manualmente
* Validar condiciones
* `raise` solo → re-lanzar

**Excepciones custom:**
* Heredar de Exception
* Nombre descriptivo
* Agregar datos extra

**Cuándo usar:**
* Validaciones
* Precondiciones
* Errores de negocio

**Próximo:**
* Buenas prácticas

---

<!-- _class: centered -->

# ¿Preguntas?
