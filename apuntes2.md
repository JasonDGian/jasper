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

>[!CAUTION]
> es importante importar una tabla a la vez, y leer los datos de esta antes de introducir la siguiente para evitar problemas de comunicacion con MySql. por algun motivo.


Vamos a sorting
![image](https://github.com/user-attachments/assets/f145350f-c943-478d-a521-cfcc7775b531)
![image](https://github.com/user-attachments/assets/861f7b19-aa72-409a-97b2-b856ab4f952f)


para ñadir un grupo
click derecho, create group, por el campo elejdio, damos nombre al grupo, siguiente y añadir cabecera y pie. 


al hacer recuentos de entidades, si lo hacemos con una mega tabla como la del ejemplo deberemos usar el DISTINCT.
ç

## Configurar tiempo de evaluacion de expresion.

vamos al campo que deseamos que se renderize, y pinchamos en text field
![image](https://github.com/user-attachments/assets/c37e3a87-a11c-4e33-97bf-7f9914b72db4)

sumar valor por grupo

controlar que el campo sea sumable
![image](https://github.com/user-attachments/assets/7688d05b-b4c8-4b9f-baa5-864b4a35b9d0)

de no serlo castear.


En la jerarquia de objetos o en la consulta en la pestaña de parametros creamos un nuevo parametor.
luego en la consulta cogemos y arrastramos el parametro que hemos creado desde la lista de parametros.  la consulta se debera de escribir a mano pero el parametro podemos arrastrarrlo para evitar erores sintacticos. de todas formas seria `$P(nombre)`. Podemos definir una propiedad llamada "Is for prompting que hará una petición, si no lo ponemos el parametro podrá dar error. Tademas podemos configurar unvalor por defecto que tomará en el caso de que no especifiquemos nada. Es necesario observar si llega al default value expression en el caso de entregar una cadena vacia como parametro.
