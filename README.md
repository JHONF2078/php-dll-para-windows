# php-dll-para-windows
manual de como crear sus propias dll para windows

vamos a suponer que tiene instalado xampp con php 7.3.6 en un equipo con windows 10 x64(bits) y necesita la dll php_pdo_informix, la cual hace parte de los repositorios pecl y no esta como dll para windows (esta dll permite la conexion con bases de datos informix )

- Descargar recursos
    - descargamos php  desde la opcion Download source code [26.77MB]
    
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/1-recursos_php.PNG)
  
   - descargamos php-sdk , el cual permitira la creacion de las dll
  
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/2-php_sdk.PNG)
  
   - descagamos php_pod_informix , que sera la libreria para conectar php y la base de datos de informix
    
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/3-pdo_inf_pecl.PNG)
    
   - descargamos visual studio, la version dependera de lo que vamos a compilar :
    
       - si vamos a compilar  PHP 7.0+: instalar visual studio 2015 (vc14)

       - si vamos a compilar  PHP 7.2+: instalar visual studio 2017 (vc15)
       
       - si vamos a compilar  PHP 7.4+: instalar visual studio 2019 (vc16)
   
   
   
   
    
- contruyendo el directorio

   - abrimos la consola de desarrollado de visual studio la cual esta ubicada en **C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools\VC** (abrir como administrador), si queremos crear nuestra dll para 64 bit debemos abrir **Símbolo del sistema de las herramientas nativas x64 de VS 2017**  y si la quemos para 32 bits debemos abrir **x86 Native Tools Command Prompt for VS 2017**
   
   ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/4-cmd_vs2017.PNG)
    
    
   - descomprimimos el php-sdk  y su contenido lo agregamos  aun nuevo directorio ubicado en  C:\php-sdk
   
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/5-ruta_phpsdk.PNG)
    
   
   -  en la consola de visual studio digitamos  cd c:\php-sdk\ para  entrar al directorio recien creado
   
   - una vez dentro del directorio **php-sdk** , ahora vamos a ejecutar el script de inicio  **phpsdk-vc15-x64** ( se ejecuta este script ya que vamos a compilar php 7.3.6 a 64(bits) 
   
    
     ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/6-iniciar_script.PNG)
 
   
   
   - ejecutamos **phpsdk_buildtree phpdev** para crear la estructura del directorio, es decir se crea la ruta
   **C:\php-sdk\phpdev\vc15\x64**
   
     ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/7-estructura.PNG)
     
     ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/8-estructura2.PNG)
   
   - descomprimimos los recursos de php y los copiamos en este ruta
   
     ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/9-copiamos_php.PNG)
   
   - en este mismo directorio cremos una carpeta llamada pecl
   
   ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/10-crear_pecl.PNG)
   
   - dentro de la carpeta pecl descomprimimos la libreria  dpo_informix
   
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/11-copiamos_pdoinf.PNG)
   
    - ahora entramos  a los recurso de php mediante el comado  **cd C:\php-sdk\phpdev\vc15\x64\php-7.3.6-src**
   
     ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/12-carpeta_php.PNG)
   
    - una vez ubicados dentro de php ejecutamos el comado **phpsdk_deps -u**,el cual descargara los dependencias de php automaticamente
   
     ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/13-descargar_depend.PNG)
   
    - se nos creara una nueva carpeta con las dependencias descargadas
   
      ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/14-dependencias.PNG)


- Compilar 
   
   - con la estructura del proyecto ya creada  y si aun estamos ubicados en   **C:\php-sdk\phpdev\vc15\x64\php-7.3.6-src** ,entonces ejecutamos el comando **buildconf*  el cual reconstruira el fichero configure.js 
    *nota :  recuerde que si quiere compilar una extension posteriormente  debera ingresar al directorio C:\php-sdk y ejecutar el comando **phpsdk-vc15-x64** para inicial al script, despues debe ir al directorio **C:\php-sdk\phpdev\vc15\x64\php-7.3.6-src** y despues si ejecuta el comado **buildconf*
    
     ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/15-buildconf.PNG)

    
    - ejecutamos el comado configure --help, donde podemos la linea  **--with-pdo-informix**,  esto significa que ya tenemos la libreroa pdo-informix lista para cargar 
    
      ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/16-configure_help.PNG)
    
        *nota :    
        (**--enable** significa que es una libreria lista paracargar y **--with** significa que es una libreria lista para  cargar pero que depende de otras, en este caso de la libreria pdo)*
   
    
   - ahora vamos a configurar el script  para que solo nos compile las libreria que necesitamos para ello ejecutamos el siguiente comando 
    
     **configure --disable-all --enable-cli  --with-pdo-informix="C:\Program Files\Informix Client-SDK",shared --enable-pdo**
        
     
     ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/17-configuracion.PNG)
   
        
     - **configure** : es el comado para la configuracion, siempre debe ir
     - **--disable-al**  deshabilita la compilacion de las otras libreria
     - **--enable-cli**  creara la consola  cli de php
     - **-with-pdo-informix="C:\Program Files\Informix Client-SDK,shared"** :  habilitara la creacion de la libreria pdo-informix como una libreria dll (shared) y ademas requiere el sdk de informix para poder compilarla 
     - **--enable-pdo** , habilitara la libreria pdo ya que es requerida para crear la libreria pdo-informix
     
     * nota: la mayoria de las librerias solo requiere ejecutar el comando  **--enable-nombre_libreria** o el comando **--     with-nombre_libreria** para ser compiladas , pero la libreria pdo-informix en un caso especial que requiere de un sdk para su compilacion
     
     * nota : recuerde que para compilar una libreria como dll debe ejecutar el comando **--enable-nombre_libreria=shared** e el comado **--with-nombre_libreria=shared** *
           
           
  - podemos ver un resumen de las extenciones habilitadas pdo como libreria estatica y pdo_informix como libreria dinamica (dll)
  
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/18-ext_habilitadas.PNG)
  
  - ahora compilamos php mediante el comando **nmake**, podemos ver la ruta donde se ha compilado nuestro php
  
   ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/19-ruta_compilacion.PNG)
  
  - podemos ver nuestra dll creada
  
  ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/20-dll_creada.PNG)
  
  
- agregar dll a php (para este ejemplo xampp con php 7.3.6 vc 15 x64)
  
  - ahora copiamos la dll creada dentro del directorio **C:\xampp\php\ext**
  
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/21-dll_xammp.PNG)
  
  - agregamos la referencia dentro del php.ini de xampp
  
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/22-php_ini.PNG)
  
  
  - verificamos el phpinfo()
  
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/23.php_module.PNG)
  
  
  
  
  
  
  
  
           
    
    
    
    
    
    
   
   
   
   
   
     
   
   
   
   
   
   
   
  

  
   
   
   
    
  

    
    
    
    
  



 
