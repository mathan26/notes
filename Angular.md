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

 - The word uppercase in the interpolation binding, right after the pipe operator ( **|** ), **activates the built-in UppercasePipe.**
 - Pipes are a good way to format strings, currency amounts, dates and other display data. Angular ships with several built-in pipes and you can create your own.
## Edit the hero

 - `[(ngModel)]` is Angular's two-way data binding syntax.
 - Here it binds the hero.name property to the HTML textbox so that data can flow in both directions: from the hero.name property to the textbox, and from the textbox back to the hero.name.


**The missing FormsModule**

 - Although ngModel is a valid Angular directive, it isn't available by default.
 - It belongs to the optional FormsModule and you must opt-in to using it.
 
 **AppModule**
 

 - Angular needs to know how the pieces of your application fit together and what other files and libraries the app requires. This information is called metadata.
 - Then add FormsModule to the `@NgModule` metadata's imports array, which contains a list of external modules that the app needs.
 
**Declare HeroesComponent**

 - Every component must be declared in exactly one NgModule.
 - The HeroesComponent is declared in the @NgModule.declarations array.
## Display a selection list

 - Create mock heroes
 - List heroes with ***ngFor**
 - `*ngFor="let hero of heroes"`
 - Don't forget the asterisk (*) in front of ngFor. It's a critical part of the syntax.
 -  **Master/Detail**
 - `<li *ngFor="let hero of heroes" (click)="onSelect(hero)">`
 - Add the click event handler
 - Add the following onSelect() method, which assigns the clicked hero from the template to the component's selectedHero.

**Add a details section**

 - Wrap the hero detail HTML in a <div>. Add Angular's *ngIf directive to the <div> and set it to selectedHero.
 - [class.selected]="hero === selectedHero"
 - You can toggle a CSS style class with a class binding.


## Create a feature component

    ng generate component hero-detail

 - Write the template

	     <div *ngIf="hero">
	    
	      <h2>{{hero.name | uppercase}} Details</h2>
	      <div><span>id: </span>{{hero.id}}</div>
	      <div>
	        <label>name:
	          <input [(ngModel)]="hero.name" placeholder="name"/>
	        </label>
	      </div>
	    
	    </div>

  **Add the @Input() hero property**
  

 - The hero property must be an ***Input property***, annotated with the `@Input()` decorator, because the external HeroesComponent will bind to it like this.

	    <app-hero-detail [hero]="selectedHero"></app-hero-detail>
	    

 - Add a hero property, preceded by the @Input() decorator.

	     @Input() hero: Hero;
**Show the HeroDetailComponent**

 - The two components will have a parent/child relationship. The parent HeroesComponent will control the child HeroDetailComponent by sending it a new hero to display whenever the user selects a hero from the list.
 - You won't change the HeroesComponent class but you will change its template.
**Update the HeroesComponent template**
		  `

	    <app-hero-detail [hero]="selectedHero"></app-hero-detail>
	    

> [hero]="selectedHero" is an Angular property binding.

*Refactoring the original HeroesComponent into two components yields benefits, both now and in the future:*

 1. You simplified the HeroesComponent by reducing its responsibilities.
 2. You can evolve the HeroDetailComponent into a rich hero editor
    without touching the parent HeroesComponent.
 3. You can evolve the HeroesComponent without touching the hero detail
    view.
 4. You can re-use the HeroDetailComponent in the template of some
    future component.

  



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYwOTUwNDIwMSwtNDM5NTc0MDQ2LC0xNT
U0MDUzOTQ3LDIwMjc2MTc3NTIsNDQwNTkxMzcwLDgwMjc0NDEz
Myw2MDc1Mjc0NzEsLTgxMjczMDkxMiwtMTQ3NDM0MDc2MywtMT
kxMTY5OTg2MSwxNTMxMTU0MzI5LDE5ODg4ODQ4MDEsLTc1NzIx
NDc4OF19
-->