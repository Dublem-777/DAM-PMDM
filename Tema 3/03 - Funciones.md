---
asignatura: PMDM
tema: 3
tipo: tema
estado: completo
fecha: 2026-09-17
tags:
  - DAM/tema
  - DAM/pmdm/kotlin/funciones
---

# Funciones en Kotlin

> [!info] Asignatura
> [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|Programación Multimedia y Dispositivos Móviles]] · Tema 3 · Kotlin

## 1. Declaración de funciones

Se declara una función con `fun`, nombre, parámetros tipados y tipo de retorno:

```kotlin
fun sumar(a: Int, b: Int): Int {
    return a + b
}
```

Si no se indica tipo de retorno en una función con cuerpo, se infiere `Unit`:

```kotlin
fun saludar(nombre: String) {
    println("Hola, $nombre")
}
```

`Unit` equivale aproximadamente a `void` en Java, pero es tipo real de Kotlin.

## 2. Expresión única

Una función cuyo cuerpo es una expresión puede usar `=`; tipo de retorno puede inferirse:

```kotlin
fun doble(valor: Int) = valor * 2
fun esPar(valor: Int): Boolean = valor % 2 == 0
```

## 3. Parámetros y argumentos

Parámetros son nombres y tipos declarados en función. Argumentos son valores proporcionados en llamada. Se pueden escribir en varias líneas y dejar coma final:

```kotlin
fun presentar(
    nombre: String,
    edad: Int,
) {
    println("$nombre tiene $edad años")
}
```

### Argumentos con nombre

Permiten indicar destino explícitamente, útil al omitir parámetros con valor por defecto o reordenar llamada:

```kotlin
fun crearInforme(titulo: String, detallado: Boolean = true) { /* ... */ }
crearInforme(titulo = "Ventas", detallado = false)
```

Al mezclar llamadas, argumentos posicionales van antes de los nombrados.

## 4. Valores por defecto

```kotlin
fun conectar(host: String, puerto: Int = 443) {
    println("$host:$puerto")
}

conectar("example.com")
conectar("example.com", 8080)
```

Los parámetros obligatorios se suelen colocar antes de los opcionales.

## 5. Retorno, Nothing y excepciones

`return` devuelve valor y finaliza función. `throw` lanza excepción. Ambos son expresiones de tipo `Nothing`, que no produce valor normal:

```kotlin
fun validar(numero: Int): String =
    if (numero > 0) "positivo"
    else throw IllegalArgumentException("Debe ser positivo")
```

## 6. Sobrecarga

Se puede declarar varias funciones con igual nombre y firmas diferentes. Firma depende del nombre y parámetros, no del tipo de retorno.

```kotlin
fun combinar(a: Int, b: Int) = a + b
fun combinar(a: String, b: String) = a + b
```

## 7. vararg y spread

`vararg` acepta cantidad variable de argumentos. Dentro, parámetro se comporta como array.

```kotlin
fun imprimir(vararg textos: String) {
    for (texto in textos) println(texto)
}

val datos = arrayOf("A", "B")
imprimir("Inicio", *datos, "Fin")
```

`*` desempaqueta un array en argumentos. Si hay parámetros posteriores a `vararg`, se proporcionan por nombre.

## 8. Funciones infijas

Una función miembro o de extensión puede declararse `infix` si tiene un único parámetro, sin `vararg` ni valor por defecto:

```kotlin
infix fun Int.veces(texto: String): String = texto.repeat(this)
val resultado = 3 veces "ja"
```

## Esquema resumen de conceptos clave

| Concepto | Sintaxis | Uso |
| --- | --- | --- |
| Función | `fun f(x: T): R` | Operación reutilizable |
| Cuerpo expresión | `fun f(x: T) = expr` | Funciones breves |
| Unit | omitir retorno | Función sin resultado útil |
| Parámetro opcional | `x: T = valor` | Valor por defecto |
| Argumento nombrado | `x = valor` | Claridad y omisión de opcionales |
| Sobrecarga | mismo nombre, parámetros distintos | Operaciones relacionadas |
| Vararg | `vararg xs: T` | Número variable de entradas |
| Spread | `*array` | Pasar elementos de array a vararg |
| Infix | `infix fun x(y)` | Llamada legible sin punto/paréntesis |

## Relaciones

- Ejercicios: [[03.1 - Ejercicios 3 Funciones]]
- [[01 - Introduccion a Kotlin]] · [[02 - Jerarquia de tipos]]
- Índice: [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|PMDM]]

## Para repasar

- [ ] Diferenciar parámetro y argumento
- [ ] ¿Qué devuelve función sin retorno explícito?
- [ ] ¿Cómo se pasan arrays a un `vararg`?
- [ ] ¿Qué requisitos tiene `infix`?
