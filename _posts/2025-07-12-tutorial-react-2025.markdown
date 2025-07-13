---
layout: post
title:  "Tutorial React"
date:   2025-07-12 18:58:09 -0600
categories: jekyll update
---
# Tutorial: Introducción y Aplicación de React

![logo react]({{ '/assets/images/react-logo.jpg' | relative_url }})

## 1. Justificación del Framework

### 1.1 ¿Para qué sirve?
React es un framework que sirve para el desarrollo de interfaces de usuario dinámicas y eficientes, mediante la creación de componentes reutilizables que responden a cambios en los datos en tiempo real. Está especialmente diseñado para aplicaciones de una sola página (SPA), mejorando la experiencia del usuario al evitar recargas completas del navegador.

### 1.2 ¿Qué aplicaciones tiene?
- Aplicaciones web interactivas  
- Dashboards de administración  
- Aplicaciones móviles (a través de React Native)
- Aplicaciones de IoT  
- Sitios de comercio electrónico  
- Sistemas educativos, redes sociales, plataformas de streaming, entre otras.

![aplicaciones web]({{ '/assets/images/app.jpg' | relative_url }})

### 1.3 ¿Sobre qué lenguajes se apoya?
- **JavaScript**: Lenguaje base de React  
- **JSX**: Sintaxis que combina JavaScript con HTML para describir interfaces  
- **HTML y CSS**: Para estructurar y estilizar las vistas

![logo javascript]({{ '/assets/images/JavaScript-logo.png' | relative_url }})

### 1.4 ¿Qué prerrequisitos necesita?
- Conocimientos básicos de JavaScript 
- Familiaridad con HTML y CSS  
- Manejo básico de la terminal o línea de comandos  
- Instalación de Node.js y npm

![logo node.js]({{ '/assets/images/node-js-logo.png' | relative_url }})

## 2. Instalación

### 2.1 ¿Se precisa instalación?
La respuesta es ¡Sí!. Para usar React, es necesario tener Node.js y npm instalados, ya que se trabaja en un entorno de desarrollo local y se utilizan herramientas modernas de construcción como Webpack y Babel.

![babel webp]({{ '/assets/images/webpack-babel.png' | relative_url }})

### 2.2 Pasos necesarios para la instalación de React.

{% highlight ruby %}
1. Descargar e instalar Node.js desde https://nodejs.org/
2. Verificar instalación con:
   node -v
   npm -v
3. Crear un nuevo proyecto con:
   npx create-react-app mi-app
4. Ingresar a la carpeta del proyecto:
   cd mi-app
5. Ejecutar la app:
   npm start
{% endhighlight %}



### 2.3 ¿Versiones necesarias?
- Node.js versión ≥ 14  
- npm versión ≥ 6  
- React versión actual estable (≥ 18)

