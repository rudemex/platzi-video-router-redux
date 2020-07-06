# Platzi Video - React - Router - Redux

#### Clase 5 - BrowserRouter

El primer componente que debemos ver a fondo y manipular será el BrowserRouter, este enrutador cuenta con diferentes propiedades para ser configurado:

- basename: configura la url base de todas las rutas.
- getUserConfirmation: recibe una función con la cual puedes validar si el usuario quiere dejar la pagina en la que se encuentra.
- forceRefresh: es un booleano, como su nombre lo indica en caso de ser verdadero se forzará a que el navegador recargue cuando se navegue.
- keyLength: un key es el id único que recibe cada movimiento en la navegación, keyLength se encarga de configurar la longitud de cada key y por defecto tiene una longitud de 6 caracteres.
- children: es lo que estará dentro de nuestro BrowserRouter.
Todo esto lo encontraras en su [documentación original de React Router](https://reactrouter.com/web/api/BrowserRouter).

Dentro de nuestro proyecto debemos envolver nuestros componentes principales dentro del BrowserRouter.

#### Clase 6 - Tipo de enrutadores

React Router es una librería más que añadimos a nuestro stack, lo más básico que debemos aprender de React Router son sus distintos enrutadores:

- **BrowserRouter:** Es el enrutador que quizá más tiempo utilices como frontend, usa el HTML5 history API lo que quiere decir que es el enrutador que nos da la posibilidad de cambiar las rutas en el navegador.
- **HashRouter:** Funciona similar al BrowserRouter, pero usa un hash **(#)** al inicio de cada url.
- **MemoryRouter:** Mantiene el historial de búsqueda en memoria y te sirve para realizar pruebas sin navegador. En este curso no haremos pruebas unitarias por lo tanto no veremos este enrutador.
- **StaticRouter:** Nunca cambia de dirección, es perfecto para realizar Server Side Render.
- **NativeRouter:** Es el router que nos servirá si queremos usar React Native, **NO** lo veremos en este curso. Es recomendable usar en su lugar [React Navigation](https://platzi.com/clases/react-navigation/).

#### Clase 7 - Link NavLink

BrowserRouter no hará mucho si no esta acompañado de enlaces y rutas, empecemos hablando de los enlaces que se llaman Link y NavLink. Estos funcionan de manera similar a las anclas <a> </a> de HTML.

**Link** cuenta con las siguientes propiedades:

- to: similar al href de <a>, puede recibir un string indicando la ruta a donde va a mandar o bien recibir un objeto con: pathname, un string que representa la ruta a donde se dirige; search, un string que representa el query de una url; hash, un hash para poner en la url; y por último state, un objeto que representa un estado en la navegación.

- replace: similar a to, pero en lugar de añadir una nueva ruta al stack del historial de navegación, reemplaza la ultima ruta por la nueva ruta.

- innerRef: es una forma de obtener el elemento HTML del componente, funciona igual que el ref de React.


**NavLink** es una versión especial de Link, cuenta con varias características más poderosas como, por ejemplo:


- activeClassName: cuando se navegue a la ruta que dirija el NavLink, esta propiedad añadirá al className del componente el string que le pasemos.
- activeStyle: similar a activeClassName, pero con estilos en línea.
- isActive: es una función que se mandara cuando naveguemos a la ruta del NavLink.
- exact: recibe un booleano, sirve para marcar si dirige a una ruta exacta. Se vera a mayor profundidad cuando manejemos rutas.
- strict: recibe un booleano, sirve para marcar si dirige a una ruta estricta. Se vera a mayor profundidad cuando manejemos rutas.
- location: sirve para poder hacer la comparación de isActive con alguna otra ruta.

Vamos a implementar estos componentes dentro del componente Header, dicho componente lo encontraras en el sistema de archivos. Importamos y añadimos Header junto al componente de Videos que se encuentra dentro del archivo app.js.

Recuerda importar **Fragment**, este es un componente que devuelve múltiples elementos. Fragment te permite agrupar multiples children sin agregar nodos adicionales al DOM.

#### Clase 8 - Route

Aun no estas cambiando nada dentro de la interfaz, solamente se esta cambiando la url. Para poder cambiar la interfaz acorde a la url usaremos **Route**, algunas propiedades son:

- component: que componente quieres renderizar.
- path: indica la ruta en la cual va a renderizar el componente que le pases.
- render: es una alternativa a componente, puedes hacer un renderizado en forma de función como en los componentes de React.
- children: son los hijos o componentes que tenga anidado.
- exact: recibe un booleano, si le indicas que es verdadero solo hará match si la ruta coincide exactamente con la ubicación, no hará caso a ninguna sub-ruta.
- strict: recibe un booleano, si le indicas que es verdadero solo hará match si la ruta a la que te diriges es idéntica a la ruta del Route.
- sensitive: recibe un booleano, si le indicas que es verdadero activara el case sensitive para la ruta.
Vamos a cambiar el nombre del componente Videos por Videos y añadiremos un nuevo componente Videos que encontraras en el sistema de archivos, por último, configuramos sus componentes Route.

#### Clase 11 - Redirect y Switch

Habrás notado que nuestro componente NotFound se está renderizando a la vez que el componente Home. Esto sucede porque la Route de NotFound está haciendo match con la de Home, para resolverlo debemos implementar Switch como componente padre de nuestros componentes Route.

**Switch** se encarga de solo renderizar el primer componente que haga match con la ruta que estés designando.

El componente **Redirect** nos ayudara para realizar un redireccionamiento en el navegador, sus principales parámetros son from y to que sirven para indicar de que ruta van a redirigir hacía que ruta van a realizar el redireccionamiento.

Para no entrar en problemas del Server Side Render añadiremos un nuevo NavLink dentro de nuestro Header para poder realizar el redireccionamiento.