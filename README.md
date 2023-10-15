# Maven:
Ahora las librerias son llamadas dependencias

Luego de agregar algo, es necesario guardar los cambios(Load Maven Changes)

![image](https://github.com/Pierohc/JDBC/assets/133154904/668896c2-faa9-4709-9b81-6cbafec56fd9)

# Agregar dependencias:

https://mvnrepository.com/artifact/com.mysql/mysql-connector-j/8.0.33

![image](https://github.com/Pierohc/JDBC/assets/133154904/dd48281e-b6ae-497e-b489-6bcf3f954eb5)

# Driver:
Ubicacion:

![image](https://github.com/Pierohc/JDBC/assets/133154904/9f1c76cf-8576-41de-a7b9-2bfe45214894)


![image](https://github.com/Pierohc/JDBC/assets/133154904/24f082f9-5dd0-47e0-a168-ac22ebb402b8)

---------

Igual debemos declarar la libreria en el main para conectarnos a sql a traves del driver y agregar un try catch:

![image](https://github.com/Pierohc/JDBC/assets/133154904/7c432e16-132b-4a9a-9eae-25f672281e9a)

-----------------

# Parametros de conexión:

-URL de conexión

-Usuario

-Password

![image](https://github.com/Pierohc/JDBC/assets/133154904/31748286-be79-4514-b19b-ce376b82569f)

![image](https://github.com/Pierohc/JDBC/assets/133154904/ece77ff3-9668-44a1-be17-8822bd587ec5)

-----------------------------

# Conexión:

Saldra un error y par solucionarlo debemos agregar una variable local y debemos asegurranos que se importar "import java.sql.Connnection"

![image](https://github.com/Pierohc/JDBC/assets/133154904/d15338df-7bc3-41e0-8ce2-87c53ed021ad)

Igualmente agregando la variable saldra un error en getConnection por lo que debemos agregar un try catch

![image](https://github.com/Pierohc/JDBC/assets/133154904/72f59f46-9b01-4368-bdae-71b693bd7955)

# Añadimos el encargado de llevar nuestra sentencia de JAVA a SQL:

![image](https://github.com/Pierohc/JDBC/assets/133154904/34ea6edd-8042-4fb3-ad4f-3373126da02f)

# Ejecutamos el envio del Query y guardamos lo que nos devolvera con ResultSet en una variable:

![image](https://github.com/Pierohc/JDBC/assets/133154904/3a874242-f64a-48e1-abe2-b28f52ed1d9f)

# rs.next():

Apunta a una tabla vacia inicialmente, luego si devuelve True es que es una tabla con datos 
y si esta vacía devuelve False. Se considera con datos si la PK tiene valor

Recordar que el recorrido con jdbs es fila por fila, una vez estando en una fila recien puedo acceder a cada columna

Podemos llamar a una columna por numero o por su nombre (2 o "first_name"). Además, cabe resaltar
que dependera tambien del "select *" ya que si en vez de asterisco colocamos
"select salary, first_name", salary seria 1 y first name 2.

![image](https://github.com/Pierohc/JDBC/assets/133154904/295edce6-b34e-4a63-a1cc-46e72ae499ff)

-----------

## Si quiero mostrar todos los empleados:

![image](https://github.com/Pierohc/JDBC/assets/133154904/ee01ee1a-dc00-4da2-9911-5305786f05a0)

## La fecha se puede trabajar como String:

![image](https://github.com/Pierohc/JDBC/assets/133154904/86aecd9a-f5e5-472d-a923-b8f414d24f70)

## Condiciones:
Debemos analizar si es más sencillo filtrar por medio de Java o SQL.

Java:

![image](https://github.com/Pierohc/JDBC/assets/133154904/86287084-8237-4dce-a8e1-0ffe58feb377)

SQL:

![image](https://github.com/Pierohc/JDBC/assets/133154904/01913dc5-72e8-4303-9981-53ef6edc306a)











