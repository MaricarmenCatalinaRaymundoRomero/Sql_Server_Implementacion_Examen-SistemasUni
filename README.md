# Sql_Server_Implementacion_Examen-SistemasUni
### DOCUMENTO QUE DEJO EL PROFESOR
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/f8a2c002-5d70-4b80-8377-bae533c18f71)



# PROYECTO QUE REALICE

[ManualImplementacionRaymundoRomero.pdf](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/files/12223210/ManualImplementacionRaymundoRomero.pdf)


#### ANALISIS
- Primero lo que ise es ver el diagrama y analizar de que se trata el base de datos.
- El diagrama era de una venta o tienda. 
- Las tablas son:
    * Categoría
    * Producto
    * Empleado
    * Venta
    * Distrito
    * Cliente
- Utilice un programa para la creación del diagrama (yed) para así poder guiarme. Cada tabla les agregue mi apellido al costado como me pidió. También agregue algunos errores en escribir para poder utilizar la sentencia DML.
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/7cd70ddd-b0b5-4f8d-a24e-9327616a82bc)

## LA CREACION DE LAS TABLAS 
- Creamos nuestra base de datos con el nombre “BDFINALRAYMUNDO”.
- Recordemos que al momento de hacer las tablas y que tenga una relación. Primero tenemos que crear las tablas exteriores. Las tablas exteriores son CategoriaRaymundo, EmpleadoRaymundo y DistritoRaymundo.

```
create table CategoriaRaymundo
(--inicio de la tabla
CodCat int,
NomCat varchar(30),
DesCat varchar(50),
FotCat text--FotCat image
)--final de la tabla

create table EmpleadoRaymundo
(--inicio de la tabla
CodEmp int,
NomEmp varchar(30),
ApaEmp varchar(40),
AmaEmp varchar(40),
DniEmp int,
Whatsapp varchar,--WhaEmp int
FotoEmpleado int,--FotEmp image
GenEmp bit,
FnaEmp int
)--final de la tabla

create table DistritoRaymundo
(--inicio de la tabla
CodDis int,
NombredelDistrito varchar(300),--NomDis varchar(30)
DesDis varchar(50)
)--final de la tabla
```

- 
•	Después de crear las tablas exteriores, continuamos con las demás tablas que son ClienteRaymundo y ProductoRaymundo.
Pero no la tabla de VentaRaymundo porque al momento de crearlo lo vamos a relacionar con dos tablas inmediatamente que son
ClienteRaymundo y ProductoRaymundo. Eso lo dejamos al final.

```
create table ClienteRaymundo
(--inicio de la tabla
CodCli int, 
NomCli int,--varchar(30) 
ApaCli varchar(40),
AmaCli varchar(40),
FnaCli date,
FotCli image,
WhaCli int,
DniCli int,
GenCli bit,
CodDis int---
)--final de la tabla


create table ProductoRaymundo 
(--inicio de la tabla
CodPro int,
Nombre varchar(30),--NomPro varchar(30)--LISTOO
DesPro varchar(40),
PrePro int,
CodCat int---
)--final de la tabla

```

- Ejecutamos las dos tablas.
- Ahora vamos a utilizar la sentencia DML porque en nuestra tabla tenemos muchos errores que corregir.
- Primero corregimos la tabla CategoriaRaymundo. 
- Vemos que el atributo CodCat no tiene un primary key, asi que lo vamos agregar, pero primero lo vamos a eliminar y luego agregar.

```
---------------------------------------------------------
----------CORREGIR LA TABLA ""CategoriaRaymundo""----------      
---------------------------------------------------------
--ELIMINAR "CodCat int"
   alter table CategoriaRaymundo--Que Objeto(Tabla)
   drop column CodCat--Que Accion (Eliminar)  
--AGREGAR " CodCat int primary key identity (20280001,1)"
   alter table CategoriaRaymundo--Que Objeto(Tabla)
   add CodCat int primary key identity (20280001,1)
---------------------------------------------------------
```

- La consulta "alter table CategoriaRaymundo add CodCat int primary key identity (20280001,1)" realiza
  la acción de agregar una columna llamada "CodCat" a la tabla "CategoriaRaymundo". El tipo de dato de
  la columna es "int" y se define como una clave primaria utilizando la propiedad "primary key". Además,
  se utiliza la propiedad "identity" para generar valores automáticamente para esta columna.
