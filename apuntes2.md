# Elegir origen de datos MYSQL.
nuevo > jasper report > blank report > repository explorer > data adapters click derecho > create new adapter > Database JDB connection > dar nombre, elegir `MySQL (com.mysql.jdbc.Driver), jdbc:mysql://localhost/empresa y poner credenciales.
    
A partir de ahi pinchar aen pestaña Driver Classpath.
![image](https://github.com/user-attachments/assets/a6678847-b3d3-4f98-b18b-55dba308225a)

## driver classpath
![image](https://github.com/user-attachments/assets/a76fd955-bd8b-4fae-ae9e-b3f39606f7b4)

## añadir el driver mysql.
Este driver es un driver que debemos de descargar a parte para poderlo registrar con Jasper.
![image](https://github.com/user-attachments/assets/dfb318d1-c36b-480e-8f6d-6d719426c293)

con el driver añadido dando en test deberia de funcionar.



# Crear consultas con diagrama
arrastramos las tablas interesadas al diagrama, y luego arrastramos los ID a los campos que representan para crear la conexion en la consulta como join.
![image](https://github.com/user-attachments/assets/d2b1540f-cd5f-406c-90f8-dd19f1be7378)

>![CAUTION]
> es importante importar una tabla a la vez, y leer los datos de esta antes de introducir la siguiente para evitar problemas de comunicacion con MySql. por algun motivo.
