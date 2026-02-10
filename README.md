# Angular

# 1. Introducción a Angular:

Angular es un framework que permite desarrollar aplicaciones web donde el cliente asuma la mayor parte de la lógica y descargue al servidor, con la finalidad de que las aplicaciones ejecutadas a través de Internet sean más rápidas.

Está mantenido por Google lo que favorece su desarrollo, mantenimiento y tiene una fuerte comunicada.

Angular permite crear aplicaciones web de una sola página (**SPA, Single Page Application**), realizando la carga de datos de forma asíncrona.

Las aplicaciones en Angular se encuentran modularizadas en **Componentes** con el objetivo de independizar las diferentes funcionalidades de la aplicación. Cada uno de los **Componentes** se encuentran conformados por una **Plantilla**, una hoja de estilos y un **Controlador** que representa a dicho componentes y desde dónde se manejará su comportamiento.

Tomando como ejemplo una app tipo to-do list: La carcasa que engloba toda la app, la barra de navegación, un listado de tareas, cada una de las tareas, o un editor de tareas… son todo vistas controladas por componentes.

![Component Structure](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/component-structure.png)

Durante este curso vamos a desarrollar una aplicación web llamada Planify dónde pondremos en práctica todos lo aprendido.

## Planify

Planify es una aplicación web desarrollada con Angular cuyo objetivo es facilitar la gestión personal de tareas de manera intuitiva, organizada y visualmente atractiva.

Planify permitirá al usuario crear, visualizar, editar y eliminar tareas, asignándoles distintos niveles de prioridad y estado de progreso. Además, se implementarán funcionalidades adicionales que fomenten la productividad y la planificación diaria, como resúmenes de tareas, filtrado por estado o prioridad, y una interfaz adaptada a diferentes dispositivos (diseño responsive gracias a Bootstrap).


# 2. Creación de un proyecto Angular.

Para poder crear un proyecto en Angular previamente necesitamos tener instalado node y typescript. Además, es necesario instalar Angular CLI, herramienta que nos permitirá crear la estructura de un proyecto Angular.

```jsx
npm install -g  @angular/cli@19.2.19
```

Una vez instalado Angular CLI podremos crear un nuevo proyecto mediante el siguiente comando:

```jsx
ng new <nombre_proyecto>
```

Tras lanzar el comando nos pedirá que indiquemos el lenguaje que usaremos para los estilos CSS y si deseamos usar routing en nuestra aplicación.

Una vez creado nuestro proyecto podemos lanzarlo con el siguiente comando:

```jsx
ng serve
```

Desde este momento todos los cambios que realicemos en nuestra aplicación se desplegarán de manera automática en el servidor.

## RETO. Creación del proyecto Planify
Crea la estructura base del proyecto Planify. Configura correctamente el entorno seleccionando el preprocesador CSS para el estilo de la aplicación y desactivando el SSR. Sube tu proyecto a GitHub para poder gestionar correctamente el control de cambios.

# 3. Estructura de un proyecto Angular

