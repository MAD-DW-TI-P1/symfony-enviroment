<img src="https://jorgebenitezlopez.com/github/symfony.jpg">
<img src="https://img.shields.io/static/v1?label=PHP&message=Symfony&color=green">

# Symfony enviroment

Control del enviroment y manejo de errores

# Requisitos

- Symfony CLI: https://symfony.com/download
- PHP 8.2.3 (cli). Por ejemplo se puede descargar en OSX con: https://formulae.brew.sh/formula/php
- Composer: https://getcomposer.org/download/

# Pasos para la instalación de Symfomy y paquetes

- symfony new symfony-enviroment --version=5.4
- cd symfony-enviroment
- composer require symfony/maker-bundle
- composer require form validator twig-bundle security-csrf annotations
- composer require symfony/twig-pack

# Configuración 

- Arrancamos el servidor: symfony server:start
- Ponemos la ruta /error
- Aparece el log con mucha información
- En el .env podemos quitar el modo debug añadiendo: APP_DEBUG=0
- Similar to configuring the debug mode you can also change de environment. A typical Symfony application begins with three environments: dev for local development, prod for production servers, test for automated tests.
- When running the application, Symfony loads the configuration files in this order (the last files can override the values set in the previous ones). Puedes conectar bases de datos o servicios a diferentes enviroments
- El modo prod es más rápido y no da información de los errores. En el .env poner: APP_ENV=prod
- Volver a visitar la ruta /error y ver la diferencia
- En modo prod tira de cache por lo que es importante limpiar la cache cuando hagamos un cambio. Ejecutar: php bin/console cache:clear
- Para configurar la página de errores hay tres formas. Vamos a configurar el twig. 
- Creamos los twig en las siguientes rutas y los personalizamos
templates/
└─ bundles/
   └─ TwigBundle/
      └─ Exception/
         ├─ error404.html.twig
         ├─ error403.html.twig
         └─ error.html.twig      # All other HTML errors (including 500)
- Borrar cache para actualizar los cambio. Revisar un error de twig. Poner por ejemplo: {{ path('homepage') }} (No existe...) ¿Borrar cache?



# Rutas de la aplicación:

| URL path                    | Description           | 
| :--------------------------:|:---------------------:|
| /error                    |  Diferentes páginas de error dependiendo de la configuración|

# Referencias

- Debug mode: https://symfony.com/doc/5.4/configuration/front_controllers_and_kernel.html#debug-mode

- Enviroment: https://symfony.com/doc/5.4/configuration.html#configuration-environments

- Manejor de errores: http://symfony.com/doc/current/cookbook/controller/error_pages.html#use-kernel-exception-event


# Resumen visual

Error en modo dev
<img src="https://jorgebenitezlopez.com/github/errorSymfony1.png">

Error en modo prod
<img src="https://jorgebenitezlopez.com/github/errorSymfony2.png">

Error en prod personalizado
<img src="https://jorgebenitezlopez.com/github/errorSymfony3.png">

