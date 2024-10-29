# Cassandra Database Setup with Docker Compose

Este proyecto proporciona un entorno de base de datos Cassandra utilizando Docker Compose con la versión 5.0 o superior.

## Requisitos

- Docker
- Docker Compose

## Configuración del Entorno

El archivo `docker-compose.yml` crea un contenedor de Cassandra con las siguientes configuraciones:

- **Cluster Name**: TestCluster
- **Data Center**: datacenter1
- **Rack**: rack1
- **Seeds**: `cassandra` (nombre del contenedor)

La base de datos estará disponible en el puerto `9042` en tu máquina local.

## Archivos

- **docker-compose.yml**: Define el servicio de Cassandra, incluyendo su configuración y volumen para persistencia de datos.
- **Volumen**: `cassandra_data` para asegurar la persistencia de datos en reinicios.

## Cómo Configurar y Ejecutar Cassandra

1. **Clonar el Repositorio**

   Clona este repositorio en tu máquina local o crea un directorio nuevo y descarga los archivos necesarios.

   ```bash
   git clone https://github.com/Carlososuna11/cassandra-docker-setup.git
   cd cassandra-docker-setup
   ```

2. **Iniciar el Contenedor**

   Ejecuta el siguiente comando para iniciar el contenedor en segundo plano:

   ```bash
   docker-compose up -d
   ```

   Esto descargará la imagen de Cassandra (si aún no la tienes) y ejecutará el contenedor de Cassandra con las configuraciones especificadas en `docker-compose.yml`.

3. **Verificar que Cassandra esté Corriendo**

   Puedes verificar el estado del contenedor ejecutando:

   ```bash
   docker ps
   ```

   Cassandra debería aparecer como un contenedor en ejecución en la lista.

4. **Conectar a Cassandra**

   Para conectarte a la base de datos, puedes utilizar `cqlsh` (la CLI de Cassandra) ejecutando el siguiente comando:

   ```bash
   docker exec -it cassandra cqlsh
   ```

   Esto abrirá una consola `cqlsh` para interactuar con Cassandra. Una vez dentro, puedes crear tablas, insertar datos y realizar consultas.

5. **Detener Cassandra**

   Para detener y eliminar los contenedores, ejecuta:

   ```bash
   docker-compose down
   ```

   Esto detendrá el contenedor de Cassandra y liberará los recursos, manteniendo los datos en el volumen `cassandra_data`.

## Configuraciones Adicionales

Puedes modificar el archivo `docker-compose.yml` para:

- Cambiar el nombre del cluster (`CASSANDRA_CLUSTER_NAME`)
- Ajustar el número de tokens (`CASSANDRA_NUM_TOKENS`)
- Configurar más nodos (ideal para configuraciones de clúster multinodo)

Para obtener más información sobre las variables de entorno de Cassandra, consulta la [documentación oficial de Cassandra en Docker Hub](https://hub.docker.com/_/cassandra).

## Solución de Problemas

Si experimentas problemas al iniciar Cassandra, puedes revisar los logs del contenedor para obtener detalles:

```bash
docker logs cassandra
```