***public/*** :  carpeta que almacena los archivos estáticos como imágenes, fuentes, etc.

***src/** :* carpeta donde se encuentra el código fuente de la aplicación.

***app/***: contiene los componentes, servicios, modelos y otras funcionalidades de la aplicación.

***components/*** : carpeta que contiene los diferentes componentes de la aplicación, mediante la definición de constantes, variables de configuración o parámetros que se usarán en diferentes partes.

***services/*** : carpeta que contiene los servicios que gestionan la lógica de negocio y la comunicación con las APIs.

***models/*** : contiene las interfaces y las clases que definen el modelo de datos.

***pipes/*** : carpeta que almacena los pipes personalizados.

**app.config.ts :** archivo donde se centraliza la configuración de la aplicación.

**app.routes.ts :** archivo que contiene las configuraciones de las rutas. Básicamente una routa o route se usa para mapear un componente a una URL específica.

**index.html** : archivo HTML principal donde se carga la aplicación.

**main.ts** : el punto de entrada de la aplicación, dónde se inicializa el componente principal.

**styles.css** : archivo que contiene los estilos globales de la aplicación.

**angular.json :** archivo de configuración de Angular CLI dónde se definen las opciones del proyecto, cómo, por ejemplo, rutas, estilos, scripts, etc.

**package.json :** contiene las dependencias del proyecto, scripts para ejecutar tareas y metadatos del proyecto.

**tsconfig.json :** archivo de configuración de TypeScript dónde se especifican las opciones para el compilador.

**node_modules/** :  carpeta que contiene las dependencias npm que han sido instaladas.

Dentro de la carpeta src/app se encuentra el componente principal de la aplicación. Cada componente está formado por los siguientes archivos:

- **app.component.ts** → clase dónde se implementará los diferentes métodos y atributos para dotar de funcionalidad a un componente.
    
    Todo componente tiene una clase Controlador decorada con @Component donde se definen propiedades y métodos que están disponibles en su template.
    
    ```jsx
    @Component({
    selector: 'app-root',
    imports: [RouterOutlet],
    templateUrl: './app.component.html',
    styleUrl: './app.component.css'
    })
    ```
    
    ¿Qué opciones de configuración estoy pasando en los metadatos?
    
    - selector: etiqueta que será usada para importar el componente en un documento HTML. En este ejemplo, cuando se use la etiqueta <app-root> <app-root/> se reemplazará por todo el contenido del componente indicado.
    - standalone: marca el componente como independiente.
    - imports: se emplea para especificar otros módulos que necesita el componente. Esto es útil cuando el componente necesita funcionalidades de otros módulos.
    - templateURL: la ruta dónde se encuentra el template que quieres vincular al componente.
    - styleURL: ruta donde se encuentra el archivo que contiene los estilos del componente.
- **app.component.html** → plantilla HTML asociada al componente.
- **app.component.css** → archivo de estilos asociado al componente.
- **app.component.spec.ts** → archivo donde se implementarán las pruebas funcionales del componente.

![Proyect Structure](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/structure.png)

# 4. Instalación de Bootstrap en Angular

Bootstrap es un popular **framework de CSS** que facilita el desarrollo de aplicaciones web con diseños modernos, adaptativos y consistentes. Proporciona una serie de **estilos predefinidos**, **componentes** y **utilidades CSS** para la creación rápida de interfaces atractivas y responsive, es decir, que se adaptan automáticamente a diferentes tamaños de pantalla (escritorios, tablets, móviles, etc.).

## 4.1. ¿Cómo funciona Bootstrap?

Boostrap se basa en un sistema de rejilla o grid. El sistema de **rejilla** (grid) de Bootstrap permite organizar y alinear contenido en una página dividiéndola en hasta **12 columnas** por fila. Este sistema es adaptable y responsive, lo que significa que las columnas se ajustan automáticamente según el tamaño de la pantalla del dispositivo.

La configuración de cada una de las filas y las columnas de la aplicación la realizaremos estableciendo clases a cada uno de los componentes. 

## 4.2. Principios de Bootstrap.

1. Contenedores : 
    - Los contenedores .container o .container-fluid es el elemento principal dónde vamos a introducir las filas y las columnas.
    - `.container` tiene un ancho fijo que se adapta a diferentes tamaños de pantalla, mientras que `.container-fluid` se extiende a todo el ancho de la pantalla.

2. Filas: 

- Dentro de un contenedor, se usa la clase `.row` para crear una fila. Las filas dividen el contenido horizontalmente y organizan las columnas dentro de ellas.
1. Columnas
    - Dentro de cada fila, se agregan columnas usando clases como `.col`, `.col-md-6`, `.col-lg-4`, etc.
    - La rejilla de Bootstrap se basa en un sistema de 12 columnas, así que se pueden combinar diferentes tamaños para lograr distribuciones variadas (por ejemplo, `.col-6` ocupa 6 de las 12 columnas, es decir, la mitad del ancho).
    - Bootstrap incluye clases específicas para diferentes tamaños de pantalla: `.col-sm-` para móviles, `.col-md-` para tabletas, `.col-lg-` para pantallas grandes y `.col-xl-` para pantallas extra grandes.
    - Estas clases permiten que las columnas cambien de tamaño o se reorganicen según el dispositivo, haciendo que el diseño sea responsive.

## 4.3. Instalación de Bootstrap en un proyecto Angular:

Existen varias formas de instalar Bootstrap en un proyecto Angular. La forma en la que nosotros lo realizaremos será instalando la dependencia de node en nuestro proyecto e importando los archivos de Boostrap en el archivo de configuración de `angular.json`.

Para instalar el módulo de Boostrap desde node tenemos que lanzar el siguiente comando desde la terminal de nuestro proyecto:

```tsx
npm install bootstrap@5.3.3
npm install bootstrap-icons
```

Tener en cuenta que mediante `@5.3.3` estamos definiendo la versión que deseamos instalar. También podemos lanzar este mismo comando sin usar `@5.3.3` y se instalará la última versión.

Podemos observar cómo se ha añadido dicha dependencia al archivo `package.json` de nuestro proyecto:

```json
    "bootstrap": "^5.3.3",
```

Una vez instalado el módulo de node, tenemos que indicarle a Angular dónde se encuentra el archivo que contiene los estilos del framework y el archivo de funcionalidades .js. Para ello, modificaremos el archivo `angular.json` y añadiremos las siguientes líneas dentro de `build`.

```json
"styles": [
  "src/styles.css",
  "node_modules/bootstrap/dist/css/bootstrap.min.css",
  "node_modules/bootstrap-icons/font/bootstrap-icons.min.css"
],
"scripts": [
  "node_modules/bootstrap/dist/js/bootstrap.bundle.min.js"
]
```
Para poder probar que Bootstrap funciona correctamente podemos hacer uso de uno de sus iconos en la plantilla de nuestro componente principal. Si aparece el icono del avión tendremos instalado y configurado correctamente Bootstrap.
`<i class="bi bi-airplane-engines"></i>`

Ya tendríamos Boostrap listo para ser usado en nuestro proyecto Angular.

## 4.4. Ejemplo básico:

```html
<div class="container">
<div class="row">
<div class="col-md-4">Columna 1</div>
<div class="col-md-4">Columna 2</div>
<div class="col-md-4">Columna 3</div>
</div>
</div>
```

En este ejemplo las columnas se dividen en partes iguales de 4 columnas cada una (3x4=12 columnas)

En dispositivos medianos y más grandes estas columnas se mostrarán en una sola fila. En dispositivos más pequeños se ajustarán automáticamente en filas de una sola columna.

## RETO: Instalación de Bootstrap.

Realiza la instalación de Bootstrap y Bootstrap Icons en tu proyecto Planify y verifica que este funciona correctamente borrando todo el contenido del archivo app-component.html y añadiendo algún componente de Bootstrap.



# 5. Componentes.

En Angular un componente es una de las piezas fundamentales de la aplicación. Los componentes son bloques de funcionalidades independientes y reutilizables que controlan una parte de la interfaz gráfica de usuario. Como hemos mencionado anteriormente, cada componente tiene su controlador, su plantilla HTML, su hoja de estilos y su archivo de pruebas.

Toda aplicación en Angular cuenta con un componente principal AppComponent, desde donde arranca la aplicación. Sin embargo, se pueden añadir nuevos componentes.

## 5.1. Creación e importación de componentes.

La forma más sencilla que tenemos de crear un componente es usando la consola de Angular, mediante el siguiente comando:

```jsx
ng generate component components/navbar
```

En la anterior línea hemos creado un componente llamado navbar dentro del contenedor components/ para mejorar su organización.

Todo componente cuenta con un selector que nos permitirá utilizarlo dentro de otro componente, por ejemplo, dentro del componente principal. El selector básicamente lo que establece es el nombre de la etiqueta que se deberá usar para importar dicho componente.

Por ejemplo, si accedemos a la clase del componente que hemos creado podremos observar que dentro del decorador @component existe una propiedad llamada selector. Esta es la propiedad que define el nombre de la etiqueta.

```tsx
import { Component } from '@angular/core';
@Component({
  selector: 'app-navbar',
  imports: [],
  templateUrl: './navbar.component.html',
  styleUrl: './navbar.component.css'
})
export class NavbarComponent {
}
```

Para poder usar este componente en nuestro proyecto, primeramente, será necesario añadirlo a la propiedad `imports`  de la clase AppComponent y posteriormente lo importaremos dentro del documento HTML empleando el nombre de su etiqueta.

```tsx
@Component({
  selector: 'app-root',
  standalone: true,
  imports: [RouterOutlet,NavbarComponent],
  templateUrl: './app.component.html',
  styleUrl: './app.component.css',
  
})
```

```html
app-navbar></app-navbar>
```

### RETO. Creación de los componentes de Planify.

El objetivo de este reto es comenzar a crear los diferentes componentes
que conformarán nuestra aplicación Planify y que iremos desarrollando en futuros retos. Para ello, será necesario crear la siguiente estructura de componentes:

`src/app/componentes/` → carpeta que contendrá todos los componentes creados. No es necesario crearla, pero sí indicarla en la ruta a la hora de crear los siguientes componentes.

- `navbar/` → componente que contendrá la barra de navegación de nuestra aplicación. Ejemplo de creación: 
```bash 
ng generate component components/navbar
```
- `home/` → componente que contendrá la pantalla inicial de la aplicación.

- `footer/` → componente que contendrá el footer de nuestra aplicación.

- `auth/` → carpeta que contendrá los componentes de autenticación y registro.

  - `sigin/` → componente de registro.

  - `login/` → componente para iniciar sesión.

- `task/` → carpeta que contendrá los componentes relacionados con la gestión de tareas.

  - `tasklist/` → componente que mostrará todas las tareas

  - `taskform/`→ componente para crear o editar una tarea.

  - `taskresume/` → componente que mostrará de manera resumida una tarea.
    
- `dashboard` -> componente dónde se mostrarán los siguientes componentes hijos.
  
  - `profile` -> componente que mostrará el perfil de un usuario.
  
  - `stats` -> componente que mostrará las estadísticas de un usuario.

El resultado tras la creación de los componentes debe ser el siguiente:


![EstructuraComponentes](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/reto-estructura-componentes.png)


### RETO. Configurando el Navbar y Footer.

Modifica la plantilla de los componentes `navbar` y añade una barra de navegación de Bootstrap. Modifica el HTML del componente de Bootstrap, cambia el nombre de la app y añade las siguientes opciones al menú:
 - Home
 - Tasks
 - Dashboard
 - Signin
 - Login
 - Logout

Modifica la plantilla del componente `footer` y añade un pie de página de bootstrap.

Una vez modificada la plantilla de ambos componentes, importalos en el componente principal `app-component.`. Añade también en medio de ambos componentes el Home. La estructura de componentes deberá quedar así:

![OrganizacionComponentes](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/reto-organizacion-componentes.png)



Tras realizar este reto nuestra aplicación debe tener el siguiente aspecto:

![NavbarFooter](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/reto-navbar-footer.png)

## 5.2. Ciclo de vida de un componente.

Como hemos visto en los apartados anteriores los componentes son una parte de la aplicación que estamos construyendo. Por ejemplo, en Planify, vamos a desarrollar diferentes componentes: 
- TaskListComponent: componente que se encargará de mostrar el listado de tareas.
- TaskFormComponent: componente que se encargará de mostrar el formulario para añadir nuevas tareas.
- NavbarComponent: contiene toda la lógica de la barra de navegación
...

Cada uno de estos componentes nace, cambia y muere durante la ejecución de nuestra aplicación.

### ¿Qué es el ciclo de vida de un componente?

El ciclo de vida de un componente es el conjunto de etapas que atraviesa un componentes desde que se crea hasta que se destruye. Angular nos permite intervenir en cada una de estas etapas mediante métodos especiales denominados **hooks del ciclo de vida**, los cuales Angular activa automáticamente en momentos claves.

### Etapas principales de un componente.

| Etapa | Método | Cuándo se ejecuta | Qué hace |
|-----------|-----------|----------------------|--------------|
| **Creación** | `constructor()` | Cuando Angular crea la instancia del componente | Se inicializan variables e inyectan dependencias. No se debe acceder aún al DOM ni a datos de entrada (`@Input`). |
| **Inicialización** | `ngOnInit()` | Una vez creada la vista y cargados los datos de entrada. Se ejecuta una sola vez. | Se inicializan datos, se hacen peticiones HTTP y se preparan suscripciones. |
| **Cambios en datos de entrada** | `ngOnChanges(changes: SimpleChanges)` | Cada vez que cambia un valor de entrada (`@Input`) | Permite reaccionar ante cambios en propiedades que el componente recibe de su padre. |
| **Detección de cambios** | `ngDoCheck()` | Cada vez que Angular ejecuta el detector de cambios. | Permite detectar cambios más profundos. |
| **Renderizado de la vista** | `ngAfterViewInit()` | Cuando la vista y los elementos hijos (`@ViewChild`) ya se han renderizado | Ideal para acceder al DOM o manipular elementos ya cargados en pantalla. |
| **Destrucción** | `ngOnDestroy()` | Justo antes de que Angular elimine el componente de la vista. Angular destruye un componente cuando ya no se muestra en la página. | Se liberan recursos como suscripciones a observables. |

![CicloComponente](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/ciclo-componente.png)


### Implementación

Para poder implementar los hooks es necesario que la clase del componente implemente a la interfaz de dicho hook y realizar la implementación del método correspondiente. Es muy importante destacar que el constructor no forma parte de los hooks del ciclo de vida de un componente. Un uso muy adecuado de los constructores es inyectar servicios.

  En el siguiente fragmento de código se muestra un ejemplo:

```typescript
export class TaskListComponent implements OnInit, OnDestroy {
  tasks: Task[] = [];
  subscription: any;

  constructor(private taskService: TaskService) {
    console.log('Constructor: componente creado');
  }

  ngOnInit() {
    console.log('ngOnInit: cargando tareas...');
    this.subscription = this.taskService.getTasks().subscribe(data => {
      this.tasks = data;
    });
  }

  ngOnDestroy() {
    console.log('ngOnDestroy: limpiando recursos');
    this.subscription.unsubscribe();
  }
}

```

## Reto: Prueba los ciclos del componente home.

El objetivo de este reto es mostrar en consola el orden en el que Angular ejecuta los principales hooks del ciclo de vida del componente Home. Implementa todas las interfaces estudiadas y sus métodos y muestra por consola un mensaje que identifique cada una de las fases del ciclo de vida.

# 6. Sintaxis de la plantilla(Template Syntax).

En angular cada componente tiene una plantilla asociada dónde se visualizará la información de este. Estas plantillas son archivos .html en cuyo interior podemos encontrar código HTML, sin embargo, también se puede usar una sintaxis especial que permitirá añadirle un comportamiento dinámico a nuestra plantilla.

La sintaxis de las plantillas nos permitirá vincular el HTML con la lógica del componente (TypeScript) creando una interfaz dinámica y reactiva.

## 6.1. Interpolación.

La interpolación es una técnica que se utiliza en Angular para enlazar datos desde el controlador a la vista o plantilla HTML, lo que nos permitirá mostrar valores de las propiedades de un componente de manera dinámica. 

Para poder indicarle al framework que evalué una expresión de controlador usaremos dobles llaves ``{{ expresión }}``

Supongamos que tenemos una propiedad llamada titulo en el controlador del componente Home:

```tsx
import { Component } from '@angular/core';

@Component({
  selector: 'app-home',
  imports: [],
  templateUrl: './home.component.html',
  styleUrl: './home.component.css'
})
export class HomeComponent {

  title = '@joseprofeinformatica';

}

```

En la plantilla interpolaremos el valor de title de la siguiente forma:

```html
<h1>Hola! {{title}}</h1>
```

Al ejecutar este código, el navegador renderizará así:

![Interpolation](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/interpolation.png)

### 6.1.1. Características de la interpolación:

- Permite evaluar expresiones simples de TypeScript:
    
    ```html
    <p>El año es: {{ 2024 }}</p>
    <p>La suma es: {{ 2 + 3 }}</p>
    ```
    
- Permite realizar llamadas a métodos:
    
    ```html
    <p>Mensaje: {{ obtenerMensaje() }}</p>
    ```

## 6.3. Directivas.

Las directivas son instrucciones que le indican al framework cómo renderizar los diferentes elementos. Esto permitirá modificar la estructura del DOM: aplicar estilos, añadir comportamientos, realizar operaciones condicionales, etc.

Las directivas se dividen en tres categorías:

- Directivas Estructurales.
- Directivas de Atributo.
- Directivas Personalizadas.

**IMPORTANTE!** Para poder emplear las directivas es necesario importar el módulo `CommonModule` en la clase del componente.

Para explicar las directivas trabajaremos con un componente que tendrá la siguiente información:

Dado el contenido del controlador:

```tsx
  edad = 40;

  esMayorEdad=true;

  articulos = [
  { codigo: 1, descripcion: 'naranjas', precio: 3 },
  { codigo: 2, descripcion: 'manzanas', precio: 5 },
  { codigo: 3, descripcion: 'peras', precio: 1 },
  { codigo: 4, descripcion: 'plátanos', precio: 2 },
  { codigo: 5, descripcion: 'kiwis', precio: 4 },
  { codigo: 6, descripcion: 'uvas', precio: 3 },
  ];
  
  numeroAleatorio(){
    return Math.floor(Math.random()*3)+1;
  }
```

### 6.3.1. Directivas estructurales:

Son aquellas que cambian la estructura del DOM, es decir, añaden o eliminan elementos según una condición o una lógica determinada. Estas directivas se identifican por el prefijo `*` que indica que Angular debe manejar el DOM de forma especial.

Ejemplos de directivas estructurales:

- `*ngIf`: renderiza un elemento del DOM si se cumple una determinada expresión booleana.

```html
<p *ngIf="esMayorEdad">La persona es mayor de Edad</p>
```

- `*ngFor:` renderiza un conjunto de elementos de forma repetida en función de una colección de objetos.

```html
<table>
<tr *ngFor="let articulo of articulos">
   <td>{{articulo.codigo}}</td>
    <td>{{articulo.descripcion}}</td>
    <td>{{articulo.precio}}</td>
</tr>
</table>
```

- **`*ngSwitch`, `*ngSwitchCase`, y `*ngSwitchDefault`**: Permiten una lógica de control similar a `switch`, donde se evalúa una expresión y se muestra un bloque específico.

```html
<div [ngSwitch]="numeroAleatorio()">
<p *ngSwitchCase="1">El numero es un 1</p>
<p *ngSwitchCase="2">El numero es un 2</p>
<p *ngSwitchDefault>El numero es un 3</p>
</div>
```

### 6.3.2. Nueva sintaxis para el flujo de control (New Control Flow Syntax).
A partir de Angular 17 se introduce una nueva sintaxis para controlar el flujo de nuestros elementos. La principal diferencia es que no es necesario introducirlas dentro de ninguna etiqueta HTML y que usan el caracter `@`. A continuación se muestran varios ejemplos:

- `@if` → nos permitirá controlar si se añadirán bloques de código HTML según si se cumple o no una determinada condición:

```html
@if (edad>=18) {
  <p>Es mayor de edad.</p>
} @else {
  <p>Es menor de edad.</p>
}
```

- `@for` → nos permitirá generar muchos elementos HTML a partir del recorrido de un conjunto de elementos:

```html
  @for(articulo of articulos; track articulo.codigo) {
    <tr>
      <td>{{articulo.codigo}}</td>
      <td>{{articulo.descripcion}}</td>
      <td>{{articulo.precio}}</td>
    </tr>
    }@empty {
      <li> There are no items. </li>
     }
```

- `@switch/@case/@default` → nos permitirá mostrar una estructura de código u otra según la expresión evaluada, así como mostrar una estructura por defecto en el supuesto que no se cumpla ninguna condición. A continuación se muestra un ejemplo de cómo se evalúa la ejecución de una función que genera números aleatorios entre 1 y 3:

```html
  @switch (numeroAletorio()) {
    @case (1) {
      <p>Uno</p>
    }
    @case (2) {
      <p>Dos</p>
    }
    @case (3) {
      <p>Tres</p>
    }
  }
```
### 6.3.3 `ng-container`

`<ng-container>` es un contenedor lógico que no se renderiza en el DOM.
Sirve para agrupar elementos o aplicar directivas estructurales (*ngIf, *ngFor, @if, @for, etc.) sin añadir nodos extra al HTML.

En el siguiente fragmento de código se ha tenido que añadir una etiqueta `<div>`,que se mostrará en el DOM, para controlar la visibilidad de un conjunto de subetiquetas en el DOM.

```html
<div *ngIf="usuario">
  <h2>Bienvenido {{ usuario.nombre }}</h2>
  <p>Tienes {{ usuario.mensajes }} mensajes.</p>
</div>
```

Para evitar esta casuística se podría usar la etiqueta `<ng-container>`:

```html
<ng-container *ngIf="usuario">
  <h2>Bienvenido {{ usuario.nombre }}</h2>
  <p>Tienes {{ usuario.mensajes }} mensajes.</p>
</ng-container>
```
### 6.3.4 `ng-template`
`<ng-template>` define un bloque de código HTML que Angular no renderiza de inmediato, sino que guarda como una plantilla, puediéndose controlar su visibilidad según determinadas acciones.

En el siguiente ejemplo se muestra cómo se controla la visiblidad de un bloque de código HTML según si existe o no un usuario. Si el usuario existe se muestra el mensaje de bienvenida, de lo contrario, se muestra el contenido del `ng-template` llamado #noUsario.

```html
<ng-template #noUsuario>
  <p>No hay usuario logueado.</p>
</ng-template>

<ng-container *ngIf="usuario; else noUsuario">
  <p>Bienvenido {{ usuario.nombre }}!</p>
</ng-container>
```

### 6.3.5. Directivas de atributo.

Son aquellas que modifican la apariencia o el comportamiento de un elemento en el DOM. A diferencia de las directivas estructurales no cambian la estructura del DOM.

Ejemplos de directivas de atributo:

- **`ngClass`**: Añade o elimina clases CSS en un elemento de acuerdo con una expresión.

```html

<p [ngClass]="{'activo': esActivo, 'inactivo': !esActivo}">Texto con clases dinámicas.</p>

```

- **`ngStyle`**: Cambia estilos en línea de un elemento basados en una expresión.

```html
<p [ngStyle]="{'color': colorTexto}">Texto con estilo dinámico.</p>
```

- **`[hidden]`**: Muestra u oculta un elemento (es similar a `*ngIf`, pero mantiene el elemento en el DOM).

```html
<p [hidden]="ocultar">Este texto puede ocultarse.</p>
```


## Reto : Funcionalidad componente TaskList.

El objetivo del presente ejercicio consiste en implementar la funcionalidad básica del componente TaskListComponente, cuyo propósito es mostrar una tabla con las diferentes tareas que existen creadas en el sistema.

Para poder trabajar con las tareas, lo primero que es necesario realizar es modelar un objeto `Task`que la represente. Para ello, crea un archivo llamado `task.model.ts` en el directorio `src/app/models`dónde se implemente una clase llamada `Task` que contenga las siguientes propiedades:

- `id`
- `nombre`
- `descripción`
- `prioridad` que puede ser, Baja, Media, Alta
- `estado`que puede ser: Completada, En progreso y Pendiente.
- `fecha de creación`
- `fecha de expiración`

Declara una propiedad, en el componente TaskList, llamada `tareas` e incicializa un listado de tareas tomando como referencia el objeto anteriormente definido.

Modifica el código HTML del componente `TaskList` y añade una tabla de bootstrap dónde se deberá mostrar las siguientes propiedades de cada tarea: nombre, descripción, prioridad, estado, fecha de expiración, acciones.

**La tabla deberá cumplir los siguientes requisitos funcionales:**

- Se deberá mostrar una fila que actuará como encabezado con la información anteriormente mencionada de cada una de las tareas que han sido creadas en el controlador.
- La celda que muestra la **prioridad** de cada una de las tareas deberá tener un fondo, aplicando para ello una clase concreta, según su valor:
    - Si la prioridad es Baja → class=”table-success”
    - Si la prioridad es Media → class=”table-warning”
    - Si la prioridad es Alta → class=”table-danger”
- La celda que muestra el **estado** de cada una de las tareas deberá tener un fondo, aplicando para ello una clase concreta, según su valor:
    - Si el estado es Completada→ class=”table-success”
    - Si el estado es En progreso→ class=”table-warning”
    - Si el estado es Pendiente→ class=”table-danger”
- Añade en las siguientes columnas los iconos para poder cambiar el estado y prioridad de las tareas:
    - **Columna prioridad:**
        - bi bi-arrow-up-circle-fill → solo se mostrará si la prioridad de una tarea es “Baja” o “Media” y la tarea no ha sido completada.
        - bi bi-arrow-down-circle-fill → solo se mostrará si el estado de una tarea es “Alta” o “Media” y la tarea no ha sido completada.
    - **Columna estado:**
        - bi bi-play-fill → solo se mostrará si el estado de la tarea es “Pendiente”
        - bi bi-check-lg → solo se mostrará si el estado de la tarea es “En proceso”
        - bi bi-arrow-return-right → solo se mostrará si el estado de la tarea es “Completada”
- En la columna **Acciones** se deberá mostrar los siguientes iconos:
    - bi bi-pencil-square
    - bi bi-trash

A continuación se muestra un ejemplo del resultado final de la tabla mostrada por el componente:

![TaskList Component](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/tasklist-component.png)

**Ampliación**: si visualizamos nuestra aplicación en un dispositivo móvil podemos observar cómo la tabla que hemos implementado en nuestra aplicación no se adapta adecuadamente al tamaño de la pantalla. Busca en la documentación oficial de Bootstrap, algún otro componente que te permita mostrar el listado de tareas de manera responsivo. Piensa cómo lo mostrarías en una aplicación Android.

## Reto: Información si no existen tareas.

Utilizando la etiqueta `ng-template` crea un bloque de código HTML que muestre un mensaje informando que no existen tareas creadas si el array de tareas del controlador está vacío. De lo contrario, se deberá mostrar la tabla de tareas.

# 7. Event Binding.

Angular permite enlazar eventos del DOM a métodos o funciones del componentes. Para enlazar eventos se usa la sintaxis `(evento)=”accion()”` en la etiqueta del elemento en cuestión al que queremos enlazar dicho evento.

- evento → es el tipo de evento que será capturado. Algunos de los posibles eventos son:
    - `click`: Se dispara cuando se hace clic en un elemento.
    - `dblclick`: Se dispara cuando se hace doble clic en un elemento.
    - `mouseenter`: Se dispara cuando el cursor del ratón entra en el área de un elemento.
    - `mouseleave`: Se dispara cuando el cursor del ratón sale del área de un elemento.
    - `mousemove`: Se dispara cuando el cursor del ratón se mueve sobre un elemento.
    - `mousedown`: Se dispara cuando se presiona un botón del ratón sobre un elemento.
    - `mouseup`: Se dispara cuando se suelta un botón del ratón sobre un elemento.
    - `keydown`: Se dispara cuando se presiona una tecla.
    - `keyup`: Se dispara cuando se suelta una tecla.
    - `keypress`: Se dispara cuando se presiona una tecla que genera un carácter (menos común en versiones recientes).
    - `change`: Se dispara cuando el valor de un elemento de formulario cambia.
    - `input`: Se dispara cuando el valor de un elemento de entrada se modifica (incluye el evento `keyup`).
- accion() → método del controlador que se ejecutará cuando se capture el evento.

## 7.1. Ejemplo de cómo capturar un evento click:

```tsx
// app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  mensaje: string = '';

  mostrarMensaje() {
    this.mensaje = '¡Botón clicado!';
  }
}
```

```html
<!-- app.component.html -->
<button (click)="mostrarMensaje()">Haz clic aquí</button>
<p>{{ mensaje }}</p>
```

Cuando el usuario hace clic en el botón, el método mostrarMensaje() se ejecuta y cambia el valor de mensaje, que luego se muestra en la vista.



## 7.2. Obtener el elemento que ha desencadenado el evento.

En Angular, puedes capturar el elemento que ha desencadenado un evento pasándole el objeto $event al método del componente. Este objeto $event contiene información detallada sobre el evento, incluido el elemento DOM que fue clicado.

```html
<button (click)="capturarElemento($event)">Haz clic aquí</button>
```

```tsx
capturarElemento(event: Event) {
	const elementoClicado = event.target as HTMLElement;  // Convertir el target a un elemento HTML

	console.log('Elemento clicado:', elementoClicado);
	console.log('Texto del elemento:', elementoClicado.innerText);  // Ejemplo: texto del elemento
	console.log('ID del elemento:', [elementoClicado.id](http://elementoclicado.id/));  // Ejemplo: ID del elemento
}
```

## 7.3. Ejemplo de cómo capturar un evento de teclado keyup:

```tsx
// app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  mensaje: string = '';

  mostrarTexto(event:Event){
    const element = event.target as HTMLInputElement;
    console.log(element.value)
  }
}

```

```html
<!-- app.component.html -->
<div>
  <input type="text" placeholder="Introduce un texto aquí!" (keyup)="mostrarText($event)"/>
</div>
```
### Ejercicio: Contador de números

Tu objetivo es desarrollar un componente en Angular que funcione como un contador. Este componente debe hacer lo siguiente:

1. **Mostrar un Texto**: Debe mostrar un número en la pantalla, que inicialmente será 0.
2. **Incluir Dos Botones**:
    - Un botón que incremente el número en 1 cada vez que se haga clic en él.
    - Un botón que decrete el número en 1 cada vez que se haga clic en él.
3. **Comportamiento Esperado**:
    - Cuando el usuario haga clic en el botón de "Incrementar", el número mostrado debe aumentar en 1.
    - Cuando el usuario haga clic en el botón de "Decrementar", el número mostrado debe disminuir en 1.

## Reto. Funcionalidad iconos tasklist.

Implementa las siguientes funcionalidad a los iconos añadidos en la tabla del componente `tasklist` :

- **Columna prioridad:**
    - bi bi-arrow-up-circle-fill → subirá la prioridad de la tarea seleccionada. Si la tarea tiene una prioridad baja pasará a ser media y si es media pasará a ser alta.
    - bi bi-arrow-down-circle-fill → bajará la prioridad de la tarea seleccionada. Si la tarea tiene una prioridad alta pasará a ser media y si es media pasará a ser baja.
- **Columna estado:**
    - bi bi-play-fill → cambiará el estado de la tarea seleccionada a “En Progreso”.
    - bi bi-check-lg → solo se mostrará si el estado de la tarea es “En proceso”
    - bi bi-arrow-return-right → solo se mostrará si el estado de la tarea es “Completada”
- En la columna **Acciones** se deberá mostrar los siguientes iconos:
    - bi bi-pencil-square → implementa un método que muestre por consola “Editando Tarea”. Esta funcionalidad será implementada más adelante.
    - bi bi-trash → borra la tarea seleccionada.


# 10. Property Binding.

El property binding o enlace de propiedades es una técnica que nos permitirá enlazar las propiedades del controlador con las propiedades del DOM. Esto significa que podremos vincular datos del controlador a las propiedades de un elemento HTML, lo que permite que el DOM se actualice cuando se actualice automáticamente los datos del controlador.

El property binding se utiliza en la plantilla HTML empleando la sintaxis de corchetes `[]` . La expresión dentro del corchete se evalúa y el valor resultante se asigna a la propiedad del elemento del DOM correspondiente.

![Property Binding Scheme](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/property-binding.png)

Fuente: [https://zainulebadd.medium.com/property-binding-in-angular-explained-6eebf850e1be](https://zainulebadd.medium.com/property-binding-in-angular-explained-6eebf850e1be)

A continuación se muestra un ejemplo de cómo usar property binding en Angular.

```tsx
// archivo: app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  // Propiedad del componente
  titulo: string = 'Hola, mundo!';
  imagenUrl: string = 'https://example.com/imagen.jpg';
  habilitarBoton: boolean = true;
}
```

```html
<!-- archivo: app.component.html -->V
<h1 [textContent]="titulo"></h1> <!-- Binding a la propiedad textContent -->
<img [src]="imagenUrl" alt="Descripción de la imagen"> <!-- Binding a la propiedad src -->
<button [disabled]="!habilitarBoton">Enviar</button> <!-- Binding a la propiedad disabled -->
```

- **`[textContent]="titulo"`**: Vincula la propiedad `textContent` del elemento `<h1>` al valor de la propiedad `titulo` del componente. Cada vez que `titulo` cambia, el contenido del `<h1>` se actualiza automáticamente.
- **`[src]="imagenUrl"`**: Vincula la propiedad `src` de la etiqueta `<img>` a `imagenUrl`. Esto permite que la imagen mostrada cambie según el valor de `imagenUrl`.
- **`[disabled]="!habilitarBoton"`**: Vincula la propiedad `disabled` del botón al valor booleano de `habilitarBoton`. Si `habilitarBoton` es `false`, el botón estará deshabilitado.

A continuación se muestra algunas de las propiedades que se pueden usar:

- **`textContent`**: Establece el contenido de texto de un elemento.
- **`innerHTML`**: Establece el contenido HTML de un elemento.
- **`value`**: Utilizado con elementos de formulario como `<input>` o `<textarea>`, establece el valor del campo.
- **`src`**: Establece la fuente de una imagen (`<img>`).
- **`href`**: Establece el destino de un enlace (`<a>`).
- **`disabled`**: Habilita o deshabilita un elemento, como un botón o un campo de entrada.
- **`checked`**: Establece si un checkbox o un radio button está seleccionado.
- **`selected`**: Establece si una opción en un `<select>` está seleccionada.
- **`placeholder`**: Establece un texto de marcador de posición en campos de entrada.

También existen propiedades de estilo:

- `style.color`
- `style.backgroundColor`
- `style.fontSize`
- `style.border`

Otro de los aspectos interesantes es que se puede agregar o quitar clases CSS de un elemento usando la sintaxis de enlace de clases:

```html
<div [class.active]="isActive"></div>
```

`isActive` hace referencia a una propiedad del controlador, si este es `true` se añadirá la clase active quedando de esta forma:

```html
<div class="active">
```

### 10.1. Beneficios del Property Binding

- **Actualización Automática**: Cualquier cambio en la propiedad del componente se refleja automáticamente en la vista, lo que simplifica la gestión del estado.
- **Interactividad**: Permite crear interfaces de usuario interactivas que responden a los cambios en los datos.
- **Claridad**: Hace que el código sea más legible y mantenible al separar la lógica del componente de la presentación.

### Ejercicio imagen aleatoria:

Tu objetivo es desarrollar un componente en Angular que muestre una imagen aleatoria cada vez que se presione un botón. Sigue estos pasos:

1. **Crear un Botón**:
    - Debe haber un botón en la interfaz que tenga el texto "Imagen Aleatoria".
2. **Mostrar una Imagen**:
    - Debe haber un elemento HTML `<img>` en el componente que inicialmente no tendrá una URL establecida (puede estar vacío o mostrar un marcador de posición).
3. **Cambiar la Imagen al Hacer Clic**:
    - Cada vez que el usuario haga clic en el botón "Imagen Aleatoria", el componente debe generar un número aleatorio entre 1 y 10,000.
    - Usa este número aleatorio para construir una URL de imagen. La URL debe tener el siguiente formato:
        
        ```html
        https://picsum.photos/200/300?random=numero_aleatorio
        ```
        
    - Cambia la propiedad `src` del elemento `<img>` con la nueva URL para mostrar la imagen.
4. **Objetivo Final**:
    - Al hacer clic en el botón, la imagen mostrada debe cambiar a una nueva imagen aleatoria.

# 11. Comunicación entre componentes.

## 11.1. Comunicación entre componentes: padre a hijo.

Para pasar datos de un componente padre a un componente hijo se usa el decorador `@Input()` dentro de la clase hijo, concretamente, en una de sus propiedades. Por ejemplo, supongamos que tenemos un componentes NavBar que recibe como dato de entrada un listado de los diferentes elementos que tendrá.

En el componente hijo NavBar tendremos la siguiente propiedad:

```tsx
//navbar.component.ts
 @Input()
  listaOpciones:string[]=[];
```

Para poder pasarle desde el componente padre el listado de opciones tendremos que añadir a la etiqueta del componente hijo lo siguiente:

```html
<!--app.component.html-->
<app-navbar [listaOpciones]="opciones"></app-navbar>
```

Mediante property binding estamos mapeando la propiedad listaOpciones del hijo con la propiedad opciones del padre. Si nos fijamos en la clase padre, esta deberá contar con una propiedad llamada opciones.

```tsx
//app.component.ts
export class AppComponent {
  opciones=["Inicio","Perfil","Acerca de"]
}
```

Si en el template del componente hijo usamos @for para mostrar todos los elementos recibidos del padre de la siguiente forma:

```html
   <!--navbar.component.html-->
    @for (opcion of listaOpciones; track opcion){
        <p>{{opcion}}</p>
    }
```

## 11.2. Comunicación entre componentes: hijo a padre.

Para enviar datos desde un componente hijo a su padre usaremos el decorador `@Output()` junto con `EventEmiiter`.

Siguiendo con el ejemplo anterior, supongamos que queremos enviarle al componente padre la opción del menú en la que hacen clic nuestros usuarios. Para ello, primeramente capturaremos dicho click en las opciones añadiendo la captura del evento en el HTML.

```html
<!--navbar.component.html-->
    @for (opcion of listaOpciones; track opcion){
        <p (click)="opcionClick($event)">{{opcion}}</p>
    }
```

En la clase del componente hijo tendremos lo siguiente:

```tsx
//navbar.component.ts
export class NavbarComponent {

  @Input() listaOpciones:string[]=[];
  
  // Inicializamos el evento que le enviaremos al componente padre.
  @Output() opcionSeleccionada = new EventEmitter<string>();  // Evento de salida

	// Implementamos el método que se lanzará cuando se capture el clic en algunas de las opciones
  opcionClick(event:Event): void {
  
    //Obtenemos el elemento sobre el que se ha hecho clic.
    let elemento = event.target as HTMLElement;
    
    // Le enviamos un evento al padre con el texto del menú sobre el que se ha hecho click.
    this.opcionSeleccionada.emit(elemento.innerText);
  }
}
```

Una vez que se ha emitido el evento al componente padre es necesario capturarlo y definir qué función se ejecutará. Para capturar dicho evento usaremos lo visto en el apartado Event Binding. Concretamente, añadiremos lo siguiente en el template del componente padre:

```html
<!--app.component.html-->
<app-navbar [listaOpciones]="opciones" (opcionSeleccionada)="muestraOpcionSeleccionada($event)"></app-navbar>

```

- `(opcionSeleccionada)="muestraOpcionSeleccionada($event)"` → En este fragmento de código se captura el evento del hijo y se llama al método `muestraOpcionSeleccionada` que está definido en la clase padre, pasándole el mensaje del evento que ha ocurrido, que en este caso es un string.

En la clase padre se ha implementado la lógica del método anterior:

```tsx
// app.component.ts
export class AppComponent {
  opciones=["Inicio","Perfil","Acerca de"];
  opcionSeleccionada="";
  
  muestraOpcionSeleccionada(opcion:string):void{
    this.opcionSeleccionada=opcion;
  }
}
```

Por último, para poder visualizar la opción seleccionada, se ha modificado la plantilla del componente padre y se ha añadido la siguiente línea:

```html
<!--app.component.html-->
<p>{{opcionSeleccionada}}</p>
```


## RETO: Comunicación entre componentes.

Para darle un aspecto más profesional a nuestra aplicación se ha decidido cambiar la tabla usada para listar las diferentes tareas del usuario por tarjetas. Para ello, vamos se deberá modificar el componente `task-resume` para que reciba una tarea como dato de entrada pudiendo así mostrar toda su información en la tarjeta.

Para poder visualizar las tarjetas de cada tarea, será necesario modificar el componente `task-list` para que inyecte en su HTML el componente `<app-task-list></app-task-list>` para cada una de las tareas.

Por último, será necesario implementar la lógica de las acciones relacionadas con la tarea (borrar,subir prioridad, bajar prioridad, cambiar estado). Para ello, será necesario comunicarse con el componente padre e indicarle a este la modificación que se desea realizar sobre la tarea en cuestión, ya que es el encargado de gestionar el listado de tareas.

A continuación se muestra cómo se deberán organizar los diferentes componentes:

![Task List Structure](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/tasklist-structure.png)

**Requisitos funcionales:**

- Componente TaskListComponente:
    - Debe tener un listado de tareas en en controlador.
    - Debe mostrar en la plantilla un componente hijo TaskResume por cada una de las tareas del arreglo.
    - Debe implementar los mecanismos de comunicación necesarios para actualizar la lista de Tareas cuando se realice alguna acción en el componente hijo TaskResume.
- Componente TaskResume:
    - Debe implementar los mecanismos de comunicación necesarios para que reciba un objeto tarea del componente padre y muestre la información de dicho objeto en la plantilla.
    - Debe implementar los mecanismos de comunicación necesarios para informar al componente padre de los eventos que se desea realizar en una tarea concreta.

# 12. Routing.

Angular cuenta con un módulo encargado de gestionar las rutas de nuestra aplicación, decidiendo qué pantalla cargar en cada momento. Mediante Routing nuestra aplicación se comportará como una SPA (Single Page Application), donde no se realizan recargas completas del navegador.

Tomando como referencia nuestra app Planify, algunas de las posibles rutas de nuestra aplicación pueden ser:

- [http://localhost:4200/](http://localhost:4200/)login
- [http://localhost:4200/](http://localhost:4200/)singin
- [http://localhost:4200/](http://localhost:4200/)home
- [http://localhost:4200/](http://localhost:4200/)tasks
- [http://localhost:4200/](http://localhost:4200/)new
- [http://localhost:4200/](http://localhost:4200/)edit/{id}
- [http://localhost:4200/](http://localhost:4200/)dashboard


Cada vez que se acceda a algunas de las anteriores rutas Angular cargará un componente específico.

Lo ideal sería contar con un componente dedicado para cada una de las rutas de primer nivel, es decir, siguiendo con el ejemplo anterior deberíamos tener los siguientes componentes: `login, singin, home, tasks, new, dashboard`. Estos componentes los crearemos dentro del directorio `src/app/pages`. 

![pages-structure](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/pages-structure.png)

Fuente: [https://www.ganatan.com/tutorials/routing-with-angular](https://www.ganatan.com/tutorials/routing-with-angular)

Cada uno de estos componentes serán inyectados en el componente principal de nuestra aplicación `app-componet` , concretamente, se reemplazará la etiqueta `<router-outlet />` por el módulo en cuestión que sea cargado según la ruta indicada. Dentro de estos módulos “padres” se podrán cargar otros componentes hijos, así como usar rutas anidadas, lo cual lo veremos más adelante. A continuación se muestra un gráfico del funcionamiento:

![angular-routing](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/angular-routing.png)


Fuente: [https://www.ganatan.com/tutorials/routing-with-angular](https://www.ganatan.com/tutorials/routing-with-angular)

## 12.1. Configuración de rutas simples.

1. **Modificación del archivo `src/app/app.routes.ts` :**
    
    Lo primero que vamos a realizar será definir las diferentes rutas que tendrá nuestra aplicación y los componentes asociados a dichas rutas:
    
    ```tsx
    //app.routes.ts

    export const routes: Routes = [
        {path:'home', component:HomeComponent},
        {path:'login', component:LoginComponent},
        {path:'notfound', component:NotFoundComponent},
        {path:'',redirectTo:'/home',pathMatch:'full'},
        {path:'**',redirectTo:'/home',pathMatch:'full'}];
    ```
    
    En el archivo anterior hemos asociado las rutas /home y /login a los componentes HomeComponent y LoginComponent. Además, hemos aplicado una redireción para que cada vez que el usuario acceda a la ruta raiz del proyecto, es decir, a / , se le redireccione a /home. 
    
    Además, hemos configurado la página 404 de nuestra aplicación para que cada vez que el usuario acceda a una ruta no existente se cargue dicho componente. Para realizar esto, lo primero que hemos realizado a sido asociar el path /notfound al componente mediante `{path:'notfound', component:NotFoundComponent}` , y posteriormente, al final del arreglo de rutas (importante que se el último valor del arreglo), hemos indicado que todas aquellas rutas que coincidan con “**” sean redireccionadas a notfound.
    
2. **Configuración del controlador del componente app.component.ts**
    
    Para que el componente sea compatible con el Routing es necesario importar las siguientes clases dentro del decorador `@componente` . Esta configuración será necesaria realizarla en todos los componentes que vayan a inyectar algún otro componente hijo mediante routing. En nuestro caso solo realizaremos dicha configuración en el componente app.componente ya que será aquí donde se cargarán los diferentes componentes según la ruta seleccionada.
    

```tsx
//app.component.ts

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [CommonModule, **RouterOutlet, RouterLink**],
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
}
```

1. **Configuración de la plantilla app.component.html**

Para que un hipervínculo use una ruta configurada en el routing de nuestra aplicación es necesario utilizar el atributo routerLink=”/ruta”, tal y como se muestra a continuación:

```
<div id="menu">
  <a routerLink="/home">Home</a> -
  <a routerLink="/profile">Profile</a>
</div>

<router-outlet />
```

Es importante que dicha plantilla cuente con la etiqueta `<router-outlet />` ya que será aquí dónde se inyecten los componentes asociados a la ruta en la que haga clic el usuario, por ejemplo, el componente `/home` o `/profile`, en el caso anterior.

## RETO: Configuración rutas simples de Planify
El objetivo de este reto es realizar la configuración de las diferentes rutas simples de la aplicación Planify. Concretamente, se deberán configurar las siguientes rutas en el archivo app.routes.ts:

- /home -> HomeComponent
- /tasks -> TasksComponent
- /dashboard -> DashboardComponent
- /login -> LoginComponent
- /singin -> SinginComponent
- /new -> TaskFormComponent


Realiza las configuraciones necesarias para que cuando se haga clic en algunas opciones del menu se muestre el componente asociado a cada ruta en el componente principal `app.component`.

Además, también será necesario realizar la configuración de los siguientes botones mostrados en las siguientes componentes:

- Componente Tasklist:
  - Botón `Crear tarea`: redirección a `/new`
- Componente Stats:
  - Botón `Nueva tarea`: redirección a `/new`
- Componente Taskform:
  - Botón `Cancelar`: redirección a `/tasks`
- Componente Home:
  - Botón `Comenzar`: redireccion a `/tasks`
  - Botón `Iniciar sesión`: redirección a `/login`

## 12.2. Configuración de rutas con parámetros.

Angular también permite que se pase algún parámetro en la ruta para que pueda ser recuperado desde el controlador y modificar la lógica del componente asociado a dicha ruta según el valor del parámetro recibido.

Por ejemplo, nuestra aplicación sobre gestión de tareas puede tener una ruta que sea la siguiente [http://localhost:4200/edit/323](http://localhost:4200/edit/323) que nos permita modificar una tarea en concreto, en este caso, la tareas con identificador 323. 

Para lograr esto, será necesario modificar el componente asociado a la ruta /task para capturar el valor del parámetro pasado y el archivo app.routes.ts para indicarle que dicha ruta recibirá un parámetro.

1. **Modificación del archivo app.routes.ts**

```tsx
//app.routes.ts
export const routes: Routes = [
{path: "task/:id", component: TaskComponent}
];
```

En el código anterior hemos definido el path y mediante `:id` hemos indicado que el primer parámetro tendrá el identificador `id` 

Si necesitásemos pasarle a una ruta más de un parámetro es tan sencillo como seguir la estructura anterior. Por ejemplo: `"tasklist/:id1/:id2/id3"` .

1. **Acceso al parámetro desde el controlador:**

Para que nuestro controlador pueda acceder al parámetro indicado en la ruta, debemos modificar nuestro constructor para que reciba un objeto `ActivatedRoute` quedando de la siguiente forma:

```tsx
export class TaskformComponent implements OnInit{

  constructor(private route: ActivatedRoute) {}

  ngOnInit() {
    this.route.paramMap.subscribe(params => {
    var id = params.get('id');
    console.log(id);
    });
  }
}
```

Mediante el código anterior hemos obtenido una ruta con la que operaremos usando la implementación del ngOnInit (función que se ejecuta justo después de recibir todos los parámetros y antes de renderizar la plantilla). 

Dentro de ngOnInit() nos estamos suscribiendo a los parámetros de nuestra ruta, lo que nos permitirá reaccionar a cambios dinámicos si la ruta cambia sin necesidad de recargar la página.

## RETO: Configuración rutas con parametros de Planify
El objetivo de este reto es realizar la configuración de las diferentes rutas con parámetros de la aplicación Planify. Concretamente, se deberán configurar las siguientes rutas en el archivo app.routes.ts:

- /edit/:id -> TaskFormComponent

Realiza las configuraciones necesarias para que cuando se haga clic en el botón `Editar` de una tarea se acceda al component TaskformComponent y se le pase como parámetro el identificador de la tarea que se desea editar. Muestra en una etiqueta HTML del componente `task-form` el identificador pasado como parámetro en la URL.

## 12.3. Rutas anidadas.

Las rutas anidadas nos permitirán organizar los componentes de nuestra aplicación de manera jerárquica, lo que nos facilitará la construcción de aplicaciones complejas. Se suelen utilizar cuando un componente tiene sus propias subrutas para cargar componentes hijos dentro del componente padre de manera dinámica.

Imaginemos que nuestra aplicación tiene un componente padre llamado DashboardComponent con las siguientes secciones: Estadísticas y Configuración. Para poder cargar dentro de dicho componente la sección específica en la que haga clic el usuario, se deben usar rutas anidadas.

Para llevar a cabo esto es necesario realizar la siguiente configuración:

1. **Configuración del archivo app.routes.ts:**

```tsx
**#app.routes.ts**
export const routes: Routes = [
  {
    path: 'dashboard',
    component: DashboardComponent,
    children: [
      {
        path: 'stats',
        component: StatsComponent
      },
      {
        path: 'configuration',
        component: ConfigurationComponent
      }
    ]
  }
]
```

A la ruta del componente padre le hemos añadido dos rutas anidadas empleando la propiedad `children` el cual recibe un arreglo de rutas anidadas.

1. **Configuración del controlador del componente DashboardComponent:**

Será necesario importar en el decorador de nuestro componente los módulos de routing, tal y como hemos explicado en el ejemplo anterior:

```tsx
  imports: [CommonModule, RouterOutlet, RouterLink],
```

1. **Configuración de la plantilla del componente DashboardComponent:**

```tsx
<!-- dashboard.component.html -->
<h1>Dashboard</h1>
<nav>
  <a routerLink="stats">Estadísticas</a> |
  <a routerLink="settings">Configuración</a>
</nav>

<!-- Aquí se renderizarán los componentes hijos -->
<router-outlet></router-outlet>
```

## RETO: Configuración rutas anidadas en Planify.

El objetivo de este reto es configurar dos rutas anidadas a la ruta '/dashboard' para que en el componente asociado a esta ruta, `DashboardComponent`, se muestre uno de los siguientes componentes hijos:
- Ruta `/dashboard/profile`: Se debe mostrar el componente hijo `ProfileComponent`
- Ruta `/dashboard/stats`: Se debe mostrar el componente hijo `StatsComponent`

El resultado debe ser el siguiente:
![reto-rutas-anidadas1](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/reto-rutas-anidadas1.png)

![reto-rutas-anidadas2](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/reto-rutas-anidadas2.png)


## 12.4. Redirección desde el controlador.

Para poder realizar una redirección a una ruta específica desde el controlador de un componente es necesario usar el servicio Router, el cual, proporciona un conjunto de métodos para navegar entre rutas.

Supongamos que tenemos un componente llamado LoginComponente que es el encargado de mostrar un formulario de inicio de sesión. En el caso de que el login del usuario sea correcto será necesario redirigir al usuario a la página principal. Para ello, realizaremos los siguientes pasos:

1. **Inyectar el servicio Router en la clase/controlador del componente LoginComponent:**

```
export class LoginComponent {

  constructor(private routerService:Router){}
}

```

1. **Usar servicio Router:**

```tsx
export class LoginComponent {

  constructor(private routerService:Router){}

  login(){
    //TODO: Comprobamos que el login es correcto

    //Redirección sin parámetros
    this.routerService.navigate(['/home']);
  }
```

En el ejemplo anterior se realiza una redirección sin parámetros, pero también podría ser necesario redireccionar a una ruta usando algún parámetro. Para ello, debemos usar el servicio Router de la siguiente forma:

```tsx
this.router.navigate(['/taskform', taskId]);
```

## RETO: Redirección desde el controlador.

El objetivo de este reto consiste en realizar una redirección a una ruta desde el controlador. En Planify existen varios botones que al ser pulsados primeramente realizarán una acción y posteriormente si todo es correcto realizará una redirección a una ruta de la aplicación. Algunos de estos botones son:

- Componente Login:
  - Botón `Entrar`: tras ser pulsado y comprobar que el usuario y la contraseña es correcto redirigirá a la ruta `/tasks`.
- Componente Singin:
  - Botón `Registrarse`: tras verificar que los datos introducidos en el formulario son correctos redirigirá a la ruta `/tasks`.

Implementa en el controlador de cada uno de los siguientes componentes un método y asocialo a cada botón para que realice la redirección cuando el usuario haga clic en alguno de ellos.


# 13. Servicios.

Un servicio es una clase en la que se implementarán todas la lógica de negocio de nuestra aplicación así como el acceso y envío de datos de una API. De esta forma los servicios nos permitirán compartir datos, lógica de negocio o funcionalidades entre diferentes componentes que se encuentren relacionados.

Pongamos un ejemplo tomando como referencia nuestra aplicación Planify, la cual cuenta con diferentes componentes relacionados con el listado, visualización y edición de una tarea. Toda la lógica de nuestra aplicación  relacionada con la gestión de las tareas (obtener las tareas del usuario de la base de datos, guardar una nueva tarea, editar una tarea, etc) la implementaremos en un servicio que será consumido por cada componente, según lo necesite. 

Los servicios cuentan con las siguientes características:

- Son reutilizables: pueden ser llamados desde distintos componentes de la aplicación.
- Son singleton: solo se crea una instancia del servicio para toda la aplicación, por lo que todos los componentes comparten la misma información.
- Centralización: toda la lógica estará en un solo lugar, si necesidad de ser repetida por los componentes.
- Pruebas: es más fácil probar un servicio a tener que probar la lógica de varios componentes.

## 13.1. Creación de un servicio.

Para generar un nuevo servicio usaremos Angular CLI, ejecutando el siguiente comando en la terminal de nuestro IDE:

```bash
ng generate service services/task
```

## **13.2. Implementar la lógica del servicio.**

Dentro de nuestro servicio podemos añadir diferentes funciones para gestionar toda la lógica relacionada con la gestión de tareas de nuestra aplicación:

```tsx
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class TaskService {
  private tasks: Task[] = [];
  
  getTasks(): Task[] {
    //TODO: lógica para obtener el listado completo de tareas.
  }
  
  addTask(task: Task): void {
    //TODO: lógica para añadir una nueva tarea al listado.
  }
}
```

## 13.3. Usar un servicio desde un componente.

Una vez implementado el servicio este ya puede ser usado desde cualquier componente. Para ello, lo primero que debemos hacer es inyectar dicho servicio en el la clase del componente donde queremos usarlo. A continuación se muestra un ejemplo de cómo se inyectaría este servicio en el componente TaskList:

```tsx
export class TaskListComponent implements OnInit {
  tasks: string[] = [];

  constructor(private taskService: TaskService) {} // Inyecta el servicio

  ngOnInit(): void {
    this.tasks = this.taskService.getTasks(); // Obtén las tareas del servicio
  }
}
```

Como se ha podido observar, para inyectar un servicio lo que hemos realizado ha sido pasárselo como parámetro en el constructor de nuestro componente.

## RETO: Implementación del servicio TaskService.
El objetivo de este reto consiste en extraer toda la lógica de negocio implementada en los controladores de los componentes Tasklist, Taskresume a un servicio llamado Task y ubicado en `/src/app/services` .

# 14. Formularios basados en plantillas.

Los formularios basados en plantillas o Template-driven Forms son una manera declarativa de crear formularios HTML vinculados a los datos (data binding). Son declarativos porque la mayoría de la lógica del formulario se configura directamente en la plantilla HTML.

Este enfoque se suele emplear en formularios sencillos donde no es necesario implementar mucha lógica en el controlador.

Para poder hacer uso de este tipo de formularios es necesario importar el módulo `FormsModule` en el controlador del componente donde será implementado.

El objetivo de este tipo de formularios es crear un enlace bidireccional entre las propiedades del controlador y los campos del formulario, de tal forma que cuando se modifique un dato en el formulario se actualice el valor en el controlador y viceversa. Para pode realizar dicho enlace se usará la directiva `[(ngModel)]` . Un ejemplo básico sería el siguiente:

Vamos a crear en el controlador un objeto usuario con tres propiedades:

```tsx
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';

@Component({
  selector: 'app-form',
  standalone: true,
  imports: [FormsModule],
  templateUrl: './form.component.html',
  styleUrl: './form.component.css'
})
export class FormComponent {

  usuario = {
    nombre : '',
    apellidos: '',
    edad: ''
  }
}
```

En la plantilla vamos un formulario con tres campos, dos de texto y uno numérico y los vamos a enlazar de manera bidireccional con las propiedades del controlador usando la directiva `[(ngModel)]` . Además, añadiremos la interpolación de las propiedades del controlador para ver cómo cambian.

```html
<form>
    <input type="text" [(ngModel)]="usuario.nombre" name="nombre" placeholder="Indique el nombre del usuario"/>
    <input type="text" [(ngModel)]="usuario.apellidos" name="apellidos" placeholder="Indique los apellidos del usuario"/>
    <input type="number" [(ngModel)]="usuario.edad" name="edad" placeholder="Indique la edad del usuario"/>
    <input type="submit" >
</form>

<p>{{usuario.nombre}}</p>
<p>{{usuario.apellidos}}</p>
<p>{{usuario.edad}}</p>
```

Si implementamos dicho código podemos observar cómo cuando cambiamos el valor de los inputs se actualiza el valor del controlador y se muestra por pantalla el valor actualizado.

## RETO: Funcionalidades formulario inicio de sesión.

El objetivo del presente reto es implementar un formulario basado en plantillas en el componente `LoginComponente` para que los usuarios puedan iniciar sesión en la aplicación Planify. Tomando como referencia la plantilla proporcionada, realiza las modificaciones necesarias para capturar los valores introducidos en los campos del formulario de inicio de sesión. Verifica que el usuario y la contraseña son válidas y redirigue a la ruta `/tasks`.

# 15. Formularios reactivos.

Los formularios reactivos o Reactive Forms nos permitirán crear formularios dinámicos y complejos utilizando el enfoque de la programación reactiva, la cual se basa en gestionar estos formularios desde el controlador donde se declarará el modelo del formulario como un grupo de controles. 

Este tipo de formularios es ideal cuando se quiere un mayor control sobre la lógica del formulario, las validaciones y los datos.


A continuación veremos cómo implementar un formulario reactivo en nuestro proyecto Planify. Concretamente, implementaremos el formulario de registro. Para ello, debemos incluir el siguiente fragmento de código HTML en la plantilla del componente SinginComponent.

```html
<!--signin.component.html-->

<div class="container py-5">
    <div class="row justify-content-center">
        <div class="col-12 col-sm-10 col-md-8 col-lg-8">
            <div class="card shadow-sm">
                <div class="card-body p-4">
                    <h3 class="card-title text-center mb-3">Create a Planify Account</h3>
                    <form>
                        <div class="mb-2 mt-2">
                            <input class="form-control"  placeholder="Username" />
                        </div>
                        <div class="row mt-2 g-2">
                            <div class="col-12 col-md-6 mb-2">
                                <input class="form-control" placeholder="First Name" />
                            </div>
                            <div class="col-12 col-md-6 mb-2">
                                <input class="form-control"placeholder="Last Name" />
                            </div>
                        </div>
                        <div class="mb-2 mt-2">
                            <input class="form-control" placeholder="Email" />
                        </div>
                        <div class="row mt-2 g-2">
                            <div class="col-12 col-md-6 mb-3">
                                <input class="form-control" type="password"
                                    placeholder="Password" />
                            </div>
                            <div class="col-12 col-md-6 mb-3">
                                <input class="form-control" type="password"
                                    placeholder="Confirm Password" />
                            </div>
                        </div>
                        <button class="btn btn-success w-100" type="submit">Sign In</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</div>
```

Nuestro componente deberá tener hasta el momento el siguiente aspecto:
![singin-planify](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/singin-planify.png)



## 15.1 Configuración de la clase del componente.
Una vez creado el formulario con HTML, lo siguiente que debemos hacer es crear un objeto en la clase del componente que será el encargado de representar al formulario y con el cual interactuaremos posteriormente. 

Lo primero de todo es importar las siguientes clases en los `imports` de `@Component`: `CommonModule,FormsModule, ReactiveFormsModule`

```ts
//signin.component.ts

@Component({
  selector: 'app-singin',
  imports: [CommonModule,FormsModule, ReactiveFormsModule],
  templateUrl: './singin.component.html',
  styleUrl: './singin.component.css'
})
```
Lo siguiente que realizaremos será definir una propiedad llamada `registerForm` que inicializaremos en el constuctor de nuestro componente y que será el encargado de representar a nuestro formulario de HMTL.

```ts
//signin.component.ts

export class SinginComponent {
registerForm:FormGroup;

constructor (formBuilder:FormBuilder){
  this.registerForm = formBuilder.group({
    'username': ['', [Validators.required,Validators.minLength(10)]],
    'firstName': ['', [Validators.required]],
    'lastName': ['', [Validators.required]],
    'email': ['', [Validators.required,Validators.email]],
    'password': ['', [Validators.required]],
    'confirmPassword': ['', [Validators.required]]
  });
 }
}

```
Vamos a detenernos en analizar el código anterior y a explicar cada uno de los pasos seguidos:

1. Se ha modificado el constructor del componente y se le ha pasado un  parámetro llamado `formBuilder` que es un objeto de tipo `FormBuilder`.

2. Se ha inicializado la propiedad `registerForm`. Para ello, hemos usado el método `group`. En este método hemos creado un objeto donde hemos incluido cada uno de los campos que tendrá nuestro formulario. Para ello, se debe seguir la siguiente estructura:

```json
{
  'id_campo_formulario1': ['valor_inicial',[Validaciones]],
  'id_campo_formulario2': ['valor_inicial',[Validaciones]],
  ...
}
```

Algunas de las validaciones que nos proporciona la clase `Validatos` son:

- **`required`**: Campos obligatorios.
- **`min` y `max`**: Validar rango numérico.
- **`minLength` y `maxLength`**: Limitar el número de caracteres.
- **`email`**: Validar formato de email.
- **`pattern`**: Validar expresiones regulares personalizadas.
- **`compose` y `composeAsync`**: Combinar validaciones.



## 15.2. Configuración de la plantilla del componente.

Una vez que hemos declarado e inicializado el objeto que va a representar a nuestro formulario en la clase del constructor es el momento de vincular dicho objeto con la planitlla usando `Property Binding` en las siguientes etiquetas HTML:

1. En la etiqueta `form` se incluirá lo siguiente: `[formGroup]="registerForm"`. De esta forma estamos vinculando el formulario a la propiedad `registerForm` inicializada anteriormente.

2. En cada uno de los campos del formulario donde el usuario introducirá información se incluirá lo siguiente `formControlName="id_campo"`, siendo necesario reemplazar `id_campo` por el identificador de cada uno de los campos que hemos definidos en la propiedad `registerForm`. De esta forma estamos vinculando los campos del formulario HTML con los del objeto de la clase del componente `registerForm`.

Una de las características que tienen los formularios reactivos es que de forma automática validarán los datos introducidos por los usuarios. Una configuración común es deshabilitar el botón de registro si los datos introducidos en los campos no cumple con alguna validación. Para ello mediante `Property Binding` mostaremos el atributo `disabled` si los datos del formulario no son válidos:

```html
<button class="btn btn-success w-100" type="submit" [disabled]="registerForm.invalid">Sign In</button>
```

El objeto ``registerForm`` tiene una propiedad llamada ``invalid`` que devolverá un booleano cuyo valor variará según si los datos introducidos en el formulario son o no válidos 

El código HTML resultante es el siguiente:


```html
<!--signin.component.html-->

<div class="container py-5">
    <div class="row justify-content-center">
        <div class="col-12 col-sm-10 col-md-8 col-lg-8">
            <div class="card shadow-sm">
                <div class="card-body p-4">
                    <h3 class="card-title text-center mb-3">Create a Planify Account</h3>
                    <form [formGroup]="registerForm">
                        <div class="mb-2 mt-2">
                            <input class="form-control" formControlName="username" placeholder="Username" />
                        </div>
                        <div class="row mt-2 g-2">
                            <div class="col-12 col-md-6 mb-2">
                                <input class="form-control" formControlName="firstName" placeholder="First Name" />
                            </div>
                            <div class="col-12 col-md-6 mb-2">
                                <input class="form-control" formControlName="lastName" placeholder="Last Name" />
                            </div>
                        </div>
                        <div class="mb-2 mt-2">
                            <input class="form-control" formControlName="email" placeholder="Email" />
                        </div>
                        <div class="row mt-2 g-2">
                            <div class="col-12 col-md-6 mb-3">
                                <input class="form-control" formControlName="password" type="password"
                                    placeholder="Password" />
                            </div>
                            <div class="col-12 col-md-6 mb-3">
                                <input class="form-control" formControlName="confirmPassword" type="password"
                                    placeholder="Confirm Password" />
                            </div>
                        </div>
                        <button class="btn btn-success w-100" type="submit" [disabled]="registerForm.invalid">Sign In</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</div>
```

## 15.3. Validaciones personalizadas:

Como hemos estudiado en los apartados anteriores, podemos validar los campos de un formulario usando las validaciones proporcionadas por la clase `Validators` , pero además, también podemos realizar la implementación de validaciones personalizadas, cómo, por ejemplo, una validación para verificar que el DNI de un usuario cumple con el formato y letra correcta.

### 15.3.1 Validaciones a un campo.

Para poder implementar una nueva validación es necesario implementar una función que devuelva un objeto con errores o  con un `null` si la validación es exitosa. Dicha función la implementaremos en un archivo diferente llamada `signin.validator.ts` que ubicaremos en el contenedor `validations` dentro de `src/app`. La estructura que debe tener la función de validación es la siguiente

```tsx
//signin.validator.ts
import { AbstractControl, ValidationErrors, ValidatorFn } from '@angular/forms';

//Ejemplo estructura función
export function customValidator(control: AbstractControl): ValidationErrors | null {

  let valorCampo = control.value
  const isValid = true /* condición para validar el valor */;
  return isValid ? null : { customErrorKey: true }; // Error si no es válido

}
```
La función de validación anterior recibirá un parámetro `control` de tipo `AbstractControl` que representa el campo del formulario dónde estamos usando dicha validación. Dentro de dicha función se obtendrá el valor del campo mediante un `control.value` y se realizarán las comprobaciones necesarias. Si la validación es correcta, es decir, no hay errores, se devolverá null, de lo contrario, se devolverá un objeto con los errores producidos. Dicho objeto tendrá la siguiente estructura: `{nombreError1:true, nombreError2:true}` 

A continuación se muestra un ejemplo de una función para realizar la validación del campo `password` del formulario de registro. Con esta función se está comprobando si la contraseña contiene una letra mayúscula y un número:

```tsx
//signin.validation.ts

