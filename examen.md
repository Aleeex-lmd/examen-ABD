# Bloque I. Instalación de Servidores y Clientes. Interconexión de Servidores.

## 1. En este primer ejercicio tendrás que realizar algunas modificaciones que afectarán a la aplicación web que realizaste en la parte individual de la práctica 1.

### a) Crea una base de datos con el nombre GN si estás en Mongo, Postgres o MySQL. Si tu aplicación conectaba con ORACLE cambia el nombre de la instancia por GNR1 y crea un esquema para el usuario RAUL. Realiza una captura donde se aprecie este cambio. (1 punto)

![alt text](img/bloque1_ejercicio1_img1.png)

### b) Usando la herramienta gráfica de administración usada en la parte grupal de la práctica 1 o SQL Developer y usando una conexión TNS (no básica) si tu aplicación trabaja con ORACLE, crea una tabla o una colección profesores con los campos DNI y Nombre e introduce los siguientes datos:

```
DNI	Nombre
28888888	Raúl Ruiz Padilla
27777777	Rafael Luengo Sanz
```

![alt text](img/bloque1_ejercicio1_img2.png)

![alt text](img/bloque1_ejercicio1_img3.png)

![alt text](img/bloque1_ejercicio1_img4.png)

![alt text](img/bloque1_ejercicio1_img5.png)

![alt text](img/bloque1_ejercicio1_img6.png)

![alt text](img/bloque1_ejercicio1_img7.png)

![alt text](img/bloque1_ejercicio1_img8.png)

## 2. Para este ejercicio necesitarás tener en una BD ORACLE llamada GNREC, en el esquema RAUL la tabla profesores antes creada y en una BD Postgres llamada GNREC2 en otra máquina la siguiente tabla Asignaturas:

Nombre	DNI Profesor
ASO	28888888
ABD	27777777

### a) Debes realizar una consulta desde un cliente ORACLE que muestre el nombre de las asignaturas y el del profesor que las imparte usando una interconexión entre ambos servidores. (2,5 p)


### b) Debes realizar una consulta desde un cliente Postgres que muestre el nombre de las asignaturas y el del profesor que las imparte usando una interconexión entre ambos servidores. (2,5 puntos)

![alt text](img/bloque1_ejercicio2_img2.png)

![alt text](img/bloque1_ejercicio2_img3.png)



# Bloque II. SQL y PL/SQL

## 1.- Realiza una consulta SQL que muestre los nombres de los trabajadores que tienen tareas sin terminar en más de un proyecto (1,5 puntos)

```sql
SELECT personaresponsable
FROM tareasproyecto
WHERE terminada = 'n'
GROUP BY personaresponsable
HAVING COUNT(DISTINCT codproyecto) > 1;
```

![alt text](img/bloque2_ejercicio1_img1.png)

## 2.- Realiza una consulta SQL que muestre los nombres de los proyectos junto a la descripción de la tarea más larga que se haya terminado de cada uno de ellos. (1,5 puntos)

```sql
select p.nombre, t.descripcion
from proyectos p
join tareasproyecto tp on p.codproyecto = tp.codproyecto
join tareas t on tp.codtarea = t.codtarea
where tp.terminada = 's' and t.numdias = (
    select max(t2.numdias)
    from tareas t2
    join tareasproyecto tp2 on t2.codtarea = tp2.codtarea
    where tp2.codproyecto = p.codproyecto and tp2.terminada = 's');
```

![alt text](img/bloque2_ejercicio2_img2.png)

# Bloque III. Usuarios y Almacenamiento.

## 1. (2 puntos) Crea una base de datos llamada Examen en Postgres con una tabla llamada Prueba1 con dos registros y otra llamada Prueba2 sin registros.

Crea ahora un usuario en Postgres con las siguientes características:

    • Podrá consultar las tablas existentes en la base de datos Examen e insertar registros en la tabla Prueba2 pero solo podrá leer Prueba1.
    • No podrá crear tablas nuevas en la base de datos Examen, pero sí vistas.
    • Su contraseña deberá ser cambiada cuando entre por primera vez en el sistema.
    • No podrá saber las bases de datos existentes en el gestor de bases de datos.
    • Podrá crear funciones y procedimientos.

![alt text](img/bloque3_ejercicio1_img1.png)

![alt text](img/bloque3_ejercicio1_img2.png)

![alt text](img/bloque3_ejercicio1_img3.png)

![alt text](img/bloque3_ejercicio1_img4.png)

![alt text](img/bloque3_ejercicio1_img5.png)

![alt text](img/bloque3_ejercicio1_img6.png)

-- falta el de la contraseña

![alt text](img/bloque3_ejercicio1_img10.png)

![alt text](img/bloque3_ejercicio1_img11.png)

![alt text](img/bloque3_ejercicio1_img11.png)

