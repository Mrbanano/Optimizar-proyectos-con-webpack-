<div align="center">
<img width="200px"  src="https://miro.medium.com/max/2400/1*xQCjgB2DVqhtqGoGw9E6TQ.png" />

# webpack
</div>



[webpack](https://webpack.js.org/)

# Optimizar proyectos con webpack 

## 馃幉 驴Qu茅 es Webpack?

<br>

Module bundlers son herramientas de frontend que nos permiten usar archivos con m贸dulos JavaScript, entre otras caracter铆sticas y convertiros a un JavaScript el cual el navegador pueda entender.

Nos ayudan a optimizar el codigo y estandarizarlo para la web, asi como empaquetarlo para darle mayor robustes a nuestros desarollos.

Es muy util ya que empaqueta los modulos necesarios lo que facilita su despliegue en produccion.

fue creado en  el 2012

<br>

### Webpack 

<br>

webpack es un paquete de m贸dulos de JavaScript de c贸digo abierto. Est谩 hecho principalmente para JavaScript, pero puede transformar activos de front-end como HTML, CSS e im谩genes si se incluyen los loaders correspondientes. webpack toma m贸dulos con dependencias y genera archivos est谩ticos que representan esos m贸dulos.

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
    - Archivos est谩ticos
    - Im谩genes
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

- Tambi茅n nos permite
    - Gestionar dependencias
    - Ejecutar tareas
    - Conversi贸n de archivos

<br>

- Webpack soporta m贸dulos de JS en formato:

    - AMD
    - Common JS  
    - ES15

<br>

## 馃摉 Conceptos b谩sicos

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

En esta propiedad podremos configurar paquetes de js  que a帽aderan formatos admitdos a webpack,ampliando la compatilidad de webpack a mayor numero de formatos de archivos.

la configuracion depende de cada uno ya que son paquetes de terceros o muy especificos.  

<br>

### Plugins (complementos): 

Nos van a ayudar a extender las funcionalidades con los loaders, a帽adir otras configuraciones extendidas permitiendonos ser extemadamente espeficifico a la hora de indicar que archivos, con que formato y en que lugar deben ser procesador.



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

### 驴Que es babel?

<br>

En sus propias palabras "El compilador para JavaScript de pr贸xima generaci贸n." para comprender esto debemos saber que Javascrip es regido por versiones que son lanzadas cada a帽o y los navegadores al ser de diferentes emprezas implementas diferentes versiones de js, desfasando funcionalidades y compatibilidad.

la tarea que desempe帽a babel es tomar codigo de js moderno y compilarlo a javascript que este soportado por todos los navegadore dotandonos de lo mejor de los 2 mundos, escribir codigo moderno que nos permite aplicar mejores practicas y tener un proyecto que sera compatible con todos los navegadores.

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
        // Test declara que extensi贸n de archivos aplicara el loader
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
<img width="90px"  src="https://clipground.com/images/html-logo-png-3.png" />
</div>


## Optimizar e infectar Html


### HtmlWebpackPlugin
Es un plugin para inyectar javascript, css, favicons, y nos facilita la tarea de enlazar los bundles a nuestro template HTML.

1. ### Instalaci贸n

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
            new HtmlWebpackPlugin({ // CONFIGURACI脫N DEL PLUGIN
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

Un preprocesador CSS es un programa que te permite generar CSS a partir de la syntax 煤nica del preprocesador. Existen varios preprocesadores CSS de los cuales escoger, sin embargo, la mayor铆a de preprocesadores CSS a帽adir谩n algunas caracter铆sticas que no existen en CSS puro, como variable, mixins, selectores anidados, entre otros. Estas caracter铆sticas hacen la estructura de CSS m谩s legible y f谩cil de mantener.

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

<br>

<div align="">
<img width="50px"  src="https://i.postimg.cc/hPgD5cJm/folder.png" />
</div>


## Optimizar e infectar Fuentes

La forma comun de utilizar fuentes en un proyecto web es consumirla desde algun CDN descargando desde los servidores ya sea de google o servicios externos, pero esto penzaliza en algunos casos equipos con poca conexion. 

Para poder optimizar este apartado podemos aplicar 2 metodos uno sin instalacion y sin instalacion. 


1.  ### Sin Instalacion
    1.  Abrimos el archivo
        > webpack.config.js 
    2.  Lo configuramos de la siguiente manera 
    ```js
    {
        test: /\.(woff|woff2)$/,
        type: "asset/resource",
        generator: {
          filename: "assets/fonts/[name][ext]"
        }
    }
    ```
1. ### Con Instalacion

    1. Vamos a instalar los siguientes plugins
        ```console
        npm i  --save-dev url-loader file-loader
        ```
    1. Abriremos el archivo
    1. Lo configuraremos de la siguiente manera:
        ```js
        module.exports = {
            ...
        module: {
            rules: [
                    ...
            {
                test: /\.(woff|woff2)$/,
                use: {
                loader: "url-loader",
                options: {
                    // limit => limite de tama帽o
                    limit: 10000,
                    // Mimetype => tipo de dato
                    mimetype: "application/font-woff",
                    // name => nombre de salida
                    name: "[name].[ext]",
                    // outputPath => donde se va a guardar en la carpeta final
                    outputPath: "./assets/fonts/",
                    publicPath: "./assets/fonts/",
                    esModule: false,
                }
                }
            }
            ]
        },
            ...
        }
        ```
    1. En los archivos Css vamos a implimentarlo asi:  
        ```css

        @font-face {
            font-family: "Ubuntu";
            src: url("../assets/fonts/ubuntu-regular.woff2") format('woff2'),
                    url("../assets/fonts/ubuntu-regular.woff") format('woff');
            font-weight: 400;
            font-style: normal;
        }
        ```

<br>
<br>

<div align="">
<img width="50px"  src="https://i.postimg.cc/1tJk7hbG/archivo-comprimido.png" />
</div>

## Optimizaci贸n: hashes, compresi贸n y minificaci贸n de archivos

Unos de las razones por que utilizamos webpack es porque nos permite optimizar y comprimir nuestro proyecto

### Instalaci贸n

 ```console
    npm i --save-dev  css-minimizer-webpack-plugin terser-webpack-plugin
```
#### **css-minimizer-webpack-plugin** 
Nos ayuda a comprimir nuestros archivos finales CSS

#### **terser-webpack-plugin** 
Permite minificar de una mejor forma

  1. Instalamos dependencias 
```console
      npm i --save-dev  css-minimizer-webpack-plugin terser-webpack-plugin
```
  2. Abrimos el archivo
     > webpack.config.js 
  1. Importamos los plugins:
      ```js
      const CssMinimizerPlugin = require('css-minimizer-webpack-plugin');
      const TerserPlugin = require('terser-webpack-plugin');
      ```
  1. Debajo de la seccion de plugins creamos: 
      ```js
      module.exports = {
        ...
        optimization: {
          minimize: true,
          minimizer: [
            new CssMinimizerPlugin(),
            new TerserPlugin()
          ]
        }
      }
      ```
Cuando nombremos en la configuraci贸n de webpack es importante usar [contenthash] para evitar problemas con la cache

<br>
<br>

<div align="">
<img width="50px"  src="https://image.flaticon.com/icons/png/512/1161/1161366.png"/>
</div>

## Webpack Alias

<br>

Esta es un configuracion sensilla que se realiza en webpack para otorgarle un nombre a rutas espeficicas para evitar las rutas largas y asigarnes un nombre clave o mejor dicho un alias. 

```js
module.exports = {
	...
	resolve: {
		...
    alias: {
      '@nombreDeAlias': path.resolve(__dirname, 'src/<directorio>'),
    },
	}
}
```
Puedes usarlo en los imports de la siguiente manera
```js
import modulo from "@ejemplo/archivo.js";
```


<br>
<br>


<div align="">
<img width="50px"  src="https://image.flaticon.com/icons/png/512/1022/1022463.png"/>
</div>


<br>

### Variables de entorno 

<br>

1. Instalar dotenv para utilizar variables de entorno
    ```console
      npm i --save-dev dotenv-webpack 
    ```
1. Crearemos en la raiz del proyecto el archivo
     > .env 
1. Crearemos una copia con el nombre 
    > .env.example
1. llenaremos el archivo original y 
    ```js
      NombreDeTuVariable = "Valor de tu variable "
    ```
1. Asi se usa 
    ```js
    const Variable = process.env.NombreDeTuVariable;
    ```

<br>

listo ahora tienes en todo tu proyecto una variable secreta, en el example pon el nombre de la variable por si alguien mas quiere trabajar en el proyecto ve cuales son las variables 



<br>
<div align="">
<img width="50px"  src="https://image.flaticon.com/icons/png/512/1336/1336791.png"/>
</div>


<br>

### Development file 

Es momento de separnos, en este punto haremos una copia de nuestra configuracion.
> webpack.config.js
> webpack.config.dev.js

1. eliminaremos la seccion de optimizacion del segundo archivo 
1. en el package.json crearemos modificaremos el comando dev 
"dev": "webpack --mode development "

    ```js
    "dev": "webpack --mode development --config webpack.config.dev.js"
    ``` 

pero aun falta ver algo jaja

<br>

### webpack watch 
 
 <br>

consiste en monitorear todos los cambios y compilar al detectar algun cambio existen 2 modos de activarlo 

1. en el archivo webpack.config
    ```js
      module.exports = {
	    ...
	    watch: true
      }
    ```
1. en el comando se agrega el flag 
    ```js
     -watch
    ``` 
    Asi quedaria nuestro comando de desarollo:

    ```js
    "dev": "webpack --mode development --config webpack.config.dev.js"
    ``` 


<br>
<br>
<div align="">
<img width="50px"  src="https://image.flaticon.com/icons/png/512/755/755066.png"/>
</div>

<br>

### Production

El proyecto tiene lo minimo basico sobre optimizacion, es momento de mostrarlo al mundo.

 
 <br>

La version de produccion debe ser la mas limpia, optimizad,actualizada y siempre lista para ser mostrada al publico.


## limpiar para produccion 
 
 <br>

Para limpiar todos las compilaciones que se quedan en el dist por estar haciendo pruebas vamos a instalar y configurar una dependincia nueva.

1. Instalacion
    ```console
    npm i --save-dev clean-webpack-plugin
     ```
1. Vamos al archivo
    > webpack.config.js
1. Inicializamos el plugin 
    ```js
    plugins:[
      ...
      new CleanWebpackPlugin(),
    ]
    ```

Listo apartir de ahora la compilacion de produccion solo tendra los archivos de la ultima versio.


<br>
<br>
<div align="">
<img width="50px"  src="https://image.flaticon.com/icons/png/512/2285/2285537.png"/>
</div>


## Deploy 


Hora de mostarle al mundo de lo que somos capaces en este caso particular desplegaremos en Netlify.

1. creamos el archivo en la raiz de proyecto
    > Netflify.toml
1. lo llenamos de esta manera:
    ```js
    [build]
        publish = "dist/"
        command = "npm run build"
    ```

la primer parte ya esta lista, la siguiente la aplicaras si tu proyecto tiene variables de entorno

1. crea un carpeta en la raiz del proyecto 
     >Scrip
1. creamos dentro de ella el archivo
     > create-env.js
1. la llenas con los nombres de variables y donde deberian estar 
    ```js
    const fs = require('fs')

    fs.writeFileSync('./.env', `NombreDeTuVariable=${process.env.NombreDetuVariable}`)
    ```

1. en el dashboard de netlify en la seccion de deploy busca la seccion de variables de entorno y podras, nombre y valor 

Por tu proyecto ya deberia de estar todo listo
queda entrar subir tu codigo a github y enlazar en netlify