export function strongPasswordValidator(control: AbstractControl): ValidationErrors | null {
  
    const value = control.value;

    if (!value) {
      // Si el campo está vacío, dejamos que el validador muestre el error
      return null;
    }

    const hasUpperCase = /[A-Z]+/.test(value);
    const hasNumeric = /[0-9]+/.test(value);

    // Si falta la mayúscula o el número, devolvemos el error
    const passwordValid = hasUpperCase && hasNumeric;

    return passwordValid ? null : { weakPassword: true };
}
```

Para poder usar dichas validaciones personalizadas en el controlador, tendremos que modificar la definición de nuestro FormGroup:

```tsx
//signin.component.ts
  this.registerForm = formBuilder.group({
    'username': ['', [Validators.required,Validators.minLength(10)]],
    'firstName': ['', [Validators.required]],
    'lastName': ['', [Validators.required]],
    'email': ['', [Validators.required,Validators.email]],
    'password': ['', [Validators.required,strongPasswordValidator]],
    'confirmPassword': ['', [Validators.required]]
  });
```

### 15.3.2 Validaciones a un campo con parámetros.
En ocasiones es necesario pasarle datos a la función de validación personalizada para modificar su comportamiento. Por ejemplo, un longitud mínima o una lista de palabras prohibidas.

Para ello, la función de validación tendrá una estructura un poco diferente al anterior caso:

```tsx
//login.validator.ts
export function restrictedWordsValidator(words: string[]): ValidatorFn {
  return (control: AbstractControl): ValidationErrors | null => {
    const isRestricted = words.includes(control.value?.toLowerCase());
    return isRestricted ? { restrictedWord: true } : null;
  };
}
```

Para usar esta validación será necesario llamarla de la siguiente forma en la clase del componente:

```tsx
//signin.component.ts
  this.registerForm = formBuilder.group({
    'username': ['', [Validators.required,Validators.minLength(10),restrictedWordsValidator(['admin','superadmin'])]],
    'firstName': ['', [Validators.required]],
    'lastName': ['', [Validators.required]],
    'email': ['', [Validators.required,Validators.email]],
    'password': ['', [Validators.required]],
    'confirmPassword': ['', [Validators.required]]
  },{ validators: matchPasswordValidator}
  );
