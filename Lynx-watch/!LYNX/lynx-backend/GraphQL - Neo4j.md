#lynx 
#backend

![[graf-ql.jpg]]
>La cajita sonriente de abajo representa el resolver

### Links importantes
Curso [Apollo](https://www.apollographql.com/tutorials/lift-off-part2/02-exploring-our-data)

### [Intro](#intro) 

El backend se compone de 3 partes:
- El _schema_ de graphql
- Los resolvers de graphql
- El código extra para gestionar la información desde la BDD

El __que__ se va a devolver en las consultas que llegan desde el cliente se define o bien en los _type_ o en las _query_ del _schema_ de graphql:
```graphql
type Cosa {
	campos: [String]!
}

type Query {
	buscarCosas(idcosa:String): [Cosa]
}

```

```ts
export const resolvers = {
	Query: {
		buscarCosas:(object, params, ctx, resolveInfo) => {
			return buscarBDDCosas(params.idcosa)
		}
	}
}

```

Cuando se lanza una query `buscarCosas{}` desde un cliente, en el servidor se ejecuta el resolver con el mismo nombre y se devuelve la información tal como la ha pedido en la query. Los resolvers siempre tienen los mismos parámetros en el .ts, cambian los que se reciben por `params`.

En `ctx` se almacena el contexto de _express_, definido en `src/app.ts`, se guardan las referencias a las funciones que usan las BDD.
### [Relaciones](#relaciones)
Directiva `@relationship` en el campo del `type` en el schema. `type` especifica el tipo de arco.
- `IN @relationship(type: "---", direction: IN)`
- `OUT @relationship(type: "---", direction: OUT)`
Las relaciones pueden tener propiedades `@relationshipProperties`

