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
        mrbanano@pc:~$ git init 
        ``` 

    1. Inicializamos un proyecto de node, si pasas -y se configura por defecto, si no deberas introducir los datos del proyecto

        ```console
        mrbanano@pc:~$ npm init -y
        ``` 
    1. Instala el core de webpack como dependencia de desarollo 

        ```console
        mrbanano@pc:~$ npm install --save-dev webpack
        # o una version especifica
        mrbanano@pc:~$ npm install --save-dev webpack@<version>
        ``` 

    1. Instal el webpack cli 
        ```console
        mrbanano@pc:~$ npm install --save-dev webpack-cli
        ``` 
    1. Listo 

    Ahora dispones de webpack en tu proyecto.

<br>

1.  **Proyecto ya iniciado** 
    
    1. Instala el core de webpack como dependencia de desarollo 
        ```console
        mrbanano@pc:~$ npm install --save-dev webpack
        # o una version especifica
        mrbanano@pc:~$ npm install --save-dev webpack@<version>
        ``` 

    1. Instal el webpack cli 
        ```console
        mrbanano@pc:~$ npm install --save-dev webpack-cli
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
    mrbanano@pc:~$ npx webpack --mode development
``` 

2.  **Production** 
    
    * Este modo convierte tu codigo en una version minificada y con las configuraciones adecudas en la version mas efeciente y optimizada de tu proyecto .

   <br>

```console
    mrbanano@pc:~$ npx webpack --mode production
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

<div align="center">
<img width="100px"  src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/02/Babel_Logo.svg/640px-Babel_Logo.svg.png" />
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
 mrbanano@pc:~$ npm install   --save-dev babel-loader @babel/core @babel/preset-env @babel/plugin-transform-runtime
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




