Con Prepare Stament:
Usado cuando el usuario ingresa datos. Aqui se creara un trabajo en JobDao y lo agregaremos a la tabla de jobs:

       public void crear(String jobId, String jobTitle, int minSalary,int maxSalary){
    
            try {
                Class.forName("com.mysql.cj.jdbc.Driver");
            }
            catch (ClassNotFoundException e) {
                throw new RuntimeException(e);
            }
    
            String url = "jdbc:mysql://localhost:3306/hr";
            String username = "root";
            String password = "root";
    
    
    
            //Query:
            String sql = "insert into jobs(job_id,job_title,min_salary,max_salary)" +
                    "values(?,?,?,?)";
    
    
            try(Connection conn = DriverManager.getConnection(url, username, password);
                PreparedStatement psmtmt = conn.prepareStatement(sql)) {
                
                
                
                psmtmt.setString(1,jobId);
                psmtmt.setString(2,jobTitle);
                psmtmt.setInt(3,minSalary);
                psmtmt.setInt(4,maxSalary);

                psmtmt.executeUpdate();

            }
            catch (SQLException e) {
                throw new RuntimeException(e);
            }
    
        }

    

Sin Prepare Stament:

    try {
                Class.forName("com.mysql.cj.jdbc.Driver");
            } 
            catch (ClassNotFoundException e) {
                throw new RuntimeException(e);
            }
    
            String url = "jdbc:mysql://localhost:3306/hr";
            String username = "root";
            String password = "root";
    
    
    
            //Query:
            String sql = "select * from employees where employee_id > 148";
    
    
            try(Connection conn = DriverManager.getConnection(url, username, password);
                Statement stmt = conn.createStatement();
                ResultSet rs = stmt.executeQuery(sql)) {
    
    
    
                ///////////////////////////AQUI VA EL CODIGO. EJEMPLO://////////////////////////
               
                while(rs.next()){
    
                    int employeeId = rs.getInt(1 );
                    String firstName = rs.getString("first_name");
                    String hireDate = rs.getString("hire_date");
                    
                    System.out.println("eid:  " + employeeId + " | first_name: " + firstName + " | hd: "+ hireDate);
                }
                ///////////////////////////////////////////////////////////////////////////////
    
    
            } 
            catch (SQLException e) {
                throw new RuntimeException(e);
            }



# Maven:
Ahora las librerias son llamadas dependencias

Luego de agregar algo, es necesario guardar los cambios(Load Maven Changes)

![image](https://github.com/Pierohc/JDBC/assets/133154904/668896c2-faa9-4709-9b81-6cbafec56fd9)

# Agregar dependencias:

https://mvnrepository.com/artifact/com.mysql/mysql-connector-j/8.0.33

    <!-- https://mvnrepository.com/artifact/com.mysql/mysql-connector-j -->
    <dependency>
        <groupId>com.mysql</groupId>
        <artifactId>mysql-connector-j</artifactId>
        <version>8.0.33</version>
    </dependency>

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

![image](https://github.com/Pierohc/JDBC/assets/133154904/e4543acf-c879-4363-946f-0d228a1d666a)

![image](https://github.com/Pierohc/JDBC/assets/133154904/ee01ee1a-dc00-4da2-9911-5305786f05a0)

## La fecha se puede trabajar como String:

![image](https://github.com/Pierohc/JDBC/assets/133154904/86aecd9a-f5e5-472d-a923-b8f414d24f70)

## Condiciones:
Debemos analizar si es más sencillo filtrar por medio de Java o SQL.

Java:

![image](https://github.com/Pierohc/JDBC/assets/133154904/86287084-8237-4dce-a8e1-0ffe58feb377)

SQL:

![image](https://github.com/Pierohc/JDBC/assets/133154904/01913dc5-72e8-4303-9981-53ef6edc306a)

## Librerias que debemos tener:

![image](https://github.com/Pierohc/JDBC/assets/133154904/223c1b46-130c-459f-b9df-2f8588c453cc)

## Problemas con la zona horaria:

Solo será necesario colocarlo si nos sale el error mostrado.

![image](https://github.com/Pierohc/JDBC/assets/133154904/a31ab9bf-68f9-47dc-8dbc-6484b708c3b9)

## Cerrar una conexion a la base de datos:

Podemos usar try con recursos que tengan close, o sea que sean la creacion de objetos.

![image](https://github.com/Pierohc/JDBC/assets/133154904/0ec8572d-e0e4-4da8-b1e0-d80556202983)


## Agregar base de datos al IDDE:

![image](https://github.com/Pierohc/JDBC/assets/133154904/c7d4f09b-4d08-460d-98e8-9f4fe7f3f3f2)

![image](https://github.com/Pierohc/JDBC/assets/133154904/4694df7b-c340-42ed-b7de-2b1fb56b8801)

Abrir una consola:

![image](https://github.com/Pierohc/JDBC/assets/133154904/6bd36fe0-3faf-4831-820d-fc71adf21823)


## Guardar información:

Creamos la clase con el sufijo DAO(Data Access Object), es todo lo que tendran que ver con base
de datos:

![image](https://github.com/Pierohc/JDBC/assets/133154904/db7067d4-8db9-452f-b9e8-9690fc2bc801)

![image](https://github.com/Pierohc/JDBC/assets/133154904/7d52f6b0-9c7d-4c44-a87b-dd88f25a285f)

Otro ejemplo:

![image](https://github.com/Pierohc/JDBC/assets/133154904/70f4839a-d550-4ead-9968-224351f5f01a)

![image](https://github.com/Pierohc/JDBC/assets/133154904/5d9d4a80-156e-4596-9731-9751cbb41c80)

OJO: executeQuery es solo para SELECT, si quiero usar update, insert o delete debo usar executeUpdate. Y como ya no devuelve nada, ya que solo estamos actualizando la tabla, lo podemos de sacar del try con recursos.

![image](https://github.com/Pierohc/JDBC/assets/133154904/9c8eb336-5c99-41b0-9ce5-67069b65a0c8)

## SQL Injection:

Debemos cambiar:

![image](https://github.com/Pierohc/JDBC/assets/133154904/8c64d431-ef10-4cc4-8578-45c3cde1c32e)

Por:

![image](https://github.com/Pierohc/JDBC/assets/133154904/4afe98fa-a76d-4688-a595-55d11e485d2a)

Por ello debemos hacer más cambiar al pedir el usuario y contraseña. Ademas,
cabe resaltar que si a un try dentro un try no le colocamos catch, se irá al catch del try superior.

![image](https://github.com/Pierohc/JDBC/assets/133154904/3354113d-3c13-405a-9c14-04ed65f40f58)

TODO QUERY CRUD donde el usuario ingresa un dato, debe ser Prepared Stament


## Para usar like si deseo buscar por letras usando wildcards:

![image](https://github.com/Pierohc/JDBC/assets/133154904/ab4191fd-7fbb-4834-8405-bb2a9e4e8506)

## Guardar un valor ingresado:

![image](https://github.com/Pierohc/JDBC/assets/133154904/1ddee68e-cc32-433d-a768-47d704e45bc3)

![image](https://github.com/Pierohc/JDBC/assets/133154904/b0479b44-e77c-4621-a1d5-d207ac67a136)

![image](https://github.com/Pierohc/JDBC/assets/133154904/4a57054c-ad19-4ef0-98d7-de110866acf2)





