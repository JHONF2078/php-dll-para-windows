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
    
    
- Crear dll

   - abrimos la consola de desarrollado de visual studio la cual esta ubicada en C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools\VC (abrir como administrador), si queremos crear nuestra dll para 64 bit debemos abrir **Símbolo del sistema de las herramientas nativas x64 de VS 2017**  y si la quemos para 32 bits debemos abrir **x86 Native Tools Command Prompt for VS 2017**
   
   ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/4-cmd_vs2017.PNG)
    
    
   - descomprimimos el php-sdk  y su contenido lo agregamos  aun nuevo directorio ubicado en  C:\php-sdk
   
    ![no se encontro la imagen](https://raw.githubusercontent.com/JHONF2078/php-dll-para-windows/master/img/5-ruta_phpsdk.PNG)
    
   
   - entramos al directorio recien creado ejecutando  cd c:\php-sdk\ en la consola de comandos
   
   
    
  

    
    
    
    
  



 
