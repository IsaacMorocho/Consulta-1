# Consulta 1

A continuacion se detallan los pasos para lograr las siguientes caracteristicas en la apk de Ionic - Angular:

- Icono Personalizado
- Splash Screen
- Permisos en AndroidManifest.xml

Se uso una plantilla en blanco y el ng modules para la creacion de la tarea con ionic start

## ICONO

El icono que se eligio para esta tarea es el siguiente:

<img width="324" height="324" alt="icon" src="https://github.com/user-attachments/assets/a2695da4-5151-4152-9167-7d51bc46348b" />

Se requiere estrictamente las medidas 1024 x 1024 px para el icono.

## 1) Carpeta assets 

Se crea la carpeta "assets" al mismo nivel que la carpeta "src" y se coloca dentro la imagen con el nombre de "icon.png"

<img width="249" height="119" alt="image" src="https://github.com/user-attachments/assets/061ee5b0-988f-48b1-8531-0057df3614f2" />

## 2) Generacion de icono

En la raiz del proyecto ejecutamos el siguiente comando:

 npx capacitor-assets generate

Dicho comando detectará automaticamente la imagen icon.png en la carpeta assets.

## 3) Android Studio

Una vez ejecutado correctamente el comando se procede a verificar en Android Studio, sin antes de sincronizar cambios desde VS Code.

Se uso un telefono fisico para hacer las respectivas pruebas que cuenta con Android V13 

<img width="187" height="177" alt="image" src="https://github.com/user-attachments/assets/b8e83fa1-7303-46b8-bf90-18a844319653" />


## SPLASH SCREEN

La imagen que se eligio para esta tarea es la siguiente:

<img width="372" height="371" alt="image" src="https://github.com/user-attachments/assets/13fb4a78-d3e7-4545-93f9-c7b4ba051c21" />

Se requiere estrictamente las medidas de 2732 x 2732 px para el splash screen

## 1) Carpeta assets

En la carpeta generada en el anterior paso se coloca la iamgen para el splash screen con el nombre de "splash.png"

<img width="245" height="74" alt="image" src="https://github.com/user-attachments/assets/d096ec24-d3e3-4710-a9dd-48abc5620b4f" />

## 2) Configuraciones

Se instala la herramienta de capacitor: splash-screen en la raiz del proyecto con el comando:

 npm install @capacitor/splash-screen

Desde la documentacion oficial de Capacitor plugin, copiamos la configuracion de los plugins de dicho componente:

<img width="725" height="499" alt="image" src="https://github.com/user-attachments/assets/35bb74e6-f921-421d-aff2-b45fe394481f" />

Luego nos dirigimos al archivo "capacitor.config.ts" y pegamos dicha configuracion. Esto nos sirve para controlar el como se vera nuestra imagen splash cuando se abra el apk.

En el archivo "app.components.ts" agregamos una funcion asíncrona para mostrar nuestro splash con un tiempo de 3 segundos de la siguiente manera:

<img width="460" height="408" alt="image" src="https://github.com/user-attachments/assets/87391135-51db-4d87-8e04-b6a2d68fd63f" />

Cabe recalcar que "standalone" debe estar en falso para evitar problemas de importacion en la pagina home.module.ts

## 3) Android Studio

Luego de sincronizar cambios desde VS code hacia Android Studio "npx cap sync android" verificamos si se muestra correctamente en el dispositivo fisico:

<img width="365" height="715" alt="image" src="https://github.com/user-attachments/assets/eaeca684-90ec-4202-97d2-57cd806a9697" />

Se puede ajustar la visualizacion desde el archivo "capacitor.config.ts" para una mejor comodidad.

## ANDROID MANIFEST

Como contexto general, se va a usar el permiso de la linterna fisica del dispositivo movil para esta tarea.

## 1) Instalacion y permiso

De primeras se penso en utilizar el paquete: @capacitor-community/flashlight, pero actualmente dicho paquete ya no esta disponible en npm, por lo tanto se usa el plugin: @awesome-cordova-plugins/flashlight para ello instalamos las dependencias con los siguientes comandos:

 npm install cordova-plugin-flashlight
 
 npm install @awesome-cordova-plugins/flashlight

Luego abrimos el archivo "AndroidManifest.xml" en donde colocaremos la siguiente linea de codigo que contiene el permiso de acceder a la camara (necesario para controlar el flash) de la siguiente manera:

<img width="498" height="82" alt="image" src="https://github.com/user-attachments/assets/39698114-877b-42ed-aeed-3147bf8682d8" />

Y registramos como provider dentro del modulo en home.module.ts importando su libreria.

## 2) Logica para interaccion con el usuario

Dentro del componente "home.page.ts" se importa de @awesome-cordova-plugins/flashlight/ngx' la herramienta Flashlight y se crea una función asíncrona para controlar el flash cuando se accione de la siguiente manera:

<img width="636" height="399" alt="image" src="https://github.com/user-attachments/assets/f7f08750-13d5-4fa1-90db-561ae564022d" />

Para la interacción con el usuario debemos modificar el archivo home.page.html que contendra un botón que llamará la funcion asíncrona que hemos creado anteriormente de la siguiente manera:

<img width="548" height="365" alt="image" src="https://github.com/user-attachments/assets/7a6514c6-0b6c-436d-8ce2-409660c4c20d" />

## 3) Guardar cambios y verificar

Ejecutamos el comando "ionic build" para reconstruir toda la app de angular dentro de la carpeta "www" incluyendo las modificaciones en los archivos .html y .ts.

Sincronizamos cambios con Android Studio y en la pestaña "Build" seleccionamos la opción Clean Project recomendable si es la primera vez.

Y ejecutamos nuestra app.

## Resultado















