# MongoDB
# Actividad 1

- Autor: Juan A. García Cuevas
- Fecha: 05/06/2016

Sobre el modelo de datos trabajado en la sesión de MongoDB sobre la aplicación de ventas entre particulares, implemente las siguientes operaciones para el 
shell de MongoDB:

> Es necesario aportar los comandos oportunos para la creación de la base de datos e inserción de documentos en la colección "ítems".  

## 0. Inserción de datos

```
use ventasParticulares

db.items.remove({})

item1={
  descripcion: "Mando xBox negro",
  fecha: new Date ("2015, 3, 21"),
  precio: 10,
  tags: ["consolas", "xbox", "entretenimiento"],
  vendedor: {email: "pperez@gmail.com", psw: "pperez"},
  localizacion: {longitude: 37.743671, latitude: -2.552276},
  estado: "disponible",
  contraofertas: [
    {email: "llopez@gmail.com", psw: "llopez", oferta: 8, fecha: new Date("2015, 4, 2")},
    {email: "ggomez@gmail.com", psw: "ggomez", oferta: 7, fecha: new Date("2015, 4, 13")}
  ]
}
db.items.insert(item1)

db.items.insert({
  descripcion: "Mando Wii Mario",
  fecha: new Date ("2013, 10, 2"),
  precio: 8,
  tags: ["consolas", "wii", "entretenimiento"], 
  vendedor: {email: "ffernandez@gmail.com", psw: "ffernandez"},
  localizacion: {longitude: 38.743671, latitude: -10.552276},
  estado: "vendido",
  comprador: {email: "llopez@gmail.com", psw: "llopez"},
  contraofertas: [
    {email: "llopez@gmail.com", psw: "llopez", oferta: 7, fecha: new Date("2013, 10, 20")},
    {email: "aalonso@gmail.com", psw: "aalonso", oferta: 5, fecha: new Date("2013, 10, 19")}
  ]
})

db.items.insert({
  descripcion: "Thermomix",
  fecha: new Date ("2015, 5, 2"),
  precio: 80,
  tags: ["robot cocina", "menaje"], 
  vendedor: {email: "ffernandez@gmail.com", psw: "ffernandez"},
  localizacion: {longitude: 38.743671, latitude: -10.552276},
  estado: "disponible"
})

db.items.insert({
  descripcion: "Samsung Galaxy A3 A310F",
  fecha: new Date ("2013, 5, 2"),
  precio: 270,
  tags: ["Teléfono móvil"], 
  vendedor: {email: "pperez@gmail.com", psw: "pperez"},
  localizacion: {longitude: 38.745671, latitude: -10.452276},
  estado: "disponible"
})

db.items.insert({
  descripcion: "Wiko Lenny",
  fecha: new Date ("2013, 3, 7"),
  precio: 85,
  tags: ["Teléfono móvil"], 
  vendedor: {email: "ffernandez@gmail.com", psw: "ffernandez"},
  localizacion: {longitude: 38.723671, latitude: -10.552176},
  estado: "disponible"
})

db.items.insert({
  descripcion: "Apple iPhone 6 64GB",
  fecha: new Date ("2011, 5, 2"),
  precio: 625,
  tags: ["Teléfono móvil"], 
  vendedor: {email: "ggomez@gmail.com", psw: "ggomez"},
  localizacion: {longitude: 38.743641, latitude: -10.532276},
  estado: "disponible"
})

db.items.insert({
  descripcion: "Alcatel 2012",
  fecha: new Date ("2011, 5, 2"),
  precio: 40,
  tags: ["Teléfono móvil"], 
  vendedor: {email: "ggarcia@gmail.com", psw: "ggarcia"},
  localizacion: {longitude: 38.693671, latitude: -10.552976},
  estado: "disponible"
})

db.items.insert({
  descripcion: "Alcatel 2004C",
  fecha: new Date ("2010, 5, 2"),
  precio: 35,
  tags: ["Teléfono móvil"], 
  vendedor: {email: "mmartinez@gmail.com", psw: "mmartinez"},
  localizacion: {longitude: 38.723671, latitude: -10.5226},
  estado: "vendido",
  comprador: {email: "ggomez@gmail.com", psw: "ggomez"},
  contraofertas: [
    {email: "aalonso@gmail.com", psw: "aalonso", oferta: 580, fecha: new Date("2013, 6, 6")}
  ]
})

db.items.insert({
  descripcion: "Huawei Ascend Y625",
  fecha: new Date ("2010, 5, 2"),
  precio: 590,
  tags: ["Teléfono móvil"], 
  vendedor: {email: "ggomez@gmail.com", psw: "ggomez"},
  localizacion: {longitude: 38.793671, latitude: -10.55276},
  estado: "vendido",
  comprador: {email: "ggomez@gmail.com", psw: "ggomez"},
  contraofertas: [
    {email: "ggomez@gmail.com", psw: "ggomez", oferta: 580, fecha: new Date("2010, 6, 6")}
  ]
})

db.items.insert({
  descripcion: "Huawei Y625",
  fecha: new Date ("2015, 3, 9"),
  precio: 400,
  tags: ["Teléfono móvil"], 
  vendedor: {email: "bberlanga@gmail.com", psw: "bberlanga"},
  localizacion: {longitude: 38.93671, latitude: -10.45276},
  estado: "disponible"
})

db.items.insert({
  descripcion: "Nokia XYZ",
  fecha: new Date ("2014, 5, 2"),
  precio: 55,
  tags: ["Teléfono móvil"], 
  vendedor: {email: "jmoya@gmail.com", psw: "jmoya"},
  localizacion: {longitude: 38.636134, latitude: -10.55276},
  estado: "disponible"
})
```

