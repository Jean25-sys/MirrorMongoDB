# MirrorMongoDB

# Configuración de Conjunto de Réplicas en MongoDB

## 1. Iniciar la Primera Instancia

Abre una terminal y ejecuta el siguiente comando para iniciar la primera instancia de MongoDB:

```shell
mongod --replSet RS --dbpath "C:\data\db\espejo1" --port 27018
```

## 2. Iniciar la Segunda Instancia

En una segunda terminal, inicia la segunda instancia de MongoDB con el siguiente comando:

```shell
mongod --replSet RS --dbpath "C:\data\db\espejo2" --port 27019
```

## 3. Conexión al Nodo Primario

Abre una tercera terminal y conéctate al primer nodo (en el puerto 27018) usando `mongosh`:

```shell
mongosh --host localhost --port 27018
```

## 4. Inicializar el Conjunto de Réplicas

En la misma terminal (tercera), inicializa el conjunto de réplicas con el siguiente comando:

```javascript
rs.initiate({
  _id: "RS",
  members: [
    { _id: 0, host: "localhost:27018" },
    { _id: 1, host: "localhost:27019" }
  ]
})
```

## 5. Verificar el Estado del Conjunto de Réplicas

Para verificar el estado del conjunto de réplicas, ejecuta el siguiente comando:

```javascript
rs.status()
```

Este comando proporcionará información sobre el estado de cada miembro del conjunto de réplicas, indicando cuál es el nodo primario (PRIMARY) y cuáles son los nodos secundarios (SECONDARY).

## Notas

- **Permisos de acceso**: Asegúrate de que las instancias de MongoDB puedan comunicarse entre sí. En entornos de producción, es recomendable configurar adecuadamente los permisos y la seguridad de red.
- **Manejo de errores**: Si `rs.status()` no muestra el estado esperado o si encuentras errores, revisa los logs de MongoDB para obtener más información sobre posibles problemas.

---

Este archivo `.md` detalla los pasos necesarios para configurar un conjunto de réplicas básico en MongoDB. Asegúrate de tener en cuenta las configuraciones de seguridad y autenticación, especialmente en entornos de producción.


INSERT DE DATOS EN FORMATO JSON
{
    "nombre": "Juan Pérez",
    "edad": 30,
    "email": "juan.perez@example.com",
    "direccion": {
        "calle": "Calle Falsa 123",
        "ciudad": "Lima",
        "pais": "Perú"
    },
    "hobbies": ["fútbol", "lectura", "música"]
}