- El primer valor generado será 20280001 y se incrementará en 1 para cada nueva fila insertada.
- Esto asegurará que cada valor en la columna "CodCat" sea único y se utilice como clave primaria. 
- El atributo FotCat tiene la identidad incorrecta, debería ser image. Asi que vamos a corregirlo.
- Primero eliminamos y después agregamos. 

```
--ELIMINAR "FotCat text" 
   alter table CategoriaRaymundo--Que Objeto(Tabla)
   drop column FotCat--Que Accion (Eliminar) 
--AGREGAR "FotEmp image default'C:\Users\Administrator\Desktop\img\SinFoto.jpg"
   alter table CategoriaRaymundo--Que Objeto(Tabla)
   add FotCat image default'C:\Users\Administrator\Desktop\img\SinFoto.jpg'--Que Accion(Adicionar)
---------------------------------------------------------
```

- La consulta "alter table CategoriaRaymundo add FotCat image default 'C:\Users\Administrator\Desktop\img\SinFoto.jpg'"
  realiza la acción de agregar una columna llamada "FotCat" a la tabla "CategoriaRaymundo".
- El tipo de dato de la columna es "image" y se establece un valor predeterminado utilizando
  la ruta de la imagen 'C:\Users\Administrator\Desktop\img\SinFoto.jpg'. Esto significa que,
  si no se proporciona un valor al insertar datos en la tabla, se utilizará automáticamente la imagen especificada como valor predeterminado.
- Ya tenemos corregido de la tabla CategoriaRaymundo, asi que vamos verificarlo si tiene las restricciones que añadimos y los tipos.


![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/9d9a0bed-5232-4f92-a481-faaf6f18ab69)

- Ahora corregiremos la tabla EmpleadoRaymundo porque tiene varios errores y también falta añadir algunas restricciones.
- En el atributo “CodEmp int” falta añadir primary key, lo vamos a eliminar y lo agregamos con la entidad correcta.
```
---------------------------------------------------------
----------CORREGIR LA TABLA ""EmpleadoRaymundo""----------      
---------------------------------------------------------
--ELIMINAR "CodEmp int"
    alter table EmpleadoRaymundo--Que Objeto(Tabla)
	drop column CodEmp--Que Accion (Eliminar)  
--AGREGAR " CodEmp int primary key identity (20260001,1)"
	alter table EmpleadoRaymundo--Que Objeto(Tabla)
	add  CodEmp int primary key identity (20260001,1)
```

- La consulta "alter table EmpleadoRaymundo add CodEmp int primary key identity (20260001,1)"
  realiza la acción de agregar una columna llamada "CodEmp" a la tabla "EmpleadoRaymundo".
  El tipo de dato de la columna es "int" y se define como una clave primaria utilizando la propiedad
  "primary key". Además, se utiliza la propiedad "identity" para generar valores automáticamente
  para esta columna. El primer valor generado será 20260001 y se incrementará en 1 para cada nueva
  fila insertada. Esto asegurará que cada valor en la columna "CodEmp" sea único y se utilice como clave primaria.

- En el atributo DniEmp, voy a agregarle una restricción.
```
---------------------------------------------------------
--AGREGAR "DniEmp" UNA RESTRICCION
	alter table EmpleadoRaymundo--Que Objeto(Tabla)
	add check(DniEmp>=900000000 and DniEmp<=999999999)
---------------------------------------------------------
```

- La consulta "alter table EmpleadoRaymundo add check(DniEmp>=900000000 and DniEmp<=999999999)" realiza la acción
  de agregar una restricción de verificación (check constraint) a la tabla "EmpleadoRaymundo". Esta restricción
  asegura que los valores en la columna "DniEmp" cumplan con la condición especificada, donde el DNI se encuentre
  en el rango válido de 900 000 000 a 999 999 999. Si se intenta insertar un valor que no cumpla con esta condición,
  se mostrará un mensaje de error indicando que el valor del DNI no es válido.
- En el atributo Whatsapp, esta mal escrita porque debería estar las tres primeras letras de la tabla y
  del atributo especifico. Asi que vamos a eliminar y agregar. También añadiremos una restricción.

