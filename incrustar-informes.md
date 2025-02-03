# 📌 Informes incrustados en apicaciones Java.
Para poder incluir la funcionalidad de crear informes en nuestra aplicacion Java deberemos seguir los siguientes pasos:
1. Disponer y encender la BBDD.
2. Crear el informe y compilarlo en formato `.jasper`.
3. Introducir las dependencias necesarias en el proyecto (ya sea manual o mediante maven o gradle).
4. Introducir el fichero Jasper en la estructura del proyecto.
5. Crear las clases necesarias para su integracion en el proyecto.

## 🔸 Compilar el informe en formato `.jasper`.
Para poder llevar el informe a nuestra aplicacion Java necesitamos un fichero en formato `.jasper`.
Para ello crearemos el informe con los parametros y campos deseados y a continuación pincharemos en `Project` y luego en `Build all`.

![image](https://github.com/user-attachments/assets/c292e6c1-e466-44ae-aa9f-015907bd0976)
      
![image](https://github.com/user-attachments/assets/05bbbb5f-37e7-4cfa-98cd-f1be6d3e33a7)
    
![image](https://github.com/user-attachments/assets/115f75bc-6708-4325-a2c2-38f7fb658b9e)

## 🔸 Introducir las dependencias Maven necesarias.
Para poder realizar las funciones básicas con los informes Jasper es necesario incluir las siguientes dependencias.
- **Jasper Reports**: https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports/7.0.1   
- **Mysql Connector**: https://mvnrepository.com/artifact/mysql/mysql-connector-java/8.0.33
- **HSQL Database**: https://mvnrepository.com/artifact/org.hsqldb/hsqldb/2.7.4
- **Jasper Reports PDF**: https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports-pdf/7.0.1

>[!TIP]
>El arquetipo de Maven preferido para estos trabajos es `quickstart` _(org.apache.maven.archetype 1.5)_. 

**Dependencias para Maven**
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
</dependency>
<!-- https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports-pdf -->
<dependency>
    <groupId>net.sf.jasperreports</groupId>
    <artifactId>jasperreports-pdf</artifactId>
    <version>7.0.1</version>
</dependency>
```


## 📍 Creamos la clase que contiene la información relacionada con el informe.
Es necesario crear una clase que refleje la estructura de la información que deseamos recuperar en el informe.
Para ello crearemos un objeto que contendrá los siguientes elementos:
- Bloque de configuración de conexión a BBDD.
- Constructor que conecta con la BBDD.
- Método que recibe el parametro para el informe.
    - Indica una cadena que representa el fichero Jasper del informe.
    - Indica con una cadena el destino de guardado del fichero.
    - Indica con una cadena el nombre del fichero a guardar.

**Objeto de informe**:
```java
package jasperInforme.jasperInforme;

import java.awt.Desktop;
import java.io.File;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.HashMap;
import java.util.Map;

import javax.swing.JOptionPane;

import net.sf.jasperreports.engine.JasperExportManager;
import net.sf.jasperreports.engine.JasperFillManager;
import net.sf.jasperreports.engine.JasperPrint;

public class Pedidos
{
	public static Connection conexion = null;
	String baseDatos = "jdbc:hsqldb:hsql://localhost:9001/test";
	String usuario = "sa";
	String clave = "";

	// Constructor que conecta a la base de datos de prueba
	public Pedidos()
	{
		try
		{
			Class.forName("org.hsqldb.jdbcDriver").newInstance();
			conexion = DriverManager.getConnection(baseDatos, usuario, clave);
		} catch (ClassNotFoundException cnfe)
		{
			System.err.println("Fallo al cargar JDBC " + cnfe.getMessage());
			System.exit(1);
		} catch (SQLException sqle)
		{
			System.err.println("No se pudo conectar a BD " + sqle.getMessage());
			System.exit(1);
		} catch (java.lang.InstantiationException sqlex)
		{
			System.err.println("Imposible Conectar");
			System.exit(1);
		} catch (Exception ex)
		{
			System.err.println("Imposible Conectar");
			System.exit(1);
		}
	}

	// El método ejecutar recibe el parametro del informe
	public void ejecutar(String ciudad)
	{
		// Ruta del informe respecto del proyecto NetBeans
		String archivojasper = "./informes/Blank_A4.jasper";
		try
		{
			// Cargamos los parametros del informe en una tabla Hash
			Map parametros = new HashMap();
			parametros.put("Parameter1", ciudad);
			// Generamos el informe en memoria
			JasperPrint print = JasperFillManager.fillReport(archivojasper, parametros, conexion);
			// Exporta el informe a PDF
			JasperExportManager.exportReportToPdfFile(print, "informe.pdf");
			// Abre el archivo PDF generado
			File path = new File("informe.pdf");
			Desktop.getDesktop().open(path);
		}

		catch (Exception e)
		{
			JOptionPane.showMessageDialog(null, e.toString(), "Error", JOptionPane.WARNING_MESSAGE);
		}

	}

}
```

**Objeto ventana que realiza la accion de generar informe**:
```java
package jasperInforme.jasperInforme;

import java.awt.EventQueue;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.border.EmptyBorder;

public class Ventana extends JFrame
{

	private static final long serialVersionUID = 1L;
	private JPanel contentPane;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args)
	{
		EventQueue.invokeLater(new Runnable() {
			public void run()
			{
				try
				{
					Ventana frame = new Ventana();
					frame.setVisible(true);
				} catch (Exception e)
				{
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	public Ventana()
	{
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 450, 300);
		contentPane = new JPanel();
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));

		setContentPane(contentPane);

		JButton btnNewButton = new JButton("Keroro");
		btnNewButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e)
			{

				// Accion que realiza el boton.
				Pedidos informe = new Pedidos();
				String ciudad = "Barcelona";
				informe.ejecutar(ciudad);

			}
		});
		contentPane.add(btnNewButton);
	}

}
```


