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