```
---------------------------------------------------------
--ELIMINAR " Whatsapp varchar" 
    alter table EmpleadoRaymundo--Que Objeto(Tabla)
	drop column Whatsapp--Que Accion (Eliminar) 
--AGREGAR " WhaEmp int"
	alter table EmpleadoRaymundo--Que Objeto(Tabla)
	add WhaEmp int--Que Accion(Adicionar)
--AGREGAR " WhaEmp " UNA RESTRICCION
	alter table EmpleadoRaymundo--Que Objeto(Tabla)
	add check(WhaEmp>=900000000 and WhaEmp<=999999999)
---------------------------------------------------------

```

- La consulta "alter table EmpleadoRaymundo add WhaEmp int" realiza la acción de
  agregar una nueva columna llamada "WhaEmp".
- La consulta "alter table EmpleadoRaymundo add check (WhaEmp>=900000000 and WhaEmp<=999999999)" realiza la
  acción de agregar una restricción de verificación (check constraint) a la columna "WhaEmp" en la tabla
  "EmpleadoRaymundo". Esta restricción asegura que los valores en la columna "WhaEmp" cumplan con la condición especificada,
  que el valor de "WhaEmp" esté en el rango válido de 900 000 000 a 999 999 999.

- El atributo FotoEmpleado, está mal escrita porque debería estar las tres primeras letras de la tabla
  y del atributo especifico. El tipo de dato debería ser image. También le voy a agregar una restricción.
```
---------------------------------------------------------
--ELIMINAR "FotoEmpleado int" 
   alter table EmpleadoRaymundo--Que Objeto(Tabla)
   drop column FotoEmpleado--Que Accion (Eliminar) 
--AGREGAR "FotEmp image default'C:\Users\Administrator\Desktop\img\SinFoto.jpg"
   alter table EmpleadoRaymundo--Que Objeto(Tabla)
   add FotEmp image default'C:\Users\Administrator\Desktop\img\SinFoto.jpg'--Que Accion(Adicionar)

```

- La consulta "alter table EmpleadoRaymundo add FotEmp image default 'C:\Users\Administrator\Desktop\img\SinFoto.jpg'"
  realiza la acción de agregar una columna llamada "FotEmp" a la tabla "EmpleadoRaymundo".
  El tipo de dato de la columna es "image" y se establece un valor predeterminado utilizando la ruta de la imagen
  'C:\Users\Administrator\Desktop\img\SinFoto.jpg'. Esto significa que, si no se proporciona un valor al
  insertar datos en la tabla, se utilizará automáticamente la imagen especificada como valor predeterminado.
- El atributo FnaEmp, tiene el tipo de dato incorrecto porque el tipo de fecha debe ser date. también le
  vamos agregar una restricción.
```
---------------------------------------------------------
--ELIMINAR "FnaEmp int"
    alter table EmpleadoRaymundo--Que Objeto(Tabla)
	drop column FnaEmp--Que Accion (Eliminar)  
--AGREGAR " FnaEmp date"
	alter table EmpleadoRaymundo--Que Objeto(Tabla)
	add  FnaEmp date
---------------------------------------------------------
--AGREGAMOS EN "FnaEmp" UNA RESTRICCION
	alter Table EmpleadoRaymundo--Que Objeto(Tabla)
	add check(FnaEmp<=getdate())--Que acción (Adicionar)
```
- La consulta "alter table EmpleadoRaymundo add FnaEmp date" realiza la acción de agregar una nueva columna
  llamada "FnaEmp" a la tabla "EmpleadoRaymundo".
- La consulta "alter Table EmpleadoRaymundo add check(FnaEmp<=getdate())" realiza la acción de agregar una
  restricción de verificación (check constraint) a la columna "FnaEmp" en la tabla "EmpleadoRaymundo".
  Esta restricción asegura que los valores en la columna "FnaEmp" cumplan con la condición especificada,
  que la fecha de nacimiento (FnaEmp) sea menor o igual a la fecha actual (getdate()).
- Ya tenemos corregido de la tabla EmpleadoRaymundo, asi que vamos verificarlo si tiene las restricciones
  que añadimos y los tipos.

![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/fed11767-20ed-4a64-8a2c-b08c3b76e09c)