### 2.4 Rutas para tener en cuenta:
- **src/**: Código fuente de la app  
- **public/**: Archivos estáticos  
- **node_modules/**: Dependencias instaladas

![rutas app]({{ '/assets/images/rutas-app.jpg' | relative_url }})

### 2.5 ¿Variables de entorno?
LAs variables de entorno son pares de clave-valor configuradas conforme al sistema operativo donde se ejecuta el programa. React permite definir variables de entorno en archivos `.env` sin necesidad de modificar el código fuente. Esos archivos se almacenan en la raíz del proyecto y contiene el prefijo REACT_APP_

Por ejemplo:

{% highlight ruby %}

REACT_APP_API_URL=https://api.misitio.com

{% endhighlight %}

Se puede acceder en el código mediante estos comandos:

{% highlight ruby %}

const apiUrl = process.env.REACT_APP_API_URL;
console.log('API:', apiUrl);

{% endhighlight %}

- Es necesario reiniciar el servidor (npm start) tras modificar un archivo `.env`
- Las variables solo están disponibles durante el tiempo de compilación; no se pueden cambiar dinámicamente en el cliente.
- Para scripts de npm con variables, se recomienda usar `cross-env`

{% highlight ruby %}

package.json
"scripts": {
  "start": "cross-env REACT_APP_MODE=dev react-scripts start"
}

{% endhighlight %}

### 2.6 ¿Necesita base de datos?
No directamente. Ya que React se encarga de la interfaz. Para bases de datos, se puede conectar con APIs o servicios externos como Firebase, MongoDB Atlas o RESTful APIs.

### 2.7 Otras consideraciones
- El navegador debe tener soporte para JavaScript moderno.  
- Es útil contar con un editor como VS Code para facilitar el desarrollo.  

![logo vscode]({{ '/assets/images/vscode-logo.jpg' | relative_url }})

## 3. Primeros pasos

### 3.1 ¿Cómo realizar una primera aproximación (“Hola Mundo”)?
Edita el archivo `src/App.js` con el siguiente código:


{% highlight ruby %}
jsx
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          🌎¡Hola Mundo desde React!🌎
        </p>
        <p>  
          🎉Mi primera aplicación en React está funcionando.🎉
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
{% endhighlight %}


Guarda los cambios y abre `http://localhost:3000` en tu navegador para ver el resultado.

![hola mundo]({{ '/assets/images/hola-mundo-react.jpg' | relative_url }})

## 4. Utilización del Framework

### 4.1 ¿Cómo empezar a crear una aplicación base?
Usa el comando:

{% highlight ruby %}
bash
npx create-react-app nombre-proyecto
{% endhighlight %}


Esto generará una estructura base con todas las configuraciones necesarias. Luego, modifica `App.js` y `App.css` para personalizar tu aplicación.

### 4.2 ¿Cómo visualizar los resultados de la ejecución?
Usa el comando:

{% highlight ruby %}
bash
npm start
{% endhighlight %}

desde la raíz del proyecto. Esto abrirá un servidor local en `http://localhost:3000` con recarga automática al modificar archivos.

## 5. Explicación del funcionamiento del Framework

### 5.1 ¿Actúa sobre páginas, ficheros, secciones…?
React actúa sobre el **DOM virtual (Virtual DOM)**, una representación ligera del DOM real. A través de componentes, renderiza secciones dinámicamente en la página principal. En una SPA, todas las vistas se gestionan desde un único archivo HTML.

### 5.2 ¿Cómo se editan/modifican los ficheros que actúan en el framework?
Los archivos clave están en `src/`:
- `App.js`: Componente raíz  
- `index.js`: Punto de entrada principal  
- `App.css`: Estilos globales del componente  

Se pueden crear más componentes en `src/components/` y luego importarlos donde se necesiten.

Para crear o editar componentes se pueden seguir los siguientes puntos:

- Crea un archivo en `src/components/` por ejemplo `MyComponent.js`
- Define el componente:

{% highlight ruby %}
import React from 'react';

function MyComponent() {
  return Componente creado;

export default MyComponent;

}

{% endhighlight %}

- Importa y usa el componente en `App.js`

{% highlight ruby %}
import MyComponent from './components/MyComponent';

function App() {
  return (
    <div>
      <MyComponent />
    </div>
  );
}
export default App;

{% endhighlight %}

Cada ves que se guardan cambios, el servidor aplicará `Hot Reloading` para reflejar inmediatamente las modificaciones sin recargar la página manualmente.

### 5.3 ¿Cómo se referencian los ficheros creados desde otras aplicaciones (si es el caso)?  
Para consumir APIs u otros recursos externos:

{% highlight ruby %}
js
fetch('https://api.misitio.com/datos')
  .then(response => response.json())
  .then(data => console.log(data));
{% endhighlight %}


También se pueden importar módulos con `import` y consumirlos como componentes o funciones.

### 6 Conclusiones
Con este tutorial puedes entender que es React, para que sirve y como instalarlo. De igual forma se pudieron observar las diferentes aplicaciones que puede tener al implementarse. Como se estructura un proyecto y las variables de entorno que puede contener. 

De forma práctica se realizo una pequeña aplicación que es el siempre confiable `Hola Mundo`, donde se pudo manejar el código y los estilos disponibles en react. Esto de forma local con `npm start` y visualizar de forma sencilla mediante `http://localhost:3000`.

Este tutorial es solo la base para poder comprender este Framework y como iniciar su uso. Por lo que es recomendable revisar los próximos pasos para sacar provecho te esta tecnología.


Para mas recursos [React Learn][react-learn] contiene información de interés. También se puede acceder a [React Oficial][react-oficial]. 

[react-learn]: https://react.dev/learn
[react-oficial]:   https://es.reactjs.org/

