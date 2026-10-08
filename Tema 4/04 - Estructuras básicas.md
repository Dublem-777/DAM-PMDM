---
asignatura: PMDM
tema: 4
tipo: tema
estado: completo
fecha: 2026-09-17
tags:
  - DAM/tema
  - DAM/pmdm/kotlin/estructuras
---

# Estructuras básicas en Kotlin

> [!info] Asignatura
> [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|Programación Multimedia y Dispositivos Móviles]] · Tema 4 · Kotlin

## 1. Expresiones condicionales

Kotlin usa `if` y `if/else` tanto como instrucciones como expresiones. En una expresión, ambas ramas deben producir un valor:

```kotlin
val mayor = if (a > b) a else b
```

`when` permite comparar valor o condiciones de forma clara:

```kotlin
val etiqueta = when {
    nota >= 9 -> "Sobresaliente"
    nota >= 7 -> "Notable"
    nota >= 5 -> "Aprobado"
    else -> "Suspenso"
}
```

## 2. Bucles

### while y do-while

`while` comprueba condición antes de cada iteración. `do-while` ejecuta cuerpo al menos una vez:

```kotlin
var contador = 0
while (contador < 3) {
    println(contador)
    contador++
}
```

### for

`for` recorre rangos, arrays, cadenas y colecciones:

```kotlin
for (i in 1..5) println(i)
for (caracter in "Kotlin") println(caracter)
```

Se puede recorrer índices con `indices`, o pares índice/valor con `withIndex()`.

## 3. Control de bucle

- `break`: termina bucle actual.
- `continue`: salta a siguiente iteración.
- Etiquetas (`bucle@`) permiten controlar bucles anidados.

```kotlin
for (i in 1..10) {
    if (i == 5) continue
    if (i == 8) break
    println(i)
}
```

## 4. Rangos

`..` incluye ambos extremos; `..<` excluye límite final. `downTo` crea rango descendente y `step` cambia incremento.

```kotlin
for (i in 0..<array.size) println(array[i])
for (i in 10 downTo 0 step 2) println(i)
```

## 5. Arrays y recorridos

Los arrays tienen longitud fija; se accede con `[índice]` desde cero. `for (elemento in array)` recorre valores. `array.indices` recorre índices.

```kotlin
val nombres = arrayOf("Ana", "Luis")
for ((indice, nombre) in nombres.withIndex()) {
    println("$indice: $nombre")
}
```

## Esquema resumen de conceptos clave

| Estructura | Uso |
| --- | --- |
| `if/else` | Elegir entre dos ramas; también expresión |
| `when` | Selección entre varios casos |
| `while` | Repetir mientras condición sea verdadera |
| `do-while` | Ejecutar al menos una vez |
| `for` | Recorrer rangos y colecciones |
| `break` / `continue` | Terminar o saltar iteración |
| `..` / `..<` | Rango cerrado / semiabierto |
| `indices` / `withIndex()` | Iterar con posición |

## Relaciones

- [[03 - Funciones]] · [[05 - Operaciones con tipos nullables]]
- Índice: [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|PMDM]]

## Para repasar

- [ ] Diferenciar `while` y `do-while`
- [ ] Usar `when` como expresión
- [ ] Recorrer un array con índice y valor
- [ ] Diferenciar `break` y `continue`
