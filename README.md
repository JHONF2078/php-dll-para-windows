# php-dll-para-windows
manual de como crear sus propias dll para windows

vamos a suponer que tiene instalado xampp con php 7.3.6 en un equipo con windows 10 x64(bits) y necesita la dll php_pdo_informix, la cual hace parte de los repositorios pecl y no esta como dll para windows (esta dll permite la conexion con bases de datos informix )

- Descargar recursos
    - descargamos php  desde la opcion Download source code [26.77MB]
    
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/1-%20recursos_php.PNG)
  
   - descargamos php-sdk , el cual permitira la creacion de las dll
  
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/2-%20php_sdk.PNG)
  
   - descagamos php_pod_informix , que sera la libreria para conectar php y la base de datos de informix
    
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master   /img/3-%20pdo_informix_pecl.PNG)
    
    
- Crear dll

   - abrimos la consola de desarrollado de visual studio la cual esta ubicada en C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools\VC (abrir como administrador), si queremos crear nuestra dll para 64 bit debemos abrir **Símbolo del sistema de las herramientas nativas x64 de VS 2017**  y si la quemos para 32 bits debemos abrir **x86 Native Tools Command Prompt for VS 2017**
    
   - creamos un nuevo directorio en C:\php-sdk
   
   - entramos al directorio recien creado ejecutando  cd c:\php-sdk\ en la consola de comandos
   
   
    
  

    
    
    
    
  



 