```

### 15.3.3 Validaciones a nivel de grupo.
En el punto anterior hemos visto cómo aplicarle una validación personalizada a un campo concreto, pero, también puede darse el caso de querer aplicar una validación a dos campos al mismo tiempo, por ejemplo a dos campos llamados `password` y `confirmPassword`. Lo interesante sería aplicar una validación personalizada para validar que ambos campos contienen la misma contraseña. A continuación se muestra un ejemplo:

```tsx
//signin.validator.ts
export function matchPasswordValidator(control: AbstractControl): ValidationErrors | null {
    
  // 1. Obtenemos el valor del campo campo "confirmPassword" (que es el 'control' actual)
    const confirmValue = control.value;

    // 2. Subimos al padre (el FormGroup) para buscar el otro campo
    // Es importante verificar si existe el parent para evitar errores al inicio
    const formGroup = control.parent; 
    
    if (!formGroup) {
      return null; // Aún no está listo el formulario
    }

    const passwordControl = formGroup.get('password'); // Buscamos al hermano
    const passwordValue = passwordControl?.value;

    // 3. Comparamos
    if (!passwordValue || !confirmValue) {
        return null; // Dejamos que el 'required' haga su trabajo si están vacíos
    }

    return passwordValue === confirmValue ? null : { mismatch: true };
}
```

Añadimos la función de validación sobre el campo `confirmPassword`:

```tsx

  this.registerForm = formBuilder.group({
    'username': ['', [Validators.required,Validators.minLength(10),restrictedWordsValidator(['admin','superadmin'])]],
    'firstName': ['', [Validators.required]],
    'lastName': ['', [Validators.required]],
    'email': ['', [Validators.required,Validators.email]],
    'password': ['', [Validators.required]],
    'confirmPassword': ['', [Validators.required,matchPasswordValidator]]
  }
  );
