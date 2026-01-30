---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'IA - Parte 3/3' -->

# <!-- fit --> Ética y Verificación
## Usar IA responsablemente
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: 'Verificación es crucial' -->

# La IA se equivoca

**Realidad:**
* IA puede generar código incorrecto
* Puede "alucinar" APIs que no existen
* Puede dar explicaciones erróneas
* Puede mezclar versiones de Python

**Nunca confiar ciegamente**
**Siempre verificar**

---

<!-- _header: 'Proceso de verificación' -->

# Cómo verificar código IA

**1. Leer línea por línea**
* ¿Entiendes cada parte?
* ¿Hay algo extraño?

**2. Ejecutar**
* ¿Funciona?
* ¿Sin errores?

**3. Probar casos**
* Caso normal
* Casos borde
* Entradas inválidas

**4. Comparar con docs**
* ¿Coincide con Python oficial?

---

<!-- _header: 'Ejemplo verificación' -->

# IA te da código

**Output de IA:**
```python
def es_par(n):
    if n % 2 == 0:
        return "par"
    else:
        return "impar"
```

**Tu verificación:**
1. ✅ Lógica correcta
2. ⚠️ Retorna string, no bool
3. ❌ No maneja inputs inválidos
4. ❌ Sin docstring

**Mejoraste el código antes de usar**

---

<!-- _header: 'Experimentar' -->

# Modificar para entender

**No solo copiar, experimenta:**
```python
# Código de IA
resultado = [x**2 for x in range(10)]

# Tu experimento 1: ¿Qué pasa con range(5)?
resultado = [x**2 for x in range(5)]
print(resultado)  # [0, 1, 4, 9, 16]

# Tu experimento 2: ¿Y si uso x**3?
resultado = [x**3 for x in range(5)]
print(resultado)  # [0, 1, 8, 27, 64]

# Tu experimento 3: ¿Puedo filtrar pares?
resultado = [x**2 for x in range(10) if x % 2 == 0]
print(resultado)  # [0, 4, 16, 36, 64]
```

**Experimentar = aprender**

---

<!-- _header: 'Preguntas críticas' -->

# Cuestionar la respuesta

**Ante código de IA pregúntale:**
* "¿Por qué usas este enfoque?"
* "¿Hay forma más simple?"
* "¿Qué pasa si input es []?"
* "¿Este código sigue PEP 8?"
* "¿Hay forma más eficiente?"

**Desarrolla pensamiento crítico**

---

<!-- _header: 'Documentación oficial' -->

# Triangular con docs

**Flujo recomendado:**
```
1. IA explica concepto
   ↓
2. Lees Python docs oficial
   ↓
3. ¿Coinciden?
   ├─ Sí → Probablemente correcto
   └─ No → Investigar más
```

**Documentación oficial es autoridad:**
* docs.python.org
* PEPs oficiales

---

<!-- _header: 'Casos de error' -->

# Errores comunes de IA

**1. APIs que no existen:**
```python
# IA inventa método
lista.sort_reverse()  # ❌ No existe

# Correcto es
lista.sort(reverse=True)  # ✅
```

**2. Sintaxis de versión incorrecta:**
```python
# IA usa Python 3.10+
match valor:  # Python 3.10+
    case 1: ...

# Tu curso usa Python 3.8
# Debes usar if/elif
```

---

<!-- _header: 'Casos de error' -->

# Errores comunes de IA (cont.)

**3. Complejidad innecesaria:**
```python
# IA da código complejo
resultado = list(map(lambda x: x*2, filter(lambda x: x%2==0, nums)))

# Más simple
resultado = [x*2 for x in nums if x%2==0]
```

**4. No maneja excepciones:**
```python
# IA sin validación
def dividir(a, b):
    return a / b  # ❌ Crash si b=0
```

---

<!-- _header: 'Testing' -->

# Probar exhaustivamente

**No confiar en que funciona:**
```python
# IA te da función
def buscar(lista, valor):
    # código de IA
    pass

# TU responsabilidad: probar
assert buscar([1,2,3], 2) == 1
assert buscar([1,2,3], 4) == -1
assert buscar([], 1) == -1
assert buscar([1,1,1], 1) == 0
# etc.
```

**Tests revelan bugs ocultos**

---

<!-- _header: 'Integridad académica' -->

# Ser honesto

**En este curso:**

**✅ Permitido:**
* Pedir explicaciones a IA
* Debugging con ayuda de IA
* Comparar tu solución con IA
* Pedir mejoras de tu código

**❌ No permitido:**
* Pedir código completo de tareas
* Copiar sin entender
* Usar IA en evaluaciones (salvo indicación)
* Hacer trampa con IA

---

<!-- _header: 'Citación' -->

# Cómo citar uso de IA

**Si IA ayudó significativamente:**
```python
"""
Módulo: calculadora.py

Nota sobre IA:
Consulté ChatGPT para entender cómo manejar
excepciones en división por cero. Adapté el
código a mi implementación y agregué validaciones
adicionales.
"""
```

**Transparencia es clave:**
* Muestra integridad
* Permite feedback apropiado
* Evita problemas

---

<!-- _header: 'Línea ética' -->

# Dónde está la línea

**Zona gris - preguntar al docente:**
```
"¿Puedo usar IA para generar casos de prueba?"
"¿Puedo pedir que refactorice mi código?"
"¿Puedo usar IA para traducir pseudocódigo a Python?"
```