**Muestra el número de productos insertados**:
```
db.items.find().count()

	11
```

**Muestra la lista de productos insertados**:
```
db.items.find( {}, {_id:0, descripcion:1, precio:1, fecha:1, estado:1} ).pretty()

	{
		"descripcion" : "Mando xBox negro",
		"fecha" : ISODate("2015-03-20T23:00:00Z"),
		"precio" : 10,
		"estado" : "disponible"
	}
	{
		"descripcion" : "Mando Wii Mario",
		"fecha" : ISODate("2013-10-01T22:00:00Z"),
		"precio" : 8,
		"estado" : "vendido"
	}
	{
		"descripcion" : "Thermomix",
		"fecha" : ISODate("2015-05-01T22:00:00Z"),
		"precio" : 80,
		"estado" : "disponible"
	}
	{
		"descripcion" : "Samsung Galaxy A3 A310F",
		"fecha" : ISODate("2013-05-01T22:00:00Z"),
		"precio" : 270,
		"estado" : "disponible"
	}
	{
		"descripcion" : "Wiko Lenny",
		"fecha" : ISODate("2013-03-06T23:00:00Z"),
		"precio" : 85,
		"estado" : "disponible"
	}
	{
		"descripcion" : "Apple iPhone 6 64GB",
		"fecha" : ISODate("2011-05-01T22:00:00Z"),
		"precio" : 625,
		"estado" : "disponible"
	}
	{
		"descripcion" : "Alcatel 2012",
		"fecha" : ISODate("2011-05-01T22:00:00Z"),
		"precio" : 40,
		"estado" : "disponible"
	}
	{
		"descripcion" : "Alcatel 2004C",
		"fecha" : ISODate("2010-05-01T22:00:00Z"),
		"precio" : 35,
		"estado" : "vendido"
	}
	{
		"descripcion" : "Huawei Ascend Y625",
		"fecha" : ISODate("2010-05-01T22:00:00Z"),
		"precio" : 590,
		"estado" : "vendido"
	}
	{
		"descripcion" : "Huawei Y625",
		"fecha" : ISODate("2015-03-08T23:00:00Z"),
		"precio" : 400,
		"estado" : "disponible"
	}
	{
		"descripcion" : "Nokia XYZ",
		"fecha" : ISODate("2014-05-01T22:00:00Z"),
		"precio" : 55,
		"estado" : "disponible"
	}
```

## 1. Actualizar la colección "ítems" para hacer una contraoferta al primer producto disponible que esté etiquetado como "Teléfono móvil" y que haya sido puesto en venta con posterioridad al 1/1/2014.

