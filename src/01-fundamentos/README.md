# 01 · Fundamentos: CRUD básico y tipos de datos (BSON)

Este módulo introduce las operaciones fundamentales de MongoDB mediante una
única colección del dominio del coworking: espacios.

El objetivo es aprender a crear, consultar, actualizar y eliminar
documentos (CRUD) antes de introducir conceptos más avanzados como
relaciones entre colecciones, operadores de consulta, agregaciones e índices.

## Concepto
**MongoDB** almacena la información en **documentos**, que tienen una estructura
similar a los objetos JSON.

Los documentos se agrupan dentro de **colecciones**, que son comparables de
forma aproximada con las tablas de una base de datos relacional, aunque
MongoDB utiliza un modelo mucho más flexible y no requiere un esquema fijo
para comenzar a insertar documentos.

Internamente, MongoDB almacena los documentos utilizando BSON
(Binary JSON), que amplía los tipos disponibles en JSON.

Algunos tipos BSON que aparecen en este módulo son:

- String
- Number
- Boolean
- Array
- ObjectId

En módulos posteriores se trabajarán otros tipos y estructuras con mayor
profundidad.

## Entidad utilizada: espacios

**Para practicar el CRUD se utiliza la colección:**
```text
coworking_db
└── espacios
```

**Un documento de ejemplo tiene una estructura como:**
```js
{
  nombre: "Sala A",
  tipo: "sala de reuniones",
  capacidad: 6,
  disponible: true,
  equipamiento: ["proyector", "pizarra", "wifi"]
}
```

Esta entidad fue elegida porque es suficientemente sencilla para aprender CRUD sin introducir todavía relaciones entre colecciones.

---

## Contenido del módulo

|Archivo|Operaciones|Qué se practica|
|---|---|---|
|`01_insertar.mongodb`|`insertOne`, `insertMany`|Creación de documentos y tipos de datos BSON|
|`02_consultar.mongodb`|`find`, `findOne`, proyecciones|Consulta de documentos, filtros exactos y selección de campos|
|`03_actualizar.mongodb`|`updateOne`, `updateMany`, `$set`, `$addToSet`|Modificación parcial de documentos y actualización de arrays|
|`04_eliminar.mongodb`|`deleteOne`, `deleteMany`|Eliminación controlada y verificación previa|

# ▶️ Orden de ejecución

Los archivos están pensados para ejecutarse en orden:

```text
01_insertar.mongodb
        ↓
02_consultar.mongodb
        ↓
03_actualizar.mongodb
        ↓
04_eliminar.mongodb
```

Cada archivo utiliza el estado generado por los anteriores.

Por ejemplo:

- `01_insertar.mongodb` crea los espacios.
- `02_consultar.mongodb` consulta esos espacios.
- `03_actualizar.mongodb` modifica algunos de ellos.
- `04_eliminar.mongodb` elimina algunos documentos y comprueba el estado  
    final de la colección.

Por este motivo, **el resultado puede variar si un archivo se ejecuta varias veces**. Los scripts de este módulo están pensados principalmente como ejercicios de aprendizaje y no como migraciones idempotentes.

### NOTA:
las comparaciones de string en MongoDB son exactas
(sensibles a mayúsculas/minúsculas) por defecto. Ningún filtro avisa si no
encontró coincidencias por eso conviene:
1. Mantener consistencia de formato en los datos desde el momento de insertarlos.
2. Verificar siempre `matchedCount`/`modifiedCount` después de un `update`,
   y hacer un `find()` de confirmación antes y después de operaciones que
   modifican o eliminan datos.