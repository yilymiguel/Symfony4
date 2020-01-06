PRIMEROS PASOS EN SYMFONY 4
Symfony Demo Application
========================

Si estas empezando algún proyecto en PHP habrás oído hablar de Symfony, este es un framework muy popular que al momento de escribir este post está en su versión 4.1.
En este tutorial instalaremos paso por paso Symfony 4 en nuestro entorno de desarrollo. La instalación la haremos dependiendo si nuestro usaremos Symfony para programar una API REST o si nuestro desarrollo será una aplicación monolítica con el frontend y el backend acoplados en una misma estructura.

Requisitos antes de comenzar
Para comenzar con Symfony es muy importante tener instalado los siguiente programas.
•	Git
•	Composer
•	PHP 7.1.3 o superior
El ultimo requisito se pueden instalar con programas como XAMP, WAMP, MAMP o cualquier tipo de servidor LAMP en un entorno virtualizado como Vagrant o Docker.

Paso 1 — Instalación
En la actual versión cuatro de Symfony podemos instalarlo de dos maneras diferentes dependiendo del tipo de arquitectura que se necesite.

•	Opción 1: Si nuestro proyecto será una API REST o un Micro servicio debemos ejecutar el siguiente comando desde una terminal situados en el directorio donde estar nuestro proyecto.
$ composer create-project symfony/skeleton mi-proyecto

•	Opción 2: Si nuestro Proyecto será una aplicación con arquitectura monolítica debemos ejecutar.
$ composer create-project symfony/website-skeleton mi-proyecto

La diferencia de ambas instalaciones se encuentra en el número de librerías que se instalaran, mientras la primera opción instala las mínimas dependencias para que funcione Symfony la segunda opción instala todas las librerías mas importantes como twig o doctrine.

Paso 2 — Configuración de la Base de datos
Symfony no provee de un componente que trabaje con bases de datos es por eso que necesitaremos instalar dos paquetes para trabajar con persistencia de datos.
Primeramente, necesitaremos instalar Doctrine el cual es un ORM que nos ayuda a construir nuestra capa de abstracción para el manejo de nuestra base de datos.
$ composer require symfony/orm-pack

Una vez instalado Doctrine es importante pero no necesario instalar un paquete que nos ayude a generar código para poder ahorrar mucho trabajo escribiendo archivos que tienen una misma estructura
$ composer require symfony/maker-bundle --dev

Instalados estos dos requisitos ya podemos configurar el acceso a nuestra base de datos. Para configurar el acceso debemos buscar el archivo .env que se encuentra en la raíz de nuestro proyecto. En este archivo debemos especificar:
•	El motor de base de datos
•	El usuario y password
•	La ip y el puerto
•	El nombre de nuestra base de datos

Como por ejemplo:

###> doctrine/doctrine-bundle ###DATABASE_URL=mysql://root:12345@127.0.0.1:3306/bbdd_mi_proyecto###< doctrine/doctrine-bundle ###

No es necesario crear previamente la base de datos porque se puede crear por el comando:
$ php bin/console doctrine:database:create

Paso 3- Ejecutar nuestro servidor de PRUEBA
Resalto la palabra prueba porque en muchos casos recibo preguntas de como ejecutar el servidor de Symfony en un entorno de producción y la respuesta es siempre la misma NO SE DEBE HACER y la razón es simple, porque para un entorno de producción necesitas la configuración de un servidor APACHE o NGIX que ejecute tu proyecto.

Pero para probar que nuestra instalación sea correcta necesitamos instalar una dependencia mas para poder ejecutar nuestra aplicación en el navegador.
$ composer require symfony/web-server-bundle --dev

Una vez instalado ejecutamos nuestra aplicacion:
$ php bin/console server:run

en caso de no tener un binary para esto puedes usar este comando para ejecutar la aplicación
$ php -S localhost:8000 -t public/

accedes al navegador para ver la aplicaicon con la siguiente URL  (<https://localhost:8000> por defecto):

Y con este ultimo comando ya terminamos la intalacion.

Nota: entrar a https://symfony.com/download para descargar los CLI de Symfony4.
Documentacion a revisar.
[1]: https://symfony.com/doc/current/best_practices.html
[2]: https://symfony.com/doc/current/reference/requirements.html
[3]: https://symfony.com/doc/current/cookbook/configuration/web_server_configuration.html
[4]: https://symfony.com/download
[5]: https://github.com/symfony/webpack-encore



