---
asignatura: PMDM
tema: 2
tipo: tema
estado: completo
fecha: 2026-09-17
tags:
  - DAM/tema
  - DAM/pmdm/kotlin/tipos
---

# Jerarquía de tipos en Kotlin

> [!info] Asignatura
> [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|Programación Multimedia y Dispositivos Móviles]] · Tema 2 · Kotlin

## 1. Tipos numéricos

Kotlin ofrece tipos numéricos con distintos rangos y precisión:

| Tipo | Tamaño | Rango / precisión |
| --- | ---: | --- |
| `Byte` | 8 bits | −128 a 127 |
| `Short` | 16 bits | −32 768 a 32 767 |
| `Int` | 32 bits | −2³¹ a 2³¹−1 |
| `Long` | 64 bits | −2⁶³ a 2⁶³−1 |
| `Float` | 32 bits | Aproximadamente 6–7 dígitos decimales |
| `Double` | 64 bits | Aproximadamente 15–16 dígitos decimales |

```kotlin
val edad: Int = 20
val distancia: Long = 3_000_000_000L
val temperatura: Double = 21.5
val ratio: Float = 0.75F
```

Los literales enteros se infieren normalmente como `Int`, y los decimales como `Double`. Los sufijos `L` y `F` permiten indicar `Long` y `Float`.

### Conversión numérica

Kotlin no convierte automáticamente entre tipos numéricos. Usa funciones explícitas:

```kotlin
val x: Int = 42
val y: Long = x.toLong()
val z: Double = y.toDouble()
```

Funciones habituales: `toByte()`, `toShort()`, `toInt()`, `toLong()`, `toFloat()`, `toDouble()`.

> [!warning] Conversión puede perder información
> Convertir `Double` a `Int` trunca decimales. Convertir un número grande a un tipo más pequeño puede desbordar.

### Precisión arbitraria

La biblioteca Java ofrece `BigInteger` y `BigDecimal` para valores fuera del rango de tipos primitivos o cuando se requiere precisión decimal exacta.

```kotlin
import java.math.BigInteger

val grande = BigInteger("123456789012345678901234567890")
val resultado = grande * BigInteger.TEN
```

---

## 2. Boolean

`Boolean` solo admite `true` y `false`. Operadores principales:

- `!` negación
- `&&` AND con cortocircuito
- `||` OR con cortocircuito
- `and`, `or`, `xor` como funciones infijas sin cortocircuito

```kotlin
val esAdulto = edad >= 18
val puedeEntrar = esAdulto && tieneEntrada
```

---

## 3. Char y String

`Char` representa un carácter Unicode y se escribe entre comillas simples. `String` representa secuencia de caracteres y se escribe entre comillas dobles.

```kotlin
val inicial: Char = 'K'
val lenguaje: String = "Kotlin"
println(inicial.code) // valor Unicode
```

Las cadenas son inmutables. Se pueden iterar, indexar y consultar mediante `length`, `first()`, `last()` y otros métodos.

---

## 4. Rangos y progresiones

- `a..b`: incluye ambos extremos.
- `a..<b`: incluye inicio y excluye final.
- `a downTo b`: progresión descendente.
- `a..b step n`: progresión con paso.
- `x in rango` / `x !in rango`: comprueba pertenencia.

```kotlin
for (i in 1..5) println(i)       // 1, 2, 3, 4, 5
for (i in 0..<5) println(i)      // 0, 1, 2, 3, 4
for (i in 10 downTo 2 step 2) println(i)
```

---

## 5. Number y jerarquía de tipos

`Number` es supertipo de `Byte`, `Short`, `Int`, `Long`, `Float` y `Double`. No existe conversión implícita entre ellos: llama al método `toXxx()` adecuado.

La jerarquía raíz distingue valores anulables y no anulables:

- `Any`: supertipo común de valores no nulos.
- `Any?`: supertipo que también acepta `null`.
- `Nothing`: subtipo de todos los tipos; representa una expresión que nunca produce valor (por ejemplo, `throw`).
- `Nothing?`: tipo de `null`.

```kotlin
val entero: Any = 42
val texto: Any = "hola"
val universal: Any? = null
```

---

## 6. Null safety

Un tipo nullable lleva `?`: `String?`, `Int?`. Puede contener valor del tipo o `null`. El tipo sin `?` no permite null.

```kotlin
val nombre: String? = null
val seguro: String = "Kotlin"
// val error: String = nombre // no compila: nombre puede ser null
```

Operadores principales:

- `?.` llamada segura: devuelve `null` si receptor es nulo.
- `?:` Elvis: aporta valor alternativo.
- `!!` aserción no nula: lanza `NullPointerException` si es null; úsala con cautela.
- `as?` conversión segura: devuelve `null` si conversión falla.

```kotlin
val longitud = nombre?.length ?: 0
```

---

## 7. Arrays

Los arrays tienen tamaño fijo y acceso por índice desde cero. `Array<T>` contiene referencias; para números existen arrays primitivos `IntArray`, `DoubleArray`, etc.

```kotlin
val notas = doubleArrayOf(8.5, 7.0, 9.0)
for (nota in notas) println(nota)
```

---

## Esquema resumen de conceptos clave

| Concepto | Sintaxis / tipo | Comportamiento |
| --- | --- | --- |
| Enteros | `Byte`, `Short`, `Int`, `Long` | Rangos de 8 a 64 bits |
| Decimales | `Float`, `Double` | Precisión binaria finita |
| Conversión | `toInt()`, `toDouble()` | Explícita; puede perder información |
| Booleanos | `&&`, `||`, `!` | `&&` y `||` cortocircuitan |
| Carácter | `Char` | Unicode; consultar `.code` |
| Rangos | `..`, `..<`, `downTo`, `step` | Progresiones y pertenencia con `in` |
| Tipos raíz | `Any`, `Any?`, `Nothing` | Jerarquía común de Kotlin |
| Nulabilidad | `T` / `T?` | `T?` admite null; acceso seguro con `?.` |
| Arrays | `Array<T>`, `IntArray` | Tamaño fijo; índices desde cero |

## Relaciones

- Ejercicios: [[02.1 - Ejercicios 2 Jerarquia de Tipos]]
- [[01 - Introduccion a Kotlin]] · [[03 - Funciones]]
- Índice: [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|PMDM]]

## Para repasar

- [ ] ¿Por qué Kotlin requiere conversiones numéricas explícitas?
- [ ] Diferenciar `Any` y `Any?`
- [ ] Explicar `?.`, `?:` y `!!`
- [ ] Diferenciar `..` y `..<`
- [ ] ¿Qué pierde una conversión de `Double` a `Int`?