- Ahora corregiremos la tabla DistritoRaymundo porque tiene varios errores y también falta añadir algunas restricciones.
```
---------------------------------------------------------
----------CORREGIR LA TABLA ""DistritoRaymundo""----------      
---------------------------------------------------------
--ELIMINAR "CodDis int"
    alter table DistritoRaymundo--Que Objeto(Tabla)
	drop column CodDis--Que Accion (Eliminar)  
--AGREGAR " CodDis int primary key identity"
	alter table DistritoRaymundo--Que Objeto(Tabla)
	add  CodDis int primary key identity (20240001,1)
---------------------------------------------------------
```
- La consulta "alter table DistritoRaymundo add CodDis int primary key identity (20240001,1)"
  realiza la acción de agregar una columna llamada " CodDis " a la tabla " DistritoRaymundo ".
  El tipo de dato de la columna es "int" y se define como una clave primaria utilizando la propiedad
  "primary key". Además, se utiliza la propiedad "identity" para generar valores automáticamente para esta columna.
  El primer valor generado será 20240001 y se incrementará en 1 para cada nueva fila insertada.
  Esto asegurará que cada valor en la columna " CodDis" sea único y se utilice como clave primaria.
- Ahora vamos relacionar la tabla CategoriaRaymundo porque tiene una relación uno a muchos con la
  entidad ProductoRaymundo. Un producto pertenece a una categoría, y una categoría puede tener muchos productos.
- Así que vamos a utilizar este comando.
```
--RELACION---

   alter table ProductoRaymundo--Que Objeto(Tabla)ORIGEN
   add foreign key(CodCat) references CategoriaRaymundo--Que Accion(Relacionar y/o Referenciar)DESTINO

```

- Ahora vamos a relacionar la tabla DistritoRaymundo porque tiene una relación uno a muchos con la entidad ClienteRaymundo.
  Un distrito puede tener varios clientes, pero un cliente reside en un solo distrito.
- Así que vamos a utilizar este comando.
```
--RELACION---
	
    alter table ClienteRaymundo--Que Objeto(Tabla)ORIGEN
    add foreign key(CodDis) references DistritoRaymundo--Que Accion(Relacionar y/o Referenciar)DESTINO
```

- Por último, creamos la tabla Venta para que podamos relacionar inmediatamente con las dos tablas que son
  ClienteRaymundo y ProductoRaymundo. También agregue una restricción al CodVen.
```
create table VentaRaymundo 
(--inicio de la tabla
CodVen int primary key identity (20290001,1),
ProVen varchar(30),
CnoVen varchar(30),
CapVen varchar(40),
CamVen varchar(30),
CodEmp int,
CodCli int references ClienteRaymundo,
CodPro int references ProductoRaymundo
)--final de la tabla
```
- Finalmente vamos relacionar la tabla EmpleadoRaymundo porque tiene una relación uno a muchos con la entidad VentaRaymundo.
  Un empleado puede realizar varias ventas, pero una venta está asociada a un solo empleado.
- Asi que vamos a utilizar este comando.

```
--RELACION---
	
   alter table VentaRaymundo--Que Objeto(Tabla)ORIGEN
   add foreign key(CodEmp) references EmpleadoRaymundo--Que Accion(Relacionar y/o Referenciar)DESTINO
```

# ASI QUEDA NUESTRO DIAGRAMA BDFINALRAYMUNDO!
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/8c4eca65-064e-47e3-bffb-d37d769c6c81)


### AHORA INSERTAREMOS DATOS A CADA TABLA

- La tabla CategoriaRaymundo le vamos agregar 9 datos.
```
insert CategoriaRaymundo(NomCat,DesCat)
values('Embutidos/Quesos', 'Jamonadas, Pates y Quesos'),('Juguetes', 'Muñecas, Coches, Lego y Carros'),('Libros', 'Romance, Terror, Comedia, Misterio y Cocina'),('Ropa', 'Polo, Pantalon, Falda, Vestido y Camisa'),('Bebidas', 'Gaseosa, Agua, Alcohol, Energizantes y Cervezas')

insert CategoriaRaymundo(NomCat,DesCat)
values('Electrodoméstico', 'Televisores, Refrigeradoras y Equipos de Sonido'),('Frutas', 'Frutas de Estacion')

insert CategoriaRaymundo(NomCat,DesCat)
values('Abarrotes', 'Viveres y/o alimentos envasados'),('Informatica', 'Impresoras, Laptops, Suministros y Partes')
```