## 3. (1,5 puntos) Crea tres usuarios en MongoDB.
Crea dos colecciones Examen1 y Examen2 con dos documentos cada una con los atributos que desees.
El primer usuario podrá acceder a la colección Examen1 pero solo para añadir documentos.
El segundo podrá acceder solo Examen2 y solo para modificar los documentos.
El tercer usuario tendrá acceso a las dos colecciones para leer documentos. 

![alt text](img/bloque3_ejercicio3_img1.png)

![alt text](img/bloque3_ejercicio3_img2.png)

![alt text](img/bloque3_ejercicio3_img3.png)

![alt text](img/bloque3_ejercicio3_img4.png)

![alt text](img/bloque3_ejercicio3_img5.png)

![alt text](img/bloque3_ejercicio3_img6.png)

![alt text](img/bloque3_ejercicio3_img7.png)

![alt text](img/bloque3_ejercicio3_img8.png)


## 4. (2 puntos) Realiza una función de verificación de contraseña para ORACLE que solo permita contraseñas sin mayúsculas ni números pero de una longitud mínima superior al doble de la longitud del nombre de ese usuario. Además, la contraseña no puede coincidir con el nombre de ningún usuario, vista o tabla ya existente en la base de datos. Crea un usuario y realiza las capturas necesarias para demostrar el correcto funcionamiento de la función.

![alt text](img/bloque3_ejercicio4_img1.png)

![alt text](img/bloque3_ejercicio4_img2.png)

![alt text](img/bloque3_ejercicio4_img3.png)

![alt text](img/bloque3_ejercicio4_img4.png)

![alt text](img/bloque3_ejercicio4_img5.png)

![alt text](img/bloque3_ejercicio4_img6.png)

![alt text](img/bloque3_ejercicio4_img7.png)

![alt text](img/bloque3_ejercicio4_img8.png)

![alt text](img/bloque3_ejercicio4_img9.png)

![alt text](img/bloque3_ejercicio4_img10.png)




## 5. (1,5 puntos) Crea un índice de búsqueda de texto (son los que permiten localizar una cadena en un documento rápidamente) sobre una colección en MongoDB. Añade algunos documentos a la colección y demuestra que el índice está creado y funcionando.

![alt text](img/bloque3_ejercicio5_img1.png)

![alt text](img/bloque3_ejercicio5_img2.png)

![alt text](img/bloque3_ejercicio5_img3.png)

# Bloque IV. Auditoría, movimiento de datos y copias de seguridad

## 1. (1,5 puntos) Crea una colección en MongoDB y audita exclusivamente las modificaciones de documentos que se produzcan en la misma. Demuestra el funcionamiento.

![alt text](img/bloque4_ejercicio1_img1.png)

![alt text](img/bloque4_ejercicio1_img2.png)

![alt text](img/bloque4_ejercicio1_img3.png)

![alt text](img/bloque4_ejercicio1_img4.png)

## 2. (2,5 puntos) Crea una tabla en MariaDB con un campo cadena de caracteres, otro númerico sin decimales, otro númerico con tres decimales y otro de tipo fecha. Inserta algunos registros en ella. Exporta dicha tabla como un fichero de texto usando un guión como delimitador. Carga dichos datos en una tabla ORACLE usando SQL*Loader.

```sql
CREATE TABLE tabla_examen_recuperacion (
    cadena VARCHAR(50),
    entero INT,
    decimal_tres DECIMAL(10,3),
    fecha DATE
);


INSERT INTO tabla_examen_recuperacion (cadena, entero, decimal_tres, fecha) VALUES 
('examen a', 10, 123.456, '2023-05-10'),
('examen b', 25, 987.654, '2023-08-22'),
('examen c', 42, 0.123, '2024-01-15');
```

![alt text](img/bloque4_ejercicio2_img1.png)

```sql
SELECT * FROM tabla_examen_recuperacion
INTO OUTFILE '/tmp/datos_exportados_examen_recuperacion.txt'
FIELDS TERMINATED BY '-'
LINES TERMINATED BY '\n';
```

![alt text](img/bloque4_ejercicio2_img2.png)

```bash
cat /home/user/datos_exportados_examen_recuperacion.txt
```

![alt text](img/bloque4_ejercicio2_img3.png)

```sql
CREATE TABLE tabla_examen_recuperacion (
    cadena VARCHAR2(50),
    entero NUMBER(10,0),
    decimal_tres NUMBER(10,3),
    fecha DATE
);
```

![alt text](img/bloque4_ejercicio2_img4.png)

```bash
# control.ctl
LOAD DATA
INFILE 'datos_exportados_examen_recuperacion.txt'
INTO TABLE tabla_examen_recuperacion
FIELDS TERMINATED BY '-'
TRAILING NULLCOLS
(
  cadena,
  entero,
  decimal_tres,
  fecha DATE "YYYY-MM-DD"
)
```

![alt text](img/bloque4_ejercicio2_img5.png)

```bash
sqlldr userid=C##RAUL/asang04@GNREC control=control.ctl
```

![alt text](img/bloque4_ejercicio2_img6.png)


![alt text](img/bloque4_ejercicio2_img7.png)
