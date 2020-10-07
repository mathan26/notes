## Change the application title
 - The double curly braces are Angular's interpolation binding syntax. 
 - This interpolation binding presents the component's title property value inside the HTML header tag.
## Create the heroes component
 - `ng generate component heroes`
 - The CLI creates a new folder, src/app/heroes/, and generates the three files of the HeroesComponent along with a test file.
 - You always import the Component symbol from the Angular core library and annotate the component class with @Component.
 - `@Component` is a decorator function that specifies the Angular
   metadata for the component.

The CLI generated three metadata properties:

 - **selector**— the component's CSS element selector
 - **templateUrl**— the location of the component's template file.
 - **styleUrls**— the location of the component's private CSS styles.
 - The `ngOnInit()` is a lifecycle hook. Angular calls ***ngOnInit() shortly
   after creating a component***. It's a good place to put *initialization
   logic*.
 - Always **export** the component class so **you can import it elsewhere** ... like in the AppModule.
## Show the HeroesComponent view
 - To display the HeroesComponent, you **must add it to the template of the shell AppComponent**.
 - Remember that **app-heroes** is the element **selector for the HeroesComponent**. 
 - So add an `<app-heroes>` element to the AppComponent template file, just below the title.

## Create a Hero interface

 - Create a Hero interface in its own file in the src/app folder. Give it id and name properties.
## Show the hero object
 - Update the binding in the template to announce the hero's name and show both id and name in a details layout like this:
 ## Format with the UppercasePipe

     {{hero.name | uppercase}} Details

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ3OTQxNjMxMCwxOTg4ODg0ODAxLC03NT
cyMTQ3ODhdfQ==
-->