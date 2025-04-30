---
sidebar_label: 'Base de Datos e Insercion de Usuarios'
sidebar_position: 3
---

# Conexión a la Base de Datos MySQL y Registro de Usuarios

Este módulo establece una conexión con una base de datos MySQL y registra usuarios utilizando contraseñas cifradas con bcrypt.

# Dependencias Utilizadas

1. mysql2: Permite establecer una conexión entre la aplicación Node.js y la base de datos MySQL.

2. bcrypt: Se utiliza para cifrar las contraseñas antes de insertarlas en la base de datos, protegiendo así la seguridad de los usuarios.

Asegúrate de instalar las dependencias usando npm:
```jsx title="bash"
npm install mysql2 bcrypt
```

# Proceso de Conexión

La conexión a la base de datos se configura mediante los datos del servidor: dirección IP, puerto, nombre de usuario, contraseña y nombre de la base de datos. Una vez configurada, la conexión se prueba inmediatamente para verificar que todo esté funcionando correctamente.

Si la conexión falla, se muestra un mensaje de error en consola. Si es exitosa, se confirma la conexión activa.

# Insersión de Usuarios

Una vez conectados, el módulo prepara un conjunto de usuarios predefinidos con nombres, correos y contraseñas.

Cada contraseña es cifrada con bcrypt, usando una técnica llamada hashing con sal, que añade una capa de seguridad al hacer que cada contraseña cifrada sea única, incluso si los usuarios comparten la misma contraseña original.

# Seguridad de Contraseñas

El proceso de cifrado utiliza 10 rondas de “salting” (valor recomendado por defecto), lo que hace más lento cualquier intento de fuerza bruta. Esto significa que si alguien accede a la base de datos, no podrá ver las contraseñas reales.

Después de cifrar cada contraseña, se realiza una consulta SQL para insertar los datos del usuario en la base de datos. Si ocurre un error al insertar, se registra en consola. Si la inserción es exitosa, se muestra un mensaje de confirmación.

# Cierre de la Conexión

Una vez que todos los usuarios han sido insertados en la base de datos, la conexión se cierra explícitamente para liberar recursos.

-Jaime Gámez Gómez Rubalcava A01410192@tec.mx