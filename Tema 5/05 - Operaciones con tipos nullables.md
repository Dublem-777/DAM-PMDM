---
asignatura: PMDM
tema: 5
tipo: tema
estado: completo
fecha: 2026-09-17
tags:
  - DAM/tema
  - DAM/pmdm/kotlin/nulabilidad
---

# Operaciones con tipos nullables

> [!info] Asignatura
> [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|Programación Multimedia y Dispositivos Móviles]] · Tema 5 · Kotlin

## 1. Tipos nullable

Un tipo seguido de `?` puede contener `null`: `String?`, `Int?`. Un tipo sin `?` garantiza valor no nulo.

```kotlin
var nombre: String? = "Ana"
nombre = null
val obligatorio: String = "Kotlin"
```

## 2. Llamada segura `?.`

Ejecuta acceso o llamada solo si receptor no es nulo. Si es nulo, expresión completa produce null:

```kotlin
val longitud: Int? = nombre?.length
```

Las llamadas seguras se pueden encadenar:

```kotlin
val codigo = cliente?.direccion?.codigoPostal
```

## 3. Operador Elvis `?:`

Proporciona valor alternativo cuando expresión izquierda es nula:

```kotlin
val longitud: Int = nombre?.length ?: 0
```

También puede terminar ejecución, porque `return` y `throw` son expresiones:

```kotlin
val usuario = buscarUsuario() ?: return
```

## 4. Aserción no nula `!!`

`!!` convierte tipo nullable a no nullable, pero lanza `NullPointerException` si valor es null. Preferir `?.`, `?:` o comprobación explícita.

```kotlin
val seguro: String = nombre!!
```

## 5. Comprobación explícita y smart cast

Tras comprobar contra null, compilador puede tratar valor como no nullable en ese ámbito:

```kotlin
if (nombre != null) {
    println(nombre.length)
}
```

Smart cast requiere que variable no cambie de forma que invalide comprobación (por ejemplo, propiedad `val` estable).

## 6. Conversión segura

`as?` intenta conversión y devuelve null si falla:

```kotlin
val texto: String? = valor as? String
```

## Esquema resumen de conceptos clave

| Operador | Uso | Resultado |
| --- | --- | --- |
| `?.` | Acceso seguro | Valor nullable |
| `?:` | Valor alternativo | Tipo no nullable si alternativa lo es |
| `!!` | Afirmar no nulidad | Puede lanzar NPE |
| `as?` | Conversión segura | Tipo destino nullable |
| `if (x != null)` | Comprobación | Smart cast cuando variable es estable |

## Relaciones

- [[02 - Jerarquia de tipos]] · [[04 - Estructuras básicas]]
- Índice: [[DAM/Programacion_Multimedia_y_Dispositivos_Moviles/Indice|PMDM]]

## Para repasar

- [ ] Reescribir `!!` con `?.` y `?:`
- [ ] Explicar smart cast
- [ ] Diferenciar `as` y `as?`
