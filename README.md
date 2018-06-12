# sql-bootcamp

Ejercicios realizados en el curso SQL Bootcamp de Udemy.

## Docker Compose

Para facilidad de uso de este repositorio, se creo un archivo docker-compose.yml con la configuración necesaria para correr Postgres y PgAdmin4.

Previamente instalado docker y docker-compose en tu sistema operativo, corre el siguiente comando en la terminal.

```bash
docker-compose up -d
```

Accesa a pg admin en tu navegador usando <http://localhost> o <http://127.0.0.1>.

Asegurate que los puertos 80 y 5432 esten libres.

Si te arroja un error en los puertos 80 del pgAdmin u 5432 del postgres, cambialos a tu gusto en el archivo docker-compose.