---
asignatura: PMDM
tema: 7
tipo: tema
estado: completo
fecha: 2026-09-17
tags:
  - DAM/tema
  - DAM/pmdm/kotlin/poo
---

# Programación Orientada a Objetos 2

> [!info] Asignatura
> [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|Programación Multimedia y Dispositivos Móviles]] · Tema 7 · Kotlin

## 1. Herencia

Las clases Kotlin son `final` por defecto. Para permitir herencia, clase base debe ser `open`; los miembros que se sobrescriben también:

```kotlin
open class Animal(val nombre: String) {
    open fun sonido() = println("...")
}

class Perro(nombre: String) : Animal(nombre) {
    override fun sonido() = println("Guau")
}
```

Una clase derivada invoca constructor de clase base desde su cabecera.

## 2. Sobrescritura

`override` implementa o reemplaza miembro heredado `open` o abstracto. Sobrescritura es polimórfica: llamada se resuelve según objeto real.

## 3. Clases abstractas

Una clase `abstract` no se instancia directamente y puede declarar miembros abstractos sin implementación. Subclases concretas deben implementarlos.

```kotlin
abstract class Figura {
    abstract fun area(): Double
}
```

## 4. Interfaces

Una clase puede implementar varias interfaces. Interfaz declara contratos y puede incluir implementaciones por defecto. Propiedades de interfaz no almacenan estado de instancia.

```kotlin
interface Imprimible {
    fun imprimir()
}
```

## 5. Polimorfismo y casting

Una referencia del tipo base puede apuntar a instancia de subtipo. `is` comprueba tipo y habilita smart cast. `as` fuerza conversión; `as?` devuelve null si falla.

```kotlin
fun describir(animal: Animal) {
    if (animal is Perro) animal.sonido()
}
```

## 6. Sealed classes

`sealed class` o `sealed interface` restringe subtipos directos. Permite `when` exhaustivo:

```kotlin
sealed interface Resultado
data class Exito(val valor: String) : Resultado
data class Error(val mensaje: String) : Resultado

fun mostrar(r: Resultado) = when (r) {
    is Exito -> r.valor
    is Error -> r.mensaje
}
```

## Esquema resumen de conceptos clave

| Concepto | Sintaxis | Uso |
| --- | --- | --- |
| Herencia | `open class`, `: Base()` | Reutilizar y especializar |
| Sobrescritura | `override` | Implementar comportamiento heredado |
| Abstracta | `abstract class` | Base incompleta no instanciable |
| Interfaz | `interface` | Contrato implementable por varios tipos |
| Polimorfismo | referencia base, objeto derivado | Comportamiento según tipo real |
| Smart cast | `is` | Usar miembro específico tras comprobar tipo |
| Sealed | `sealed class/interface` | Jerarquía cerrada y `when` exhaustivo |

## Relaciones

- [[Tema 6/Programación Orientada a Objetos 1]]
- Ejercicios: [[Tema 7/07.1 - Ejercicios 7 Programación Orientada a Objetos 2]]
- Índice: [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|PMDM]]

## Para repasar

- [ ] ¿Por qué clases Kotlin son `final` por defecto?
- [ ] Diferenciar clase abstracta e interfaz
- [ ] Explicar polimorfismo y `override`
- [ ] ¿Qué ventaja ofrecen jerarquías `sealed` con `when`?
