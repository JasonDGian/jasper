Para columnizar , en las propiedades del informe, en la raiz de la izquierda, se encuentra en avanzadas, propiedad column count. Tambien se puede cambiar el orden de impresion de horizonta la vertical y vicevers.

# Insertar código en App Java.
1. Buscar dependencias de Maven para usar Jasper.

**Dependencias Maven**
```xml
<!-- https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports -->
<dependency>
    <groupId>net.sf.jasperreports</groupId>
    <artifactId>jasperreports</artifactId>
    <version>7.0.1</version>
</dependency>
<!-- https://mvnrepository.com/artifact/mysql/mysql-connector-java -->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.33</version>
</dependency>
<!-- https://mvnrepository.com/artifact/org.hsqldb/hsqldb -->
<dependency>
    <groupId>org.hsqldb</groupId>
    <artifactId>hsqldb</artifactId>
    <version>2.7.4</version>
    <classifier>jdk8</classifier>  
<!-- !!!!Para que se baje el jar de hsqldb. Si no hay que añadirlo a mano en el classpath en el proyecto si ponemos lo que viene en maven de hsqldb –>
</dependency>
<!-- https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports-pdf -->
<dependency>
    <groupId>net.sf.jasperreports</groupId>
    <artifactId>jasperreports-pdf</artifactId>
    <version>7.0.1</version>
</dependency>
```

2. Arrancar la base de datos de ejemplo.
HSQLDB es una bbdd local y 
https://drive.google.com/file/d/1DN4ODBUig3F59-yh_G86HpY-fNcA0xdN/view

descomprimir y abrir cmd
y ejecutar el comando para compilar la bbdd y arranque.
compilar lib/hsqldb.jar.
```cmd
java -cp lib/hsqldb.jar org.hsqldb.Server -database.0 file:data/database/test -dbname.0 test
```

Debemos ver el puerto en el que escucha la bbdd.
![image](https://github.com/user-attachments/assets/f74ed8e9-9fe8-493f-bb14-d4157f88b102)

3. 