- Aquí utilice este comando para poder ver la tabla CategoriaRaymundo  y sus datos.
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/bea085be-1fe4-4920-bcc3-106b1cb8c607)

- La tabla EmpleadoRaymundo le vamos agregar 9 datos.
```
--TABLA EMPLEADORAYMUNDO---

insert EmpleadoRaymundo (NomEmp, ApaEmp, AmaEmp, DniEmp, WhaEmp, GenEmp, FnaEmp)
values('Juan', 'García', 'Pérez', 912345678, 912345678, 0, '1990-01-15'),('María', 'López', 'Gómez', 923456789, 923456789, 1, '1992-05-20'),('Pedro', 'Martínez', 'Rodríguez', 934567890, 934567890, 0, '1995-08-10')
    
insert EmpleadoRaymundo (NomEmp, ApaEmp, AmaEmp, DniEmp, WhaEmp, GenEmp, FnaEmp)
values('Laura', 'Hernández', 'Sánchez', 945678901, 945678901, 1, '1998-02-28'),('Carlos', 'González', 'Lara', 956789012, 956789012, 0, '1994-11-12'),('Ana', 'Torres', 'Vargas', 967890123, 967890123, 1, '1991-07-05'),('Luis', 'Ramírez', 'Morales', 978901234, 978901234, 0, '1997-03-25')

insert EmpleadoRaymundo (NomEmp, ApaEmp, AmaEmp, DniEmp, WhaEmp, GenEmp, FnaEmp)
values('Sofía', 'Soto', 'Flores', 989012345, 989012345, 1, '1993-09-17'),('Diego', 'Ortega', 'Guerrero', 990123456, 990123456, 0, '1996-06-08')
```
- Aquí utilice este comando para poder ver la tabla EmpleadoRaymundo y sus datos.

![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/d5b46fb5-858d-4207-b701-cfd1e4b3eef9)

- La tabla DistritoRaymundo le vamos agregar 9 datos.
```
--TABLA DISTRITORAYMUNDO

insert  DistritoRaymundo (NomDis, DesDis)
values('Miraflores', 'Distrito turístico')

insert  DistritoRaymundo (NomDis, DesDis)
values('San Isidro', 'Distrito financiero'),('Barranco', 'Distrito bohemio y artístico ubicado en Lima')

insert  DistritoRaymundo (NomDis, DesDis)
values('San Borja', 'Distrito residencial'),('Surco', 'Distrito comercial ubicado en Lima.'),('Callao', 'Ubicado en la costa central de Perú.')
    
insert  DistritoRaymundo (NomDis, DesDis)
values('Chorrillos', 'Distrito costero ubicado en Lima.'),('La Molina', 'Distrito residencial y universitario.'),('Lince', 'Distrito céntrico y residencial.')
```
- Aquí utilice este comando para poder ver la tabla DistritoRaymundo y sus datos.
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/2a9e8b56-c907-449d-aae1-95c25383e963)

- La tabla ClienteRaymundo le vamos agregar 9 datos.
```
---TABLA CLIENTERAYMUNDO

insert ClienteRaymundo (NomCli, ApaCli, AmaCli, FnaCli, WhaCli, DniCli, GenCli, CodDis)
values('Martha', 'Zuñiga', 'Pérez', '1990-01-15', 912345678, 902349988, 0, 20240003),('Stiven', 'López', 'Entrada', '1992-05-20', 923456789, 922455599, 1, 20240005),('Larry', 'Rios', 'Farias', '1995-08-10', 934567890, 938867890, 0, 20240011)
    
insert ClienteRaymundo (NomCli, ApaCli, AmaCli, FnaCli, WhaCli, DniCli, GenCli, CodDis)
values('Helen', 'Chau', 'Romero', '1998-02-28', 945678901, 999678801, 1, 20240012),('Carlos', 'González', 'Lara', '1994-11-12', 956789012, 957777012, 0, 20240014),('Abigail', 'Torres', 'Vargas', '1991-07-05', 967890123, 967890123, 1, 20240015),('Leonardo', 'Caja', 'Morales', '1997-03-25', 978901234, 975551234, 0, 20240006),('Julieta', 'Leon', 'Acosta', '1993-09-17', 989012345, 900012225, 1, 20240006),('Mathias', 'Baldeon', 'Campos', '1996-06-08', 990123456, 955663226, 0, 20240010)
```
- Aquí utilice este comando para poder ver la tabla ClienteRaymundo y sus datos.
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/01aa0db5-f36a-4bbe-8ebd-e29b42e48a46)

