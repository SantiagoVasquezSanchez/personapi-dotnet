# personapi-dotnet

Para realizar el despligue de la aplicación es importante.
1. Descargar la imagen de docker de SQL Server 2022 express del repositorio de docker
  https://hub.docker.com/_/microsoft-mssql-server
2. Hacer build y run de la imagen con el siguiente comando: docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=yourStrong(!)Password" -e "MSSQL_PID=Express" -p 1433:1433 -d mcr.microsoft.com/mssql/server:2022-latest
3. Utilizar el SSMS para conectarse a la base de datos usando el USUARIO= SA, CONTRASeÑA = yourStrong(!)Password y dirección del servidor IP= ip del equipo,1433  (que es el puerto en que configuramos el sqlServer)
4. Crear una Query, copiar pegar y ejecutar lo que esta en el archivo de sqlQueryCreaciónYLlenado.txt
5. Antes de crear una imagen con el dockerfile incluido en el codigo de .NET se requiere cambiar la cadena de conexión del programa, esto pues quedo configurada con la ip del equipo en que se realizo el despliegue del SQL server mas no de donde se va a utilizar
 "PersonaDbContext": "Server=X.X.X.X,1433;Database=persona_db;User ID=sa; Password=yourStrong(!)Password;Integrated Security=False;Trusted_Connection=False;TrustServerCertificate=True;"
Cambiar la ip por la ip del computador donde se esta desplegando.
6. Crear imagen utilizando el Dockerfile generado para el despliegue posterior.
7. Desplegar en docker la imagen.
8. Utilizar.