```

## 15.4. Visualización de validaciones con Bootstrap en la plantilla.

Una vez que hemos realizado las validaciones en el controlador, vamos a ver cómo configurar la plantilla de nuestro proyecto para que tenga un estilo visual parecido al de la siguiente imagen:

![Bootstrap Form Validators](https://raw.githubusercontent.com/josearodriguezdaw/angular-tutorial/refs/heads/main/readme-images/bootstrap-form.png)

Para lograr esto, debemos controlar lo siguiente:

1. Se le deberá añadir a los campos del formulario la clase `is-valid` o `is-invalid` para que muestren el tick verde [**✅**](https://emojipedia.org/es/bot%C3%B3n-de-marca-de-verificaci%C3%B3n) o en rojos con el símbolo de exclamación **❗**. Para lograr esto, usaremos la directiva vista en el apartado anterior `[ngClass]` . Por ejemplo:
    ```html
    <input type="text" class="form-control" id="username" 
    [ngClass]="{'is-valid': this.registerForm.get('username')?.valid,'is-invalid':this.registerForm.get('username')?.invalid}" />
    ```
El problema que tiene lo realizado en el fragmento de código anterior es que en cuanto el usuario entre al formulario de creación se mostrarán todos los errores. Una mejora que se puede aplicar es que únicamente se muestren los errores si el usuario ha interactuado con el campo. De esta forma evitaremos que por defecto en el formulario aparezcan todos los errores. Para ello, será necesario añadir la siguiente conción: `registerForm.get('username')?.touched`. El código quedaría así:
   
    ```html
    <input type="text" class="form-control" id="username" 
    [ngClass]="{'is-valid': this.registerForm.get('username')?.valid && this.registerForm.get('username')?.touched,'is-invalid':this.registerForm.get('username')?.invalid && this.registerForm.get('username')?.touched }" />
   
    ```


- Para mostrar los textos con la información sobre los errores debajo de cada campo usaremos un divisor que tendrá la clase `valid-feedback` o `invalid-feedback` para mostrar el texto en color verde o rojo, respectivamente. Dentro de este divisor usaremos la etiqueta <small> para mostrar los errores específicos:

```html
 <div class="invalid-feedback">
   <small> Please choose a username.</small>
 </div>