- La tabla ProductoRaymundo le vamos agregar 9 datos.
```
insert ProductoRaymundo (NomPro, DesPro, PrePro, CodCat)
values('Agua San Mateo de 1.5L', 'La más ecológica', 12.99, 20280005),('Lavadora LG 16KG', 'Dura mas tiempo que los demas', 225.99, 20280006)
    
	
insert ProductoRaymundo (NomPro, DesPro, PrePro, CodCat)
values('Polo Adiddas', 'Buena calidad para los demas.', 55.99, 20280004),('Muñeca Sirenita', 'Tiene unas aletas de colores', 29.99, 20280002),('Manzana Roja', 'Tiempo de comer saludable.', 4.99, 20280007),('Mandarina', 'Delicioso y sin pepas.', 3.99, 20280007)
    
insert ProductoRaymundo (NomPro, DesPro, PrePro, CodCat)
values('Energizante RED BULL 250ml', 'Buena para el deporte.', 8.99, 20280005),('Aceite CAPRI  1L', 'Calidad vegetal.', 7.99, 20280008),('Chirimoya Cumbe', 'Tiempo de comer dulce.', 2.99, 20280007)
```

- Aquí utilice este comando para poder ver la tabla ProductoRaymundo y sus datos.
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/4fe37f1c-2f12-483d-9f88-d11d263d0d35)

- La tabla VentaRaymundo le vamos agregar 9 datos.
```
----TABLA VENTARAYMUNDO

insert VentaRaymundo (ProVen, CnoVen, CapVen, CamVen, CodEmp, CodCli, CodPro)
values('Mandarina', 'Leonardo', 'Caja', 'Morales', 20260006, 20230004, 20270007),('Manzana Roja', 'Martha', 'Zuñiga', 'Pérez', 20260008, 20230001, 20270006),('Aceite CAPRI  1L', 'Abigail', 'Torres', 'Vargas', 20260009, 20230006, 20270012)

insert VentaRaymundo (ProVen, CnoVen, CapVen, CamVen, CodEmp, CodCli, CodPro)
values('Chirimoya Cumbe', 'Leonardo', 'Caja', 'Morales', 20260006, 20230004, 20270013),('Mandarina', 'Martha', 'Zuñiga', 'Pérez', 20260006, 20230001, 20270007),('Lavadora LG 16KG', 'Martha', 'Zuñiga', 'Pérez', 20260009, 20230001, 20270003),('Agua San Mateo de 1.5L', 'Leonardo', 'Caja', 'Morales', 20260008, 20230004, 20270002),('Agua San Mateo de 1.5L', 'Abigail', 'Torres', 'Vargas', 20260009, 20230006, 20270002)
    
insert VentaRaymundo (ProVen, CnoVen, CapVen, CamVen, CodEmp, CodCli, CodPro)
values('Energizante RED BULL 250ml', 'Julieta', 'Leon', 'Acosta', 20260001, 20230008, 20270011),('Polo Adiddas', 'Julieta', 'Leon', 'Acosta', 20260001, 20230008, 20270004),('Agua San Mateo de 1.5L', 'Larry', 'Rios', 'Farias', 20260002, 20230003, 20270002),('Muñeca Sirenita', 'Larry', 'Rios', 'Farias', 20260002, 20230003, 20270005),('Muñeca Sirenita', 'Mathias', 'Baldeon', 'Campos', 20260006, 20230009, 20270005),('Energizante RED BULL 250ml', 'Mathias', 'Baldeon', 'Campos', 20260006, 20230009, 20270011)
    
insert VentaRaymundo (ProVen, CnoVen, CapVen, CamVen, CodEmp, CodCli, CodPro)
values('Aceite CAPRI  1L', 'Carlos', 'González', 'Lara', 20260006, 20230005, 20270012),('Agua San Mateo de 1.5L', 'Carlos', 'González', 'Lara', 20260009, 20230005, 20270002),('Lavadora LG 16KG', 'Stiven', 'López', 'Entrada', 20260001, 20230002, 20270003),('Manzana Roja', 'Stiven', 'López', 'Entrada', 20260001, 20230002, 20270006),('Polo Adiddas', 'Stiven', 'López', 'Entrada', 20260009, 20230002, 20270004),('Muñeca Sirenita', 'Stiven', 'López', 'Entrada', 20260002, 20230002, 20270005)

```
- Aquí utilice este comando para poder ver la tabla VentaRaymundo y sus datos.
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/4737c9c2-0980-4d6c-9ede-1b83e6c9c9f3)