**Muestra la lista de productos etiquetados con "Teléfono móvil"**:
```
db.items.find(
	{tags:"Teléfono móvil"}, 
	{_id:0, descripcion:1, fecha:1, estado:1}
)

	{ "descripcion" : "Samsung Galaxy A3 A310F", "fecha" : ISODate("2013-05-01T22:00:00Z"), "estado" : "disponible" }
	{ "descripcion" : "Wiko Lenny", "fecha" : ISODate("2013-03-06T23:00:00Z"), "estado" : "disponible" }
	{ "descripcion" : "Apple iPhone 6 64GB", "fecha" : ISODate("2011-05-01T22:00:00Z"), "estado" : "disponible" }
	{ "descripcion" : "Alcatel 2012", "fecha" : ISODate("2011-05-01T22:00:00Z"), "estado" : "disponible" }
	{ "descripcion" : "Alcatel 2004C", "fecha" : ISODate("2010-05-01T22:00:00Z"), "estado" : "vendido" }
	{ "descripcion" : "Huawei Ascend Y625", "fecha" : ISODate("2010-05-01T22:00:00Z"), "estado" : "vendido" }
	{ "descripcion" : "Huawei Y625", "fecha" : ISODate("2015-03-08T23:00:00Z"), "estado" : "disponible" }
	{ "descripcion" : "Nokia XYZ", "fecha" : ISODate("2014-05-01T22:00:00Z"), "estado" : "disponible" }
```

**Muestra la lista de productos etiquetados con "Teléfono móvil" y fecha posterior al 1/1/2014**:
```
var fechaBusqueda = new Date(2014, 1, 1)

db.items.find(
	{ tags: "Teléfono móvil", fecha: {$gte: fechaBusqueda} }, 
	{ _id:0, descripcion:1, fecha:1, tags:1, contraofertas:1 }
)

	{ "descripcion" : "Huawei Y625", "fecha" : ISODate("2015-03-08T23:00:00Z"), "tags" : [ "Teléfono móvil" ] }
	{ "descripcion" : "Nokia XYZ", "fecha" : ISODate("2014-05-01T22:00:00Z"), "tags" : [ "Teléfono móvil" ] }
```

**Añade una contraoferta al primer producto etiquetado con "Teléfono móvil" y fecha posterior al 1/1/2014**:
```
db.items.update(
	{ tags: "Teléfono móvil", fecha: {$gte: fechaBusqueda} }, 
	{ $set:
		{ contraofertas: 
			{
				email: "iberg@gmail.com",
				psw: "iberg",
				oferta: 590,
				fecha: ISODate("2015-12-12T22:00:00Z")
			}
		}
	}
)

	WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```

**Comprueba los cambios**:
```
db.items.find(
	{ tags: "Teléfono móvil", fecha: {$gte: fechaBusqueda} }, 
	{ _id:0, descripcion:1, fecha:1, tags:1, contraofertas:1 }
)

	{ "descripcion" : "Huawei Y625", "fecha" : ISODate("2015-03-08T23:00:00Z"), "tags" : [ "Teléfono móvil" ], "contraofertas" : { "email" : "iberg@gmail.com", "psw" : "iberg", "oferta" : 590, "fecha" : ISODate("2015-12-12T22:00:00Z") } }
	{ "descripcion" : "Nokia XYZ", "fecha" : ISODate("2014-05-01T22:00:00Z"), "tags" : [ "Teléfono móvil" ] }
```


## 2. Actualizar la colección "ítems" para modificar el estado de todos los productos puestos en venta antes de 1/1/2012 y cuyo estado sea disponible. El nuevo estado pasará a ser descatalogado.

**Muestra los productos puestos en venta antes de 1/1/2012**:
```
var fechaBusqueda = new Date(2012, 1, 1)

db.items.find( 
	{ fecha: { $lte: fechaBusqueda } }, 
	{ _id:0, descripcion:1, fecha:1, estado:1 }
).pretty()

	{
		"descripcion" : "Apple iPhone 6 64GB",
		"fecha" : ISODate("2011-05-01T22:00:00Z"),
		"estado" : "disponible"
	}
	{
		"descripcion" : "Alcatel 2012",
		"fecha" : ISODate("2011-05-01T22:00:00Z"),
		"estado" : "disponible"
	}
	{
		"descripcion" : "Alcatel 2004C",
		"fecha" : ISODate("2010-05-01T22:00:00Z"),
		"estado" : "vendido"
	}
	{
		"descripcion" : "Huawei Ascend Y625",
		"fecha" : ISODate("2010-05-01T22:00:00Z"),
		"estado" : "vendido"
	}
```