```

- Será necesario implementar en nuestra plantilla toda la lógica para poder controlar qué mensaje de error se mostrará en cada momento. Para ello, usaremos la directiva *ngIf para mostrar un mensaje de error concreto:

```html
<div class="invalid-feedback">
 <small *ngIf="registerForm.get('username')?.errors?.['required']"> Please choose a username.</small>
</div>
```

El HTML de nuestro componente Signin quedará así:

```html
<div class="container py-5">
    <div class="row justify-content-center">
        <div class="col-12 col-sm-10 col-md-8 col-lg-8">
            <div class="card shadow-sm">
                <div class="card-body p-4">
                    <h3 class="card-title text-center mb-3">Create a Planify Account</h3>
                    <form [formGroup]="registerForm">
                        <div class="mb-2 mt-2">
                            <input class="form-control" formControlName="username" placeholder="Username"
                                [ngClass]="{'is-valid': this.registerForm.get('username')?.valid && this.registerForm.get('username')?.touched,'is-invalid':this.registerForm.get('username')?.invalid && this.registerForm.get('username')?.touched }" />
                            <div class="invalid-feedback">
                                <small *ngIf="registerForm.get('username')?.errors?.['required']"> Please enter a username.</small>
                            </div>
                        </div>
                        <div class="row mt-2 g-2">
                            <div class="col-12 col-md-6 mb-2">
                                <input class="form-control" formControlName="firstName" placeholder="First Name"
                                    [ngClass]="{'is-valid': this.registerForm.get('firstName')?.valid && this.registerForm.get('firstName')?.touched,'is-invalid':this.registerForm.get('firstName')?.invalid && this.registerForm.get('firstName')?.touched }" />
                                <div class="invalid-feedback">
                                    <small *ngIf="registerForm.get('firstName')?.errors?.['required']"> Please enter a first name</small>
                                </div>
                            </div>
                            <div class="col-12 col-md-6 mb-2">
                                <input class="form-control" formControlName="lastName" placeholder="Last Name"
                                    [ngClass]="{'is-valid': this.registerForm.get('lastName')?.valid && this.registerForm.get('lastName')?.touched,'is-invalid':this.registerForm.get('lastName')?.invalid && this.registerForm.get('lastName')?.touched }" />
                                <div class="invalid-feedback">
                                    <small *ngIf="registerForm.get('lastName')?.errors?.['required']"> Please enter a last name</small>
                                </div>
                            </div>
                        </div>
                        <div class="mb-2 mt-2">
                            <input class="form-control" formControlName="email" placeholder="Email"
                                [ngClass]="{'is-valid': this.registerForm.get('email')?.valid && this.registerForm.get('email')?.touched,'is-invalid':this.registerForm.get('email')?.invalid && this.registerForm.get('email')?.touched }" />
                            <div class="invalid-feedback">
                                <small *ngIf="registerForm.get('email')?.errors?.['required']"> Please enter a valid email.</small>
                            </div>
                        </div>
                        <div class="row mt-2 g-2">
                            <div class="col-12 col-md-6 mb-3">
                                <input class="form-control" formControlName="password" type="password"
                                    placeholder="Password"
                                    [ngClass]="{'is-valid': this.registerForm.get('password')?.valid && this.registerForm.get('password')?.touched,'is-invalid':this.registerForm.get('password')?.invalid && this.registerForm.get('password')?.touched }" />
                                <div class="invalid-feedback">
                                    <small *ngIf="registerForm.get('password')?.errors?.['required']"> Please enter a password.</small>
                                </div>
                            </div>
                            <div class="col-12 col-md-6 mb-3">
                                <input class="form-control" formControlName="confirmPassword" type="password"
                                    placeholder="Confirm Password"
                                    [ngClass]="{'is-valid': this.registerForm.get('confirmPassword')?.valid && this.registerForm.get('confirmPassword')?.touched,'is-invalid':this.registerForm.get('confirmPassword')?.invalid && this.registerForm.get('confirmPassword')?.touched }" />
                                <div class="invalid-feedback">
                                    <small *ngIf="registerForm.get('confirmPassword')?.errors?.['required']">Please confirm your password</small>
                                </div>
                            </div>
                        </div>
                        <button class="btn btn-success w-100" type="submit" [disabled]="registerForm.invalid">Sign
                            In</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</div>
