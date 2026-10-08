---
asignatura: PMDM
tema: 1
tipo: tema
estado: completo
fecha: 2026-09-17
tags:
  - DAM/tema
  - DAM/pmdm/kotlin-introduccion
---

# 1 · Introducción a Kotlin

> [!info] Asignatura
> [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|Programación Multimedia y Dispositivos Móviles]] · Tema 1 · Kotlin
> Fuente original: `Documentos/Notas/Introducción a Kotlin.md`

## Índice del tema

- [[#1. El lenguaje Kotlin]]
- [[#2. IDEs]]
- [[#3. La función main()]]
- [[#4. Salida por consola]]
- [[#5. Variables]]
- [[#6. Entrada desde consola]]

---

## 1. El lenguaje Kotlin

### 1.1 ¿Qué es Kotlin?

**Kotlin** es un lenguaje de programación de **propósito general**, de **código abierto**, **multiplataforma**, **multiparadigma** y **estáticamente tipado**.

| Característica | Qué significa |
| --- | --- |
| Propósito general | No está atado a un dominio concreto: backend, móvil, frontend… |
| Código abierto | El código fuente del compilador es libre y modificable |
| Multiplataforma | Compila a varios destinos: JVM, JavaScript o código máquina |
| Multiparadigma | Soporta programación estructurada, orientada a objetos y funcional |
| Estáticamente tipado | El tipo de cada variable se comprueba en **compilación**, no en ejecución |

- Desarrollado originalmente por **JetBrains**, ahora bajo la **Kotlin Foundation**.
- Existen **KEEP** (Kotlin Evolution and Enhancement Process), procedimiento público para proponer y discutir cambios en el lenguaje.

### 1.2 Compilación: los tres targets

Kotlin es **compilado** a un lenguaje de nivel inferior.

| Target | Qué genera |
| --- | --- |
| Kotlin/JVM | Bytecode de la JVM |
| Kotlin/JS | JavaScript |
| Kotlin/Native | Código máquina |

### 1.3 Interoperabilidad con Java

**Kotlin/JVM y Java son interoperables**:

- Código y bibliotecas Java utilizables desde Kotlin/JVM.
- Kotlin/JVM puede usar clases, módulos y biblioteca estándar de Java.
- Java puede usar código Kotlin, salvo *suspend functions*.
- Archivos Kotlin y Java pueden coexistir en un proyecto, facilitando migración progresiva.

### 1.4 Dónde se usa Kotlin

- Backend, por ejemplo con **Spring**.
- **Android**, lenguaje estándar de facto.
- **Kotlin Multiplatform**: código compartido para Android, iOS, frontend y backend.
- **Jetpack Compose**: interfaces nativas en Kotlin para Android y otros destinos.

---

## 2. IDEs

| Herramienta | Para qué | Enlace |
| --- | --- | --- |
| **IntelliJ IDEA** | IDE popular para Kotlin | https://www.jetbrains.com/es-es/idea/ |
| **Android Studio** | IDE para Android, basado en IntelliJ | https://developer.android.com/studio?hl=es-419 |
| **Kotlin Playground** | Probar Kotlin online | https://play.kotlinlang.org/ |

IntelliJ permite ver bytecode Java equivalente: **Tools → Kotlin → Show Kotlin Bytecode → Decompile**.

---

## 3. La función main()

`main()` es el punto de entrada del programa Kotlin.

```kotlin
fun main() {
    println("Hello, World")
}
```

Con argumentos:

```kotlin
fun main(args: Array<String>) {
    println("Hello, World")
}
```

A diferencia de Java, `main()` es función de nivel superior y no requiere clase contenedora.

---

## 4. Salida por consola

| Función | Qué hace |
| --- | --- |
| `print(expr)` | Imprime expresión |
| `println(expr)` | Imprime expresión y añade salto de línea |

---

## 5. Variables

### 5.1 val y var

| Palabra | Mutabilidad | Uso |
| --- | --- | --- |
| `val` | Referencia inmutable | Preferir siempre que sea posible |
| `var` | Referencia reasignable | Cuando haga falta cambiar valor |

```kotlin
val question = "¿De qué color es el caballo blanco de Santiago?"
var name = "Baldomero"
val answer: Int = 42
```

### 5.2 Inferencia y tipado

El compilador puede inferir tipo del valor inicial. Una variable solo admite valores de su tipo estático.

```kotlin
var answer = 42
// answer = "no answer" // Error: tipo incompatible
```

Las variables deben inicializarse antes de leerse. `val` impide reasignar referencia, no mutar el objeto referenciado:

```kotlin
val languages = arrayListOf("Java")
languages.add("Kotlin") // válido: cambia el objeto, no la referencia
```

No hace falta punto y coma al final de cada sentencia.

---

## 6. Entrada desde consola

| Función | Resultado |
| --- | --- |
| `readln()` | Lee línea como `String`; lanza excepción al fallar |
| `readlnOrNull()` | Lee línea o devuelve `null` |
| `toInt()` | Convierte a entero; lanza excepción si falla |
| `toIntOrNull()` | Convierte o devuelve `null` |

```kotlin
fun main() {
    print("Nombre: ")
    val name = readln()
    print("Edad: ")
    val age = readln().toInt()
    println("$name tiene $age años")
}
```

`split()` divide una cadena y `map` permite convertir cada parte:

```kotlin
val numbers: List<Int> = readln().split(' ').map { it.toInt() }
```

---

## Esquema resumen de conceptos clave

- Kotlin: compilado, estáticamente tipado, multiplataforma y multiparadigma.
- Targets: JVM, JavaScript y Native.
- Interoperabilidad Kotlin/JVM con Java; ambos lenguajes pueden coexistir.
- `fun main()` inicia programa; `print`/`println` muestran salida.
- `val` referencia inmutable; `var` reasignable. Tipos estáticos e inicialización obligatoria.
- Entrada: `readln()`, conversión `toXxx()` y variantes seguras `toXxxOrNull()`.

## Relaciones

- Práctica: [[01.1 - Ejercicios 1 Introduccion a Kotlin]]
- [[02 - Jerarquia de tipos]]
- [[03 - Funciones]]

## Para repasar

- [ ] Diferenciar Kotlin/JVM, Kotlin/JS y Kotlin/Native
- [ ] Explicar `val` frente a `var`
- [ ] Diferenciar `readln()` y `readlnOrNull()`
- [ ] Explicar por qué objeto mutable puede cambiar aunque esté referenciado por `val`