## CONSULTA 
- Lo primero para hacer la consulta es ver mis tablas mediante con el diagrama que tengo. Entonces vi que hay 4 tablas relacionadas a la consulta pedido. Respondí estas preguntas para poder realizar la consulta.
```
-----------------------------------------------------------------------
--LISTA DE CONSULTAS
--1. Una consulta de los nombres de los clientes, codigo del producto, precio del producto y el nombre del empleado

--Que tablas son?
ClienteRaymundo, VentaRaymundo, ProductoRaymundo, EmpleadoRaymundo
--Están relacionadas?
si
--Cuáles son las columnas en común?
CodPro, CodCli
--Unir y Habilitar la columna en común?

select ClienteRaymundo.NomCli as Nombre, ProductoRaymundo.PrePro as Precio, ProductoRaymundo.CodCat as CodigoProducto, EmpleadoRaymundo.NomEmp as Empleado
from ClienteRaymundo
JOIN VentaRaymundo 
on ClienteRaymundo.CodCli = VentaRaymundo.CodCli
JOIN ProductoRaymundo
on VentaRaymundo.CodPro = ProductoRaymundo.CodPro
JOIN EmpleadoRaymundo
on VentaRaymundo.CodEmp = EmpleadoRaymundo.CodEmp
```
- Resultado del comando realizado.  
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/11072945-2e95-4c50-bd68-94502c864c1c)

# PA
- Este comando ejecutará el procedimiento almacenado y mostrará los registros de ClienteRaymundo en la tabla especificada. 

```
	--Crear PA para listar los Clientes
    create proc PAListarClienteNombre
	as
	begin --inicia
	--debemos utilizar cualquier comando SQL
	select*
	from ClienteRaymundo

	end--termina el PA

	--Luego de crear para ejecutar
	exec PAListarClienteNombre

```

- Esto es el resultado de “PAListarClienteNombre”

![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/a4f2fa95-2798-496a-85c0-a35e227b4b21)

- El código que muestra, es  una alteración del procedimiento almacenado "PAListarClienteNombre".
  En esta versión modificada, se ha agregado un parámetro llamado "@Nom" de tipo varchar(20).
  Luego, se utiliza este parámetro en la cláusula WHERE de la consulta SELECT para filtrar los
  resultados de la tabla "ClienteRaymundo" según el nombre de cliente ingresado.
```
	alter proc PAListarClienteNombre
	@Nom varchar(20)--Ingresamos el parametro 
	as
	begin --inicia el PA
	--debemos utilizar cualquier comando SQL
	select*
	from ClienteRaymundo
	where NomCli =@Nom
	end--termina el PA

	--Ejecutamos el PA e ingreando el WhaCli
	exec PAListarClienteNombre
```
- Esto ejecutará el procedimiento almacenado "PAListarClienteNombre" con el valor proporcionado para el parámetro "@Nom", y mostrará los registros de clientes que cumplan con el filtro.
```
	--Para mostrar el contenido de un PA
	sp_helptext PAListarClienteNombre
```
![image](https://github.com/MaricarmenCatalinaRaymundoRomero/Sql_Server_Implementacion_Examen-SistemasUni/assets/129924045/0c404c54-ee02-4002-85cb-ab73c02479f4)

- Para eliminar un procedimiento almacenado, se utiliza la instrucción DROP PROCEDURE. En este caso para eliminar el procedimiento almacenado "PAListarCliente", este código es:
```
--COMO ELIMINAR
		drop proc PAListarCliente
```