```

## 14.5. Implementación del método `onSubmit`.

Una vez que el campo ha sido validado y el botón `Guardar` se ha habilitado es el momento de obtener la información desde el controlador y procesar la información del formulario para su posterior guardado en base de datos. 

Para poder realizar el envío de los datos al controlador es fundamental que el formulario de la plantilla se haya capturado el evento submit de la siguiente forma: `(ngSubmit)="onSubmit()"`. Además, debe existir dentro del formulario un botón de tipo `submit` que será el que desencadene el evento: `<button type="submit" [disabled]="registroForm.invalid">Registrarse</button>`.

Cuando el usuario pulse el botón `Registrarse` se realizará una llamada al método `onSubmit()` definido en el controlador. Desde este método podremos acceder a los valores del formulario de la siguiente forma:

```ts
  onSubmit(){
    // Comprobamos que el formulario sea válido
    if(this.registerForm.valid){
        let name = this.taskForm.get('name')?.value;
        let surname = this.taskForm.get('surname')?.value;
        let email = this.taskForm.get('email')?.value;
        let password = this.taskForm.get('password')?.value;
        let confirmPassword = this.taskForm.get('confirmPassword')?.value;
        
        //Operamos con los datos obtenidos
    }
  }
```
En el código anterior se puede observar cómo se puede acceder a los valores de cada uno de los campos del formulario reactivo `registerForm` que ha sido definido. Una vez que se han obtenido todos los valores del formulario se pueden operar con ellos.


Para ello, será necesario configurar el formulario de nuestra plant en la etiqueta del formulario el siguiente evento

## 14.6. Carga de datos en un formulario reactivo.

En ocasiones es necesario realizar la precarga de los datos de un formulario, por ejemplo, cuando se está editando una de las tareas. En el momento que el usuario acceda al formulario es necesario que este se encuentre relleno con los datos de la tarea que desea editar. 

![task-editing](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/task-editing.png)

En la anterior ilustración se puede observar como se está editando la tarea con identificador `1` y cómo los campos del formulario se han rellenado con los datos de dicha tarea.

Para inicializar un formulario es necesario que nuestro controlador implemente la interfaz `OnInit` y dentro del método de la interfaz se realizará lo siguiente:
```ts
  ngOnInit(): void {
    //1. Obtención del identificador pasado por parámetro
    this.route.paramMap.subscribe((params)=>{
      let id = params.get("id");
      if(id){
        // 2. Comprobar que el parámetro :id sea diferente de null o undefined
        try{
          // 3. Convertimos el id a entero
          let idNumber = Number.parseInt(id);

          //4. LLamamos al método getById del servicio para obtener la tarea con el id indicado
          let task = this.taskService.getById(idNumber);

          //5. Verificamos que la tarea existe
          if(task){

            //6. Se inicializa el formulario con los datos, usando el método setValue
            this.taskForm.setValue(
              {id:task.id.toString(),
                createdAt:task.createdAt,
                name:task.name,
                description:task.description,
                priority:task.priority,
                status:task.status,
                expiresAt:task.expiresAt
              })
          }
        }catch{}
      }
    })
  }
```
En el código anterior se ha mostrado como inicializar un formulario. Fíjate cómo al método `setValue` se le está pasándo como parámetro un objeto cuyas claves corresponde al identificado de los campos del formulario definido y como valor la información de la tarea recuperada.


## RETO: Creación y edición de tareas

El objetivo de este reto es implementar toda la lógica necesaria para poder crear y editar tareas usando formularios reactivos. Para ello, trabajaremos sobre el componente `TaskFormComponent`.

A continuación se establecen los requisitos que debes cumplir para realizar el RETO:

1. Lo primero que deberás hacer es implementar un formulario HTML usando Bootstrap que nos permita añadir la información de una nueva tarea o editar una tarea existente. Este formulario deberá tener el siguiente aspecto:
![new-task-form](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/new-task-form.png)

2. Implementa toda la lógica necesaria en el componente para convertir el formulario HTML en un formulario reactivo. 

3. Añade las siguientes validaciones predeterminadas:

- Title: requerido y su longitud no puede ser superior a 50 caracteres.
- Descripcion: requerido y su longitud no puede ser superior a 250 caracteres.
- Prioridad: requerido.
- Estado: requerido.
- Fecha de expiración: requerido.


4. Implementa y configurale al formulario las siguietnes validaciones personalizadas:

- Prioridad: debe ser un valor válido para que cumpla con la definición del tipo `TaskPriority`.
- Status: debe ser un valor válido para que cumpla con la definición del tipo `TaskStatus`.
- Fecha de expiración. Debe ser una fecha mayor a la actual.

5. Realiza las modificaciones oportunas en la plantilla del componente para que se muestre visualmente si los campos que el usuario ha rellenados han sido validados correctamente o continenen algún error. Muestra también los errores específicos de cada campo.

7. Una vez realizada la validación del formulario, implementa la lógica necesaria para guardar una nueva tarea en el array de tareas. Una vez almacenada correctamente la nueva tarea será necesario realizar una redirección al listado de tareas.

8. Implementa toda la lógica necesaria para editar una tarea existente. Para ello, primeramente deberás realizar la precarga de los valores en el formulario y posteriormente realizar el guardado de los cambios que el usuario haya realizado. Una vez realizada la modificación de la tarea, será necesario realizar una redirección al listado de tareas.

# 16. Firebase

## 16.1 Integración de Firebase en un Proyecto Angular
![Integración de Firebase en un Proyecto Angular](https://www.youtube.com/watch?v=Ujfzdws-d_8)

## RETO: Integración de Firebase.

Realiza la integración de Google Firebase en tu proyecto Angular siguiendo las indicaciones del vídeo anterior.

## 16.2. Uso de Firebase Realtime Database

Para poder hacer uso de Realtime Database en nuestro proyecto Angular, lo primero que debemos hacer es inyectar el servicio `Database` en nuestro servicio.

```ts
  //OPCION 1
  constructor(private db:Database) { }

  // OPCION 2
  private db = inject(Database);
