# DAW_M07_UF3
Desarrollo de la actividad
Para la realización de esta actividad es necesario que dispongas de un servidor
web que permita ejecutar páginas PHP. En el campus dispones de un vídeo
explicativo para instalar XAMPP y también Visual Studio Code como IDE, pero
ninguno de ellos es obligatorio, puedes usar el servidor web e IDE que prefieras.
Lo que sí es obligatorio es que la aplicación web esté desarrollada en PHP y
que funcione acorde a los requisitos.
El proyecto será un sistema que permitirá a los usuarios registrarse, buscar libros,
gestionar préstamos, y que los administradores puedan gestionar la base de datos de
libros y usuarios.
Debe desarrollarse una aplicación web usando PHP acorde a los siguientes requisitos:
Requisitos compartidos con la UF2:
- Todo el proyecto estará en el directorio biblioteca. Este será el directorio que
se entregará la actividad.
- La página principal de la aplicación se llamará index.php.
- Toda la aplicación tendrá una cabecera con el nombre y colores de la
biblioteca, que estará en un fichero independiente y se añadirá en cada página
con un include.
- Una vez validado el usuario se redirigirá a index.php.
- Sí el usuario no es admin debe acceder al listado de libros (UF2)
- Sí el usuario es admin debe acceder al panel de control
- La sesión del usuario caducará a los 30 minutos de haber iniciado sesión.
Nuevos requisitos de la Actividad:
- En está practica vamos a retomar el sistema de registro de la UF1, el formulario
de registro debe ingresar los datos en una base de datos que se llamará
“biblioteca”.
- Datos de biblioteca
o server = localhost
o user = root
o pasw = “”
o bd = biblioteca
La Bd de datos biblioteca tendrá dos tablas, la primera será la de pedidos. Te dejo los
datos de la tabla en SQL.
- Tabla pedidos:
CREATE TABLE pedidos (
id INT AUTO_INCREMENT PRIMARY KEY,
titulo VARCHAR(255) NOT NULL,
isbn VARCHAR(13) NOT NULL,
fecha DATE NOT NULL,
usuario VARCHAR(10) NOT NULL );
5
Los usuarios se registrarán en una tabla que se llamará “usuarios”
- La tabla usuarios debe tener los siguientes campos:
o id : int(11) KP (clave principal) autoincremental
o nombre: varchar(100)
o edad : int(11)
o nick_usuario: varchar(10) UNICO (no puede haber dos iguales).
o contrasena: varchar(255)
- En el proceso de registro se debe confirmar que el Nick de usuario no está ya
dado de alta en la BD, en caso de existir no debe terminar el proceso de
inserción y dar un mensaje de aviso al usuario.
- El proceso de registro respetara el proceso de la UF1 :
o Habrá un enlace desde el formulario de acceso.
o Formulario de registro
o Formulario de confirmación
o Mensaje de confirmación con enlace al index.
- El primer usuario que vamos a registrar es “admin”.
Esquema de funcionamiento (sólo es una propuesta el diseño o la apariencia puede
variar).
1. Enlace desde el formulario de acceso.
2. Formulario de registro
6
3. Formulario de confirmación
4. Mensaje de confirmación con enlace al index.
- El formulario de login debe comprobar los datos de acceso en la BD y si el
usuario no está registrado o la contraseña es errónea debe dar un mensaje de
error.
- Sí el usuario que accede es el admin, se cargará el panel de control del ERP
LibroSphere.
o El enlace Gestión de Clientes dará acceso a un listado de todos los
clientes, en el listado incluiremos botones para poder actualizar los
datos de un cliente o eliminar a un cliente.
o El enlace Gestión de Pedidos dará acceso a un listado de todos los
clientes, en el listado incluiremos botones para poder actualizar los
datos de un pedido o eliminar un pedido.
o El enlace Gestión de Libros no será funcional
7
- Sí el usuario que accede no es el administrador se cargarán los libros cómo en
la UF2.
o En este caso el botón “Comprar” nos llevara a un formulario para hacer
el pedido el formulario debe cargar de forma dinámica el titulo del libro,
el isbn del libro, la fecha de compra y el usuario de la sesión activa que
realiza el pedido.
o En caso de confirmación el formulario ingresará los datos en la tabla
pedidos. Confirmará el pedido con la frase “Ped