**Cuando dudes, pregunta**
**Mejor prevenir que tener problemas después**

---

<!-- _header: 'Aprendizaje genuino' -->

# Trampa a ti mismo

**Si usas IA para copiar:**
* No aprendes de verdad
* Examen será difícil
* Proyecto final será imposible
* Trabajo profesional será frustrante

**La trampa es a ti mismo:**
> Puedes engañar al docente una vez,
> pero no puedes engañarte a ti mismo
> cuando realmente necesites programar

---

<!-- _header: 'Desarrollo de habilidades' -->

# Habilidades cruciales

**Programar requiere:**
* Pensamiento lógico
* Resolución de problemas
* Debugging mental
* Lectura de código
* Diseño de soluciones

**IA puede dar código:**
**Pero no puede darte estas habilidades**

**Solo la práctica genuina las desarrolla**

---

<!-- _header: 'Progresión' -->

# Reducir dependencia con tiempo

**Mes 1:**
* IA para conceptos básicos
* Mucha consulta

**Mes 2:**
* Menos dependencia
* Más autonomía
* IA para verificar

**Mes 3:**
* Mayormente independiente
* IA ocasionalmente
* Para optimizar soluciones propias

**Meta: autonomía profesional**

---

<!-- _header: 'Caso real' -->

# Ejemplo de proceso completo

**1. Intentas resolver:**
```python
# Tu código
def factorial(n):
    # No sé cómo hacer caso base
    pass
```

**2. Consultas IA:**
```
"Explica recursión en factorial.
Dame pista sobre caso base, no código completo."
```

---

<!-- _header: 'Caso real' -->

# Ejemplo de proceso completo (cont.)

**3. IA responde:**
```
"Caso base: cuando n=1 o n=0, retornar 1.
Caso recursivo: n * factorial(n-1)"
```

**4. Implementas tú:**
```python
def factorial(n):
    if n <= 1:
        return 1
    return n * factorial(n-1)
```

**5. Verificas:**
```python
assert factorial(0) == 1
assert factorial(1) == 1
assert factorial(5) == 120
```

---

<!-- _header: 'Caso real' -->

# Ejemplo de proceso completo (cont.)

**6. Pides revisión a IA:**
```
"Revisa mi implementación:
[pegar código]
¿Está correcto? ¿Se puede mejorar?"
```

**7. IA sugiere:**
```
"Funciona correctamente. Sugerencia:
agregar validación para números negativos."
```

**8. Mejoras:**
```python
def factorial(n):
    if n < 0:
        raise ValueError("n debe ser >= 0")
    if n <= 1:
        return 1
    return n * factorial(n-1)
```

**✅ Proceso ético y educativo**

---

<!-- _header: 'Red flags' -->

# Señales de alerta

**🚨 Problemas si:**
* No puedes explicar tu código
* Código usa conceptos no vistos
* Funciona pero no sabes por qué
* Copias y pegas sin leer
* Depende de IA para todo

**✅ Bien si:**
* Entiendes cada línea
* Puedes modificar código
* Experimentaste con él
* IA complementa, no reemplaza

---

<!-- _header: 'Reflexión' -->

# Pregúntate honestamente

**Después de usar IA:**
* ¿Aprendí algo nuevo?
* ¿Puedo replicar esto solo?
* ¿Entiendo el concepto?
* ¿Podría explicarlo a alguien?
* ¿Soy mejor programador?

**Si mayoría es NO:**
**Estás usando IA incorrectamente**

---

<!-- _header: 'Responsabilidad' -->

# Tu responsabilidad

**Como estudiante:**
* Aprender genuinamente
* Desarrollar habilidades
* Ser honesto
* Usar herramientas éticamente

**Como futuro profesional:**
* Código que entiendes
* Soluciones que puedes mantener
* Reputación íntegra
* Habilidades reales

---

<!-- _header: 'Futuro profesional' -->

# Preparación real

**En el trabajo:**
* No siempre tendrás IA
* Necesitas debugging mental
* Código complejo requiere entendimiento
* Entrevistas técnicas son presenciales
* Clientes esperan expertise real

**Aprende de verdad ahora**
**Tu futuro yo te lo agradecerá**

---

<!-- _class: inverse -->

# <!-- fit --> ¡IA responsable!
## Herramienta de aprendizaje, no atajo

---

<!-- _header: 'Resumen final' -->

# Para recordar

**Verificación:**
* Leer, ejecutar, probar
* Comparar con docs oficiales
* Experimentar modificando
* Preguntas críticas

**Ética:**
* Usar para aprender, no copiar
* Ser transparente
* Citar cuando corresponde
* Honestidad académica

**Meta:**
* Desarrollar habilidades reales
* Autonomía progresiva
* Pensamiento crítico
* Programador competente

---

<!-- _header: 'Checklist final' -->

# Antes de usar código IA

- [ ] ¿Entiendo cada línea?
- [ ] ¿Lo probé con varios casos?
- [ ] ¿Comparé con documentación oficial?
- [ ] ¿Puedo explicarlo a alguien?
- [ ] ¿Experimenté modificándolo?
- [ ] ¿Es apropiado mi nivel de dependencia?
- [ ] ¿Estoy usando IA éticamente?
- [ ] ¿Realmente aprendí algo?

---

<!-- _class: centered -->

# ¿Preguntas?

---

<!-- _class: centered -->

# ¡Gracias!
## Usa IA sabiamente