```

A continuación se muestran los diferentes métodos necesarios para poder realizar un CRUD de nuestros objetos Task en Planify. Los métodos que se os presenta a continuación son métodos genéricos, es decir, se está utilizando un objeto genérico para explicar su funcionalidad. Este objeto genérico en nuestro proyecto Planify representaría al objeto ``Task``.

### 16.2.1. Obtener todos los objetos de un nodo.

Para poder obtener todos los objetos almacenados en un nodo usaremos el método `listVal`. Como podrás observar, en el fragmento de código que se muestra a continuación, el identificador de cada uno de los nodos hijos `keyField` se le está estableciendo como valor al campo `id` de nuestro objeto ``Task``.

```ts
  getAllObjects():Observable<Object[]> {
    const objectRef = ref(this.db,"/node");
    
    // IMPORTANTE: { keyField: 'id' } mete la clave de Firebase 
    // dentro de la propiedad ID del objeto
    return listVal(objectRef,{keyField:'id'}) as Observable<Object[]>
  }
```
### 16.2.2. Obtener un objeto a partir de su id.

En el siguiente fragmento de código se os ejemplifica cómo obtener un objeto de un nodo. Como podéis observar, lo primero que se realiza es la construcción de la referencia que deseamos obtener de la base de datos, para lo cual, usaremos el identificador de dicho objeto. Una vez construida la referencia, accederemos al objeto usando el método ``get``, el cual devuelve una ``Promise`` de `DataSnapshot`.

Para simplificar el uso de este método nuestros componentes, se ha implementado también la obtención de la información del `DataSnapshot`. Es por ello, por lo que es necesario indicar que el método ``getObjectById`` es ``async``, para poder esperar ``await`` a que se resuelva la promose del método ``get``. Una vez que se ha resuelto la promesa se ha construido el objeto con la información del nodo más el identificado obtenido.

```ts
  async getObjectById(objectId:string):Promise<Object|null>{
    
    const objectRef = ref(this.db,`/node/${objectId}`);

    const data = await get(objectRef);

    if (data.exists()){
      
      // Devolvemos el objeto con el ID inyectado
      return {id:data.key, ...data.val()} as Object;
    }

    return null;
  }
```

### 16.2.3. Crear un nuevo objeto.
Par poder insertar un nuevo objeto de la base de datos usaremos el método ``push``. Este método insertará la información de nuestro objeto en un nuevo nodo hijo al que se le establecerá un identificador aleatorio. Como se puede observar en el fragmento de código siguiente, se está guardando toda la información del objeto excepto el ``id`` para evitar la redundancia de información.

```ts
  createObject(object:Object) {
    
    const objectRef = ref(this.db,`/node`);
    
    // Limpiamos el objeto: le quitamos el ID 
    // para no guardarlo en Firebase
    const {id,...dataToSave} = object;
    
    return push(objectRef,dataToSave);

  }
```

### 16.2.4. Actualizar un objeto.

A diferencia del método ``push``, el método ``update`` actualiza la información de un objeto ya existente. Es por ello, por lo que para construir la referencia de dicho objeto es necesario su identificado. 


```ts
  updateObject(object:Object){
    const objectRef = ref(this.db,`/node/${object.id}`);

    // Limpiamos el objeto: le quitamos el ID y la fecha de creación
    // para no guardarlo en Firebase
    const {id,createdAt,...dataToSave} = object;

    return update(objectRef,dataToSave)
  }

```

### 16.2.4. Borrar un objeto.

Para borrar un objeto de un nodo, es tan sencillo como construir la referencia de dicho objeto y pasárselo como parámetro al método ``remove``.

```ts
  removeObject(objectId:string): Promise<void>{
    const objectRef = ref(this.db,`/node/${objectId}`);

    return remove(objectRef)
  }
```

## RETO: Implementación de un CRUD de tareas usando Firebase Realtime Database.

El objetivo de este reto es realizar las modificaciones tanto en el servicio de ``TaskService`` como en los componentes ``TaskForm``, ``TaskResume`` y ``TaskList`` para implementar el CRUD de las Tareas de nuestra aplicación Planify usando la base de datos de Firebase.

## RETO: 
El objetivo de este reto es realizar las siguientes modificaciones en nuestro proyecto Planify para que cuando un usuario se autentique en nuestra aplicación se almacene en la base de datos la información personal de dicho usuario y además, se le permita el listado, creación, edición y borrado de sus tareas. Para ello, tomaremos como referencia el siguiente diagrama de clase:

![uml-task-person](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/uml-task-person.png)

Realiza las modificaciones oportunas en tu proyecto e implementa las clases y relaciones del diagrama anterior. NOTA: se ha decidido establecerle como nombre a la clase ``Person`` para evitar confusiones con las clase ``User`` de Firebase.

Implementa los siguientes requisitos funcionales:

- El sistema debe permitir registrarse a nuevos usuarios así como almacenar su información personal.
- El sistema debe permitir a un usuario autenticado listar sus tareas.
- El sistema debe permitir a un usuario autenticado crear una nueva tarea.
- El sistema debe permitir a un usuario autenticado modificar una de sus tareas creadas previamente.
- El sistema debe permitir a un usuario autenticado borrar una de sus tareas.

Implementa los siguientes requisitos no funcionales:

- Un usuario solo podrá acceder a las tareas que han sido creadas por él.
- Un usuario no podrá modificar las tareas de otro.

La estructura de la base de datos debe ser la siguiente:
![database-structure-task](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/database-structure-task.png)



TIP: 
Para poder obtener el listado de tareas de un usuario concreto, así como crear o modificar alguna tarea de un usuario es aconsejable usar el siguiente método dentro del ``TaskService``:

```ts
  private getUserAuth():User|null{
    return this.auth.currentUser;
  }
```
Este método os permitirá obtener el ``uid`` del usuario autenticado o ``null`` si no hay ningún usuario autenticado en la aplicación.

Otros fragmentos de códigos necesarios:

```ts

// Crear error en la promesa (catch)

Promise.reject(new Error("Error al modificar la tarea"));

// Permite crear un observable de un array vacío 

return of([])
```

# 17.Gestión de roles de un usuario

En este capítulo aprenderemos a implementar los mecanismos necesarios en nuestro proyecto de Planify para poder implementar un sistema de roles. El objetivo principal es permitirle el acceso a unas funcionalidades a aquellos usuarios que tengan ciertos roles, así como mostrarle las opciones del menú que correspondan.

Para poder llevar a cabo esto lo primero que debemos hacer es implementar un Guard personalizado y posteriormente veremos cómo mostrar una opción en el Navbar si el usuario autenticado tiene un rol en concreto.

Es importante recordar que para la autenticación estamos usando Firebase Autentication y estamos complementando esta con Firebase Realtime Database para almacenar información específica que nos interesa de los usuarios que se registran en nuestra aplicación.

![firebase-auth-database](https://raw.githubusercontent.com/joseprofeinformatica/angular-tutorial/refs/heads/main/readme-images/firebase-auth-database.png)

Vamos a ponernos manos a la obra:

## 17.1. Modificación de la clase `Person`

Para poder adaptar la funcionalidad de nuestra aplicación según los roles de los usuarios autenticados, lo primero que debemos hacer es modificar el objeto `Person` para añadirle una nueva propiedad llamada `role` que almacenará el rol de dicho usuario:

```ts

export type UserRole = 'ADMIN' | 'USER';

export interface Person {
  uid?:string;
  username: string;
  firstname: string;
  lastname:string
  email: string;
  role:UserRole;
}

```
En este ejemplo en concreto se ha establecido que los usuarios pueden ser administrador (ADMIN) o user (USER).

## 17.2 Obtención del usuario autenticado

Una pregunta que vamos a tener que realizarnos con mucha frecuencia es la siguiente: ¿Quién es la persona que está autenticada en este momento? ¿Qué roles tiene?. Para poder responder a esta pregunta vamos a implementar en el servicio `person.service.ts` el siguiente método:

```ts
//person.service.ts
    getPersonAuth():Observable<Person|null>{
      return this.authService.getUserAuthenticated().pipe(
        switchMap((user:User|null)=>{
          if(user && user.uid){
            return from(this.getPersonById(user.uid))
          }
          return of(null)
        })
      )
    }
```
el método `getPersonAuth` hace una llamada al método getUserAuthenticated implementado en el servicio `auth.service.ts`:

```ts
//auth.service.ts
  getUserAuthenticated(): Observable<User|null> {
    return authState(this.auth);
  }
```

El funcionamiento del método `getPersonAuth` es el siguiente:
1. Realiza una llamada a getUserAuthenticated para obtener el usuario de Firebase Auth autenticado en la aplicación. Este método devuelve un observable.
2. Para poder operar con los valores de un observable se está haciendo uso de la librería RxJS. Mediante `pipe` se está operando con los valores devueltos y con `switchMap` se está obteniendo la información de la persona autenticada de la base de datos, a partir de la información (UID) del usuario autenticado. En el supuesto que no exista un usuario autenticado se está devolviendo un Observable<null> con `of(null)`.

En resumen, se está cambiado el flujo del Observable<User|null> a un Observable<Person|null>.

## 17.3 Implementación de un guard personalizado.

Lo siguiente que realizaremos será la implementación de un guard personalizado para poder garantizar que un usuario solo pueda acceder a las rutas permitidas según sus roles. Para ello, lo primero que realizaremos será la creación del guard `ng generate guard guards/role` y seleccionamos el tipo `canActivate`. Una vez generado su contenido debe ser el siguiente:

```ts
//role.guard.ts

export const roleGuard: CanActivateFn = (route, state) => {
  
  // 1. Inyectamos los servicios necesarios
  const db = inject(Database);
  const router = inject(Router);
  const personService = inject(PersonService);

  // 2. Obtenemos el valor del parametro roles indicado en el app.guard.ts
  const roles:UserRole[] = route.data['roles'];

  // 3. Obtenemos la persona autenticada y operamos para modificar el flujo de datos
  return personService.getPersonAuth().pipe(

    // Tomamos solo el primer valor del observable
    take(1),

    // Convertimos de Person a true/false según los roles de la persona autenticada
    map((person) => {

      if(person){
        if (person.role && roles.includes(person.role)) {
          return true; //Acceso permitido
        }

        //No tiene los roles necesarios
        router.navigate(['/home']); //Redirigimos a /home
        return false; //Acceso denegado
      }else{
        //No hay niguna persona autenticada
        router.navigate(['/login']); //Redirigimos a /login
        return false; //Acceso denegado
      }
    })
  );
};
```

## 17.4. Uso del guard `roleGuard` en el `app.routes.ts`

Para poder garantizar que solo los usuarios con los roles establecidos puedan acceder a una ruta de nuestra aplicación, será necesario hacer uso del guard implementado en el archivo `app.routes.ts` de la siguiente forma:

```ts
// app.routes.ts
export const routes: Routes = [
    {path:'tasks', component:TaskListComponent,canActivate: [roleGuard],data: { roles: ['USER'] }}
]
```
Observa cómo en la sintaxis anterior solo se está permitiendo el acceso a la ruta `/tasks` a aquellos usuarios que tienen el rol ´USER´. Mediante `canActivate: [roleGuard]` se está indicando que la ruta se active si el Guard `roleGuard` devuelve `True` y además se le está pasando como parámetro el rol que debe tener el usuario para poder acceder a dicha ruta `data: { roles: ['USER'] }`


# 17.5. Mostras opciones del menú según el rol del usuario autenticado.

Para poder controlar las opciones del componente `Navbar` que se desean mostrar según el rol del usuario autenticado, será necesario llamar al método `getPersonAuth()` en el servicio `person.service.ts` y pasarle a la vista `navbar.component.html` la información de la persona autenticada para poder mostrar unas opciones u otras según los roles de esta:

```ts
// navbar.component.ts
@Component({
  selector: 'app-navbar',
  imports: [CommonModule,RouterLink],
  templateUrl: './navbar.component.html',
  styleUrl: './navbar.component.css'
})
export class NavbarComponent implements OnInit {

  public authService = inject(AuthService);
  public personService = inject(PersonService);
  private router = inject(Router);
  personAuth: Person | null = null;

  ngOnInit(): void {
    this.personService.getPersonAuth().subscribe((person:Person|null)=>{this.personAuth=person})
  }

  logout(){
    this.authService.logout();
    this.router.navigate(["/home"])
  }
}
```

```html
<!--navbar.component.html-->
        <li *ngIf="personAuth!=null && personAuth.role == 'USER'" class="nav-item">
          <a class="nav-link" routerLink="/tasks">Tasks</a>
        </li>
```

# Bibliografía

https://www.tutorialesprogramacionya.com/

https://blog.enriqueoriol.com/