**Muestra los productos puestos en venta antes de 1/1/2012 y estado disponible**:
```
db.items.find( 
	{ fecha: { $lte: fechaBusqueda }, estado: "disponible" }, 
	{ _id:0, descripcion:1, fecha:1, estado:1 }
).pretty()

	{
		"descripcion" : "Apple iPhone 6 64GB",
		"fecha" : ISODate("2011-05-01T22:00:00Z"),
		"estado" : "disponible"
	}
	{
		"descripcion" : "Alcatel 2012",
		"fecha" : ISODate("2011-05-01T22:00:00Z"),
		"estado" : "disponible"
	}
```

**Actualiza todos los productos anteriores asignándoles el estado descatalogado**:
```
db.items.update( 
	{ fecha: { $lte: fechaBusqueda }, estado: "disponible" }, 
	{ $set: { estado: "descatalogado" } },
	{ multi: true }
)

	WriteResult({ "nMatched" : 2, "nUpserted" : 0, "nModified" : 2 })
```

**Comprueba los cambios**:
```
db.items.find( 
	{ fecha: { $lte: fechaBusqueda }, estado: "disponible" }, 
	{ _id:0, descripcion:1, fecha:1, estado:1 }
).pretty()

```

```
db.items.find( 
	{ fecha: { $lte: fechaBusqueda }, estado: "descatalogado" }, 
	{ _id:0, descripcion:1, fecha:1, estado:1 }
).pretty()

	{
		"descripcion" : "Apple iPhone 6 64GB",
		"fecha" : ISODate("2011-05-01T22:00:00Z"),
		"estado" : "descatalogado"
	}
	{
		"descripcion" : "Alcatel 2012",
		"fecha" : ISODate("2011-05-01T22:00:00Z"),
		"estado" : "descatalogado"
	}
```

## 3. Recuperar la descripción y precio de todos los productos etiquetados como "entretenimiento", cuyo estado sea disponible y que estén en venta en un punto cercano al nuestro (+- 1000 mts.)

**Crea el índice y realiza la búsqueda:**
```
db.items.ensureIndex({"localizacion":"2dsphere"})

db.items.find( 
	{ 
		tags: "entretenimiento",
		localizacion:
		{ $near:
			{ $geometry:
				{
					type:"Point",
					coordinates:[ 37.743670, -2.552276]
				}, 
				$maxDistance:1000
			}
		} 
	}, 
	{
		_id: 0,
		descripcion: 1,
		precio: 1,
		tags: 1,
		estado: 1,
		localizacion: 1
	} 
).pretty()

	{
		"descripcion" : "Mando xBox negro",
		"precio" : 10,
		"tags" : [
			"consolas",
			"xbox",
			"entretenimiento"
		],
		"localizacion" : {
			"longitude" : 37.743671,
			"latitude" : -2.552276
		},
		"estado" : "disponible"
	}
```
	
## 4. Averiguar el número de ítems disponibles que estén etiquetados como "Teléfono móvil" y que cuesten menos de 60€.
```
db.items.find(
	{ tags: "Teléfono móvil", precio: { $lte: 60 } }
).count()

	3
```

## 5. Eliminar los registros cuyo estado sea "vendido" y que hubieran sido puestos a la venta antes del 1/1/2012.  

**Muestra la lista de productos que cumplen las condiciones para ser eliminados**:
```
var fechaBusqueda = new Date(2012, 1, 1)

db.items.find(
	{ estado: "vendido", fecha: { $lte: fechaBusqueda } },
	{ _id:0, descripcion:1, fecha:1, precio:1, estado:1 }
).pretty()

	{
		"descripcion" : "Alcatel 2004C",
		"fecha" : ISODate("2010-05-01T22:00:00Z"),
		"precio" : 35,
		"estado" : "vendido"
	}
	{
		"descripcion" : "Huawei Ascend Y625",
		"fecha" : ISODate("2010-05-01T22:00:00Z"),
		"precio" : 590,
		"estado" : "vendido"
	}
```

**Elimina los productos**:
```
db.items.remove(
	{ estado: "vendido", fecha: { $lte: fechaBusqueda } },
	{ multi: true }
)

	WriteResult({ "nRemoved" : 2 })
```

**Comprueba que los productos han sido eliminados**:
```
db.items.find(
	{ estado: "vendido", fecha: { $lte: fechaBusqueda } },
	{ _id:0, descripcion:1, fecha:1, precio:1, estado:1 }
).pretty()

```

```
db.items.find().count()

	9
```
