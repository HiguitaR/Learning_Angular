# ANGULAR LEARNING

## Instalacion de paquetes NPM

    Para realizar la instalacion de Node Js devemos ir ala pagina web http://node.org/en y verificamos
    la ultima version estable "no se recomienda la instalacion del paquete que hay por defecto
    (macOS intaller.pkg)", lo que se recomienda es usar el acceso 'nvm' este es el administrador de
    versiones de Node. Este ayuda a cambiar entre versiones de Node a me dida que cambias de proyectos.
    Vamos al repositorio en github (nvm-sh), buscamos el archivo README.md alli hay una seccion de 
    instalacion\actualizacion y sigues los pasos segun lo necesario.

    Ahora vamos a Angular Documentation 'angular.dev' y revizamos la tabla de versiones compatibles
    disponibles de angular/node.js/typescript.

    cada ves que Angular lanza una actualizacion debemos desinstalar Angular Cli y volver a instalar
    comando en terminal (npm uninstall -g @angular/cli).

    para instalar los paquetes que se necesitan para usar Angular debemos digitar en la
    terminal (npm install -g @angular/cli). 

    Si queremos verificar las versiones actualmente instaladas usamos el comando 'ng version'

    para crear un nuevo proyecto usando la terminal nos ubicamos en el directorio que deseamos
    despues alli usamos el comando (ng new "nombre del proyecto") el creara las carpetas que necesita
    a continuacion el Cli hara unas preguntas para configurar el proyecto.

    Si miramos la estructuras del proyecto vemos los archivos ya instalados por el nvm administrador
    alli hay varios archivos:
    - package.jso: donde esta la configuracion general del proyecto, vemos como ejemplo comandos para
        iniciar en terminal el servidor 'ng serve', 'ng build', 'ng test', etc.
        aqui encontramos las dependencias instaladas con su version

    - angular.json: aqui tenemos algunas configuraciones para el proyecto, podemos configurar para 
        que mi proyecto reutilice componentes, encontramos estilos y constructores para el proyecto
        para compilaciones.

    - tsconfig.json: aqui tenemos las configuraciones para Typescript, configuraciones globales del
        mismo.
    
    - Public: alli se agregaran las imagenes que usara el proyecto o demas que sea de acceso publico
        
    - src: aqui esta el codigo fuente del proyecto. hay 3 archivos para manejar las configuraciones
        globales para styles, .ts y .html.

    Usaremos para iniciar el proyecto 'npm run start' para iniciar todo los modulos y poder conectar
    el proyecto con el backend.

    


