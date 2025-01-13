# 📌 Jasper.
Jasper es una herramienta que permite realizar informes atacando un origen de datos. 


La pantalla de bienvenida.
![image](https://github.com/user-attachments/assets/679bf7b1-fbf3-4dc7-82e0-0f035c1581b2)

# Pruebas de funcionamiento.
Pinchando en get started nos llevará a esta pantalla.
![image](https://github.com/user-attachments/assets/85544fff-6540-4f04-9ea6-2cd4f7940351)

pinchando en sample DB y pinchamos en text.
![image](https://github.com/user-attachments/assets/44e1fefa-6051-471a-acc7-085e66e484a0)

![image](https://github.com/user-attachments/assets/75a695bc-23e1-4b8a-bb10-226bf57b698c)

#  Creando el primer informe.
![image](https://github.com/user-attachments/assets/7ce4f726-c2ed-4fc5-bf0b-9dae96595969)

![image](https://github.com/user-attachments/assets/f71ed214-f111-49aa-a356-cb5a0fbfb656)

este está mal, hay que poner el nombre abajo y arriba es donde se guarda el fichero.
![image](https://github.com/user-attachments/assets/0dff713a-7e79-4750-9087-fe2b892e76a8)


# Alimentar la tabla.
![image](https://github.com/user-attachments/assets/9acb88e0-43ac-43d0-bb1f-b1801e040ad5)

enganchar con el origen
![image](https://github.com/user-attachments/assets/30c80ce2-0dd5-4af9-98a5-edaa0c921c85)

crea la query
![image](https://github.com/user-attachments/assets/81651fa9-149e-4b18-926c-109e4a384b8d)

pincha en read fields
![image](https://github.com/user-attachments/assets/d665a01d-6098-4ee1-a3c7-7ad606e866dd)

![image](https://github.com/user-attachments/assets/9ff118d2-1846-4d20-8637-321548a5958f)



##Partes de un informe.
![image](https://github.com/user-attachments/assets/6c77b54f-c7d0-4d3f-8a5c-5240708f567b)

- Cabecera
Un elemento que aparece una unica vez en todo el informe, sin importar la cantidad de paginas que genera el informe.
Como su nombre indica ocupa la parte superior del informe.

- Summary
Elemento que aparece una unica vez en todo el informe. sin importar la cantidad de paginas que genera el informe.
Representa 



![image](https://github.com/user-attachments/assets/71a5816e-fbed-484d-849f-dd78a6dec2b3)



## Introducir elementos en informe.

![image](https://github.com/user-attachments/assets/d7585517-08e9-4111-a125-e95ddacc50e7)

![image](https://github.com/user-attachments/assets/39222eff-e100-4d6f-9dd8-8846e971258b)

![image](https://github.com/user-attachments/assets/76c6d727-8371-4908-9fdd-ed89b569804c)


# Ver pedidos por parametros.
Vamos a crear un nuevo parametro, como un parametro de pedido por ciudad.
![image](https://github.com/user-attachments/assets/b37b2665-af13-4113-8435-07631e8aa673)

![image](https://github.com/user-attachments/assets/a4e2a17f-c2db-4131-949f-9d2c0fe8d821)

is for prompting ?
si.
Default value es el valor si no recibe nada el parametro.

pinchando en guardar aparecera el nuevo parametro.

![image](https://github.com/user-attachments/assets/3bf3411c-fabe-4e2a-9feb-2c1a89c7c092)

Ahora debemos crear la query que utilice el parametro creado, en este caso Parameter1.
```sql
SELECT * FROM ORDERS WHERE "SHIPCITY" = $P{Parameter1}
```
![image](https://github.com/user-attachments/assets/11480495-ed96-445c-8595-162026984cbe)

![image](https://github.com/user-attachments/assets/79362222-fb83-4fe9-85e2-b8e43334d9d7)

# Crear grupos de datos.
>[!CAUTION]
>ES DE VITAL IMPORTANCIA ORDENAR LOS RESULTSETS ANTES DE AGRUPAR. SORT -> GROUP. de lo contrario se creará un nuevo grupo con cada cambio de nombre del campo discriminador..

![image](https://github.com/user-attachments/assets/4964ccd2-504e-4b38-845f-d241641bee4c)

![image](https://github.com/user-attachments/assets/f0e4612b-c2cf-4f2b-9b94-3569d11e19d1)

![image](https://github.com/user-attachments/assets/78e0f31b-15ed-4d6d-9ad7-9add213b0561)

![image](https://github.com/user-attachments/assets/43f1cbc6-263c-446e-9801-e7c3967fd721)

![image](https://github.com/user-attachments/assets/b2c3f791-d1dd-455a-a0e9-770673bfed85)

![image](https://github.com/user-attachments/assets/7dd5b31b-c036-4263-be17-e40eb07f7f6a)


# VARIABLES

![image](https://github.com/user-attachments/assets/b2723ec0-4c5c-4970-97ee-cf0c31b5646e)

![image](https://github.com/user-attachments/assets/6eb56692-8107-4905-a439-9449dd4b3167)

Es importante observar el tipo de reinicio y el tipo de incremento.
![image](https://github.com/user-attachments/assets/25c698d8-6c39-4430-b2eb-15a08e744cc9)
   
---
   
tiempo de evaluacion.
![image](https://github.com/user-attachments/assets/cc9b9173-b23f-4c0f-8ed2-4347557960a8)

configurar el tiempo de evaluacion de la variable.
![image](https://github.com/user-attachments/assets/93a4c456-3f0f-4a84-9d2c-17eaa19293de)

![image](https://github.com/user-attachments/assets/55c71407-b9a4-456c-bf22-48c6f2da6b0c)

---
   
