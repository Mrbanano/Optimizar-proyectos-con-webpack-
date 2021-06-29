<div align="center">
<img width="200px"  src="https://miro.medium.com/max/2400/1*xQCjgB2DVqhtqGoGw9E6TQ.png" />

# webpack
</div>



[webpack](https://webpack.js.org/)

# Optimizar proyectos con webpack 

## 🎲 ¿Qué es Webpack?

<br>

Module bundlers son herramientas de frontend que nos permiten usar archivos con módulos JavaScript, entre otras características y convertiros a un JavaScript el cual el navegador pueda entender.

Nos ayudan a optimizar el codigo y estandarizarlo para la web, asi como empaquetarlo para darle mayor robustes a nuestros desarollos.

Es muy util ya que empaqueta los modulos necesarios lo que facilita su despliegue en produccion.

fue creado en  el 2012

<br>

### Webpack 

<br>

webpack es un paquete de módulos de JavaScript de código abierto. Está hecho principalmente para JavaScript, pero puede transformar activos de front-end como HTML, CSS e imágenes si se incluyen los loaders correspondientes. webpack toma módulos con dependencias y genera archivos estáticos que representan esos módulos.

<br>

### Instalacion 

<br>

la instacion es sensilla pero requiere de node, npm o yard el que sea de tu preferencia y un proyecto nuevo o uno ya existente 

<br>


1.  **Proyecto nuevo** 


    > Opcional usar git yo recomiendo que si  

    <br>
    
    1. Inicializamos un repositorio.

        ```console
        git init 
        ``` 

    1. Inicializamos un proyecto de node, si pasas -y se configura por defecto, si no deberas introducir los datos del proyecto

        ```console
        npm init -y
        ``` 
    1. Instala el core de webpack como dependencia de desarollo 

        ```console
        npm install --save-dev webpack
        # o una version especifica
        npm install --save-dev webpack@<version>
        ``` 

    1. Instal el webpack cli 
        ```console
        npm install --save-dev webpack-cli
        ``` 
    1. Listo 

    Ahora dispones de webpack en tu proyecto.

<br>

1.  **Proyecto ya iniciado** 
    
    1. Instala el core de webpack como dependencia de desarollo 
        ```console
        npm install --save-dev webpack
        # o una version especifica
        npm install --save-dev webpack@<version>
        ``` 

    1. Instal el webpack cli 
        ```console
        npm install --save-dev webpack-cli
        ``` 

    1. Listo 
    
    Ahora dispones de webpack en tu proyecto.

<br>
     
### Mas sobre webpack 

<br>

- Webpack nos permite trabajar con:
    - HTML
    - CSS
    - JavaScript
    - Archivos estáticos
    - Imágenes
    - Fuentes

<br>

Webpack trabaja con base en 2 modos: 

1.  **Development** 
    
    * Este modo convierte tu codigo en una version explicita donde podras debugger mas facil y ver de manera transparente como se comporta tu codigo.

   <br>

```console
    npx webpack --mode development
``` 

2.  **Production** 
    
    * Este modo convierte tu codigo en una version minificada y con las configuraciones adecudas en la version mas efeciente y optimizada de tu proyecto .

   <br>

```console
    npx webpack --mode production
``` 

<div align="center">

**Apartir de la version 4 de webpack no es necesario un archivo de configuracion, pero mas adelante lo crearemos y vamos a configurar**

</div>


<br>

- Empresas que lo utilizan :
    - Twitter
    - Instagram
    - Paypal


<br>

- También nos permite
    - Gestionar dependencias
    - Ejecutar tareas
    - Conversión de archivos

<br>

- Webpack soporta módulos de JS en formato:

    - AMD
    - Common JS  
    - ES15

<br>

## 📖 Conceptos básicos

<br>

Todos estos conceptos se aplican para la configuracion de **webpack**, esta configuracion se realiza en el archivo :

> webpack.config.js

Este archivo debe estar ubicado en la raiz del proyecto y de no ser asi deberas crearlo.

<br>

### Entry (punto de entrada): 

Esta propiedad como su nombre lo indica sera el punto de entrada de tu proyecto, es el archivo donde arranca tu aplicacion, por lo general en proyectos de JS suele ser el  `Index.js` o  `App.js`.

Tambien se puede contar con multiples puntos de entrada.

Esta propiedad en su configuracion mas basica requiere un objeto de configuracion el cual contiene un `path` (la ruta de destino) 

```js
    module.exports = 
    {
        entry: "./src/index.js",
    }
```

<br>

### Dist: 

Esta es un convencion para nombrar la carpeta donde estara contenido el resultado del procesamiento de webpack, su nombre es el diminutivo de distribution.

<br>

### Output (punto de salida): 

Esta propiedad como tambien su nombre lo indica sera el punto de salida del proceso de empaquetado, es decir es el lugar al que sera volcado todo el proyecto una vez este listo.

Esta propiedad en su configuracion mas basica requiere un objeto de configuracion el cual contiene un `path` (la ruta de destino) y un el nombre de archivo que se asigaremos. 

```js
    module.exports = 
    {   
        entry: "./src/index.js",
        //path(ruta de destino)y filename(nombre del archivo) 
        output: 
        {
            path: path.resolve(__dirname, "dist"),
            filename: 'main.js',
        }
    }
```

<br>

### Loader (transformador): 

En esta propiedad podremos configurar paquetes de js  que añaderan formatos admitdos a webpack,ampliando la compatilidad de webpack a mayor numero de formatos de archivos.

la configuracion depende de cada uno ya que son paquetes de terceros o muy especificos.  

<br>

### Plugins (complementos): 

Nos van a ayudar a extender las funcionalidades con los loaders, añadir otras configuraciones extendidas permitiendonos ser extemadamente espeficifico a la hora de indicar que archivos, con que formato y en que lugar deben ser procesador.



Hay loader que no necesitan plugins y plugins que no necesitan loader, la mayoria de estas funcionalidades extendidas y complemetarias deberan ser instaladas desde un manejador de paquetes y guardadas como dependencias de desarollo, su configuracion e implementacion dependera del creador.

<br>
<br>

<div align="">
<img width="160px"  src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/02/Babel_Logo.svg/640px-Babel_Logo.svg.png" />
</div>


## Babel 

<br>

lo que se buscar realizar con webpack es volver nuestro proyecto lo mas optimizado posible, liviano, rapido y compatible, basado en estos objetivos vamos a utilizar otra herramienta que nos ayudara alcanzar este objetivo.

<br>

### ¿Que es babel?

<br>

En sus propias palabras "El compilador para JavaScript de próxima generación." para comprender esto debemos saber que Javascrip es regido por versiones que son lanzadas cada año y los navegadores al ser de diferentes emprezas implementas diferentes versiones de js, desfasando funcionalidades y compatibilidad.

la tarea que desempeña babel es tomar codigo de js moderno y compilarlo a javascript que este soportado por todos los navegadore dotandonos de lo mejor de los 2 mundos, escribir codigo moderno que nos permite aplicar mejores practicas y tener un proyecto que sera compatible con todos los navegadores.

<br>

### Instalacion 

<br>

Dentro de tu proyecto abriras tu consola e instalaras los siguientes paquetes.

```console
 npm install --save-dev babel-loader @babel/core @babel/preset-env @babel/plugin-transform-runtime
```

#### **@babel/core**

Instala el nucreo, el core de babel, es indispensable para que fincione. 

#### **@babel/preset-env**

Adiciona anuestro proyecto con la capacidad de traducir las ultimas caracteristicas de js 

#### **babel-loader**

Loader encargado de conectar babel con webpack 

#### **@babel/plugin-transform-runtime**

Este plugin implmenta compilacion en tiempo de ejecucion,esto es util para el manejo del asincronismo de js, utiliza async y await

<br>

### Configuracion 

<br>

La configuracion de babel vive en el archivo
> .babelrc

que vive en la raiz del proyecto  de no existir vamos a crearlo y dentro pondremos los siguiente :

<br>

```js
{
  "presets": [
    "@babel/preset-env"
  ],
  "plugins": [
    "@babel/plugin-transform-runtime"
  ]
}

```

Una vez realizada la configuracion basica de **babel** vamos a indicarle a webpack que vamos a usar babel,
abrimos el archivo 

> webpack.config.js

y ponermo la el siguiente bloque, debajo de lo que configuramos en **conceptos basicos**

```js
{
...,
module: {
    rules: [
      {
        // Test declara que extensión de archivos aplicara el loader
        test: /\.js$/,
        // Use es un arreglo u objeto donde dices que loader aplicaras
        use: {
          loader: "babel-loader"
        },
        // Exclude permite omitir archivos o carpetas especificas
        exclude: /node_modules/
      }
    ]
  }
}
```

<br>

<div align="">
<img width="75px"  src="https://clipground.com/images/html-logo-png-3.png" />
</div>


## Optimizar e infectar Html


### HtmlWebpackPlugin
Es un plugin para inyectar javascript, css, favicons, y nos facilita la tarea de enlazar los bundles a nuestro template HTML.

1. ### Instalación

    1. Abrimos nuestra terminar en nuestro proyecto  e instalamos:
        ```console
        npm i --save-dev  html-webpack-plugin 
        ```
    1. En el archivo
       > webpack.config.js 
    1. Vamos a importar este plugin   
        ```js
            const HtmlWebpackPlugin = require('html-webpack-plugin')
        ```
    1. Debajo del modulo vamos a configurar el plugin
        ```js
            // SECCION DE PLUGINS
            plugins: [
            new HtmlWebpackPlugin({ // CONFIGURACIÓN DEL PLUGIN
                inject: true, // INYECTA EL BUNDLE AL TEMPLATE HTML 
                template: './public/index.html', // LA RUTA AL TEMPLATE HTML
                filename: './index.html' // NOMBRE FINAL DEL ARCHIVO
             })
            ]
        ```
    

Si tu proyecto ya injectaba js con la etiqueta scrip deberas borrarla pues esto ya lo hace automatico 

<br>

<div align="">
<img width="50px"  src="https://3.bp.blogspot.com/-oRSUw_TmO9o/XIb61m88fcI/AAAAAAAAIq0/vnxl2zzsXEQsnHI2fH4GjKu_ZT0urRo4wCK4BGAYYCw/s1600/icon%2Bcss%2B3.png" />
</div>


## Optimizar e infectar CSS

Un preprocesador CSS es un programa que te permite generar CSS a partir de la syntax única del preprocesador. Existen varios preprocesadores CSS de los cuales escoger, sin embargo, la mayoría de preprocesadores CSS añadirán algunas características que no existen en CSS puro, como variable, mixins, selectores anidados, entre otros. Estas características hacen la estructura de CSS más legible y fácil de mantener.

procesadores son herramientas que procesan el CSS y lo transforman en una nueva hoja de CSS que le permiten optimizar y automatizar los estilos para los navegadores actuales.

Para dar soporte a CSS en webpack debes instalar los siguientes paquetes


```console
npm i --save-dev mini-css-extract-plugin css-loader 
```

#### **css-loader**

Loader para reconocer CSS
#### **mini-css-extract-plugin** 

Extrae el CSS en archivos

Para comenzar debemos agregar las configuraciones de webpack
```js
const MiniCssExtractPlugin = require('mini-css-extract-plugin');

module.exports = {
	...,
	module: {
    rules: [
      {
        test: /\.(css|styl)$/i,
        use: [
          MiniCssExtractPlugin.loader,
          "css-loader",
        ]
      }
    ]
  },
  plugins: [
		...
    new MiniCssExtractPlugin(),
  ]
}
```

Si deseamos posteriormente podemos agregar herramientas poderosas de CSS como ser:
- pre procesadores
- Sass
- Less
- Stylus
- post procesadores
- Post CSS


<br>
<br>
    
<div align="">
<img width="50px"  src="https://i.postimg.cc/fLS5x7zc/galeria.png" />
</div>


## Optimiza Imagenes 

el primer paso para optimizar las imagenes es moverla del projecto a la carpeta final eso lo haremos un el siguiente plugin.

### copy-webpack-plugin
 
Para instalarlo debemos ejecutar el comando

```console
npm i  --save-dev copy-webpack-plugin
```

Debemos configurarlo para empezar en este ejemplo estamos moviendo toda la carpeta. 
> webpack.config.js 

```js
...
const CopyPlugin = require('copy-webpack-plugin');

module.exports = {
	...
  plugins: [
    new CopyPlugin({
      patterns: [
        {
          //DONDE ESTAN LAS IMAGENES
          from: path.resolve(__dirname, "src", "assets/images"),
          //A DONDE LAS MOVERA
          to: "assets/images"
        }
      ]
    }),
  ]
}

```
Si tu proyecto ya tenia imganes enlazadas a la una carpera del proyecto deberas mover esa dirrecion a la nueva


## Imagenes como variables 

Este es uno de los loaders que no necesitan instalacion y nos permite convertir las imagenes a variables, vamos a configurar en el 
> webpack.config.js 

```js
module.exports = {
	...
  module: {
    rules: [
      {
        test: /\.png/,
        type: "asset/resource"
      }
    ]
  },
}
```
Una vez realizada la configuracion ya podemos utilizar las imagenes de la siguiente manera:

Importamos el nuevo recurso 
```js
import github from '../assets/images/github.png';
```
Dentro de Js 
```js
 <img src=`${github}` />;
```



```js
```
