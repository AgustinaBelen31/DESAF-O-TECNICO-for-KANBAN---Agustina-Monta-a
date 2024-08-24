# **Sistema de Alquiler de Películas \- KANBAN Agustina Montaña**

## **Descripción:** Este proyecto consiste en la creación y gestión de una base de datos para un sistema de alquiler de películas. El sistema permite gestionar la información de los clientes, las películas disponibles, y las transacciones de alquiler. 

## **Estructura de la database:** 

\#\# Estructura de la Base de Datos

La base de datos \`KANBAN Agustina Montaña\` consta de las siguientes tablas:

\#\#\# \`clientes\`  
| Columna       | Tipo de Dato | Descripción                |  
| \------------- | \------------ | \-------------------------- |  
| \`cliente\_id\`  | INT          | Identificador único del cliente (Primary Key) |  
| \`nombre\_cliente\` | VARCHAR(50) | Nombre del cliente          |  
| \`correo\_cliente\` | VARCHAR(50) | Correo electrónico del cliente |

\#\#\# \`peliculas\`  
| Columna       | Tipo de Dato | Descripción                |  
| \------------- | \------------ | \-------------------------- |  
| \`pelicula\_id\` | INT          | Identificador único de la película (Primary Key) |  
| \`titulo\`      | VARCHAR(100) | Título de la película        |  
| \`genero\`      | VARCHAR(50)  | Género de la película        |

\#\#\# \`alquileres\`  
| Columna       | Tipo de Dato | Descripción                |  
| \------------- | \------------ | \-------------------------- |  
| \`alquiler\_id\` | INT          | Identificador único del alquiler (Primary Key) |  
| \`pelicula\_id\` | INT          | Identificador de la película alquilada (Foreign Key) |  
| \`cliente\_id\`  | INT          | Identificador del cliente que realizó el alquiler (Foreign Key) |  
| \`fecha\_renta\` | DATE         | Fecha en que se realizó el alquiler |

## **Instrucciones para Configurar y Ejecutar:** 

\#\# Instrucciones para Configurar y Ejecutar el Proyecto

\#\#\# 1\. Configuración de la Base de Datos

1\. \*\*Crear la Base de Datos:\*\*  
   \- Usá el siguiente comando en MySQL para crear la base de datos:  
   \`\`\`sql  
   CREATE DATABASE \`KANBAN Agustina Montaña\`;  
   USE \`KANBAN Agustina Montaña\`;

### Creación de tablas

CREATE TABLE clientes (  
    cliente\_id INT AUTO\_INCREMENT PRIMARY KEY,  
    nombre\_cliente VARCHAR(50),  
    correo\_cliente VARCHAR(50)  
);

CREATE TABLE peliculas (  
    pelicula\_id INT AUTO\_INCREMENT PRIMARY KEY,  
    titulo VARCHAR(100),  
    genero VARCHAR(50)  
);

CREATE TABLE alquileres (  
    alquiler\_id INT AUTO\_INCREMENT PRIMARY KEY,  
    pelicula\_id INT,  
    cliente\_id INT,  
    fecha\_renta DATE,  
    FOREIGN KEY (pelicula\_id) REFERENCES peliculas(pelicula\_id),  
    FOREIGN KEY (cliente\_id) REFERENCES clientes(cliente\_id)  
);

### Inserción de datos iniciales: 

INSERT INTO clientes (nombre\_cliente, correo\_cliente) VALUES ('Juan Pérez', 'juan@example.com');  
INSERT INTO peliculas (titulo, genero) VALUES ('Inception', 'Ciencia Ficción');  
INSERT INTO alquileres (pelicula\_id, cliente\_id, fecha\_renta) VALUES (1, 1, '2024-08-23');

## 

## 

## **Ejecución de consultas:** 

Para verificar el funcionamiento de la base de datos, ejecute  la siguiente consulta que une las tablas `peliculas`, `clientes`, y `alquileres` para mostrar qué clientes han alquilado qué películas:

SELECT   
    p.titulo,  
    c.nombre\_cliente  
FROM peliculas p  
JOIN alquileres a ON p.pelicula\_id \= a.pelicula\_id  
JOIN clientes c ON c.cliente\_id \= a.cliente\_id  
ORDER BY p.titulo, c.nombre\_cliente;

## **Conclusión:** 

Este proyecto demuestra cómo se puede crear y gestionar una base de datos para un sistema de alquiler de películas utilizando MySQL. La estructura de las tablas y las consultas permiten manejar la información de manera eficiente, proporcionando una base sólida para un sistema de gestión más complejo en el futuro.

