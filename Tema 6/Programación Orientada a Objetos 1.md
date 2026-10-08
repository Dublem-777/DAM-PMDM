---
asignatura: PMDM
tema: 6
tipo: tema
estado: completo
fecha: 2026-09-17
tags:
  - DAM/tema
  - DAM/pmdm/kotlin/poo
---

# Programación Orientada a Objetos 1

> [!info] Asignatura
> [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|Programación Multimedia y Dispositivos Móviles]] · Tema 6 · Kotlin

## 1. Clases y objetos

Una clase define propiedades y comportamiento. Un objeto es instancia concreta de clase.

```kotlin
class Persona(val nombre: String, var edad: Int) {
    fun saludar() = println("Hola, soy $nombre")
}

val persona = Persona("Ada", 36)
persona.saludar()
```

## 2. Constructores

El constructor primario se declara en cabecera. Puede llevar parámetros con `val`/`var`, que generan propiedades. Un constructor secundario usa `constructor` y debe delegar al primario con `this(...)`.

```kotlin
class Rectangulo(val ancho: Double, val alto: Double) {
    constructor(lado: Double) : this(lado, lado)
}
```

## 3. Propiedades

Propiedades Kotlin encapsulan acceso a estado. `val` solo tiene getter; `var` tiene getter y setter. Se pueden definir getters/setters personalizados:

```kotlin
class Temperatura(var celsius: Double) {
    val fahrenheit: Double
        get() = celsius * 9 / 5 + 32
}
```

## 4. Métodos y `this`

Las funciones miembro acceden a propiedades y otras funciones de instancia. `this` referencia instancia actual y puede omitirse si no hay ambigüedad.

## 5. Visibilidad

- `public`: visible por defecto.
- `private`: visible dentro de declaración contenedora.
- `protected`: clase y subclases.
- `internal`: módulo Kotlin.

## 6. Data classes

`data class` genera `equals`, `hashCode`, `toString`, `componentN` y `copy` a partir de propiedades del constructor primario:

```kotlin
data class Punto(val x: Int, val y: Int)
val otro = Punto(1, 2).copy(y = 5)
```

## 7. Objetos singleton y companion

`object` declara singleton. `companion object` agrupa miembros asociados a clase, accesibles mediante nombre de clase.

```kotlin
object Configuracion { const val VERSION = "1.0" }
class Fabrica { companion object { fun crear() = Fabrica() } }
```

## Esquema resumen de conceptos clave

| Concepto | Uso |
| --- | --- |
| `class` | Definir tipo y estado |
| Constructor primario | Inicializar instancia desde cabecera |
| `val` / `var` | Propiedades de solo lectura o mutables |
| Getter/setter | Controlar acceso a propiedad |
| Visibilidad | Limitar acceso (`private`, `protected`, `internal`, `public`) |
| `data class` | Modelar datos con métodos generados |
| `object` | Singleton |
| `companion object` | Miembros asociados a clase |

## Relaciones

- Ejercicios: [[Tema 6/06.1 - Ejercicios 6 Programación Orientada a Objetos 1]]
- [[Tema 7/Programación Orientada a Objetos 2]]
- Índice: [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|PMDM]]

## Para repasar

- [ ] Diferenciar constructor primario y secundario
- [ ] Explicar getters/setters de propiedades
- [ ] ¿Qué métodos genera `data class`?
- [ ] Diferenciar `object` y `companion object`
