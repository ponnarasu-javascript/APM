# Angular-gettingstarted-ps
# introduction
## what is Angular
JS framework used in the frontend application
## why Angularjs
modular design, buildin backend integration, powerful data binding, expressive html
## how they marketed to world
moderen js framework, will enhance the productivity who uses
## structure
each applicaiton = several components + services
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/anatomyofangular.PNG "anatomy")
component = html template + classes + metadata
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/component.PNG "component")
modules -> componenents are mapped to the application by modules. min 1 module mandate for the application
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/modules.PNG "modules")


# steps to follow any application
## 1.each page - each component- design with requirement wireframe
main welcome page
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/welcome.PNG "welcome page")
product list page
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/productlist.PNG "productlist page")
product details page
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/productdetail.PNG "productdetail page")
created each component for each page. if component can be reused by 2 component we created sub component. all components are tied together by app comp or module. these are passed to main index page.
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/thisapparchitecture.PNG "this sample app architecture")

## 2.with design ready - get boiler code to getting started
- we can create manully the folder structure. but we have boiler code already available
- use angular quick start boiler code (https://github.com/angular/quickstart)
- use angular CLI tooling to create components and package structure 
(https://github.com/angular/angular-cli)
- use intructor boiler code for this sample app as some extra stuffs are added for this project 
(https://github.com/DeborahK/Angular-GettingStarted)
**APM-Start:** The starter files set up for use in VSCode, WebStorm, or other editors. Use this to code along with the course. (Updated for Angular version 4.3 or higher)
**APM-Final:** The completed files. Use this to see the completed solution from the course. (Updated for Angular version 4.3 or higher)

Download the github app folders and copy paste the APM-start files to APM.
very useful (https://angular.io/guide/quickstart)
## 3. any application - follow the following
- create the app folders > can get from boiler code
- add package definition package json / config files
- install the packages > npm install will install dependencies
- create app angular module > atleast one required for a project
- create main.ts > to add the angular module
- create main page > usually index.html


# selecting the language/ editors/ npm 
- **VSCode** is used here
- ECMA script based language is many. java script has versions ES2016, ES2015, ES 5 & lower or typescript language(superset of js or like js)
we use type script since it supports all the latest ecma standards. we cant use directly in browser as most of them yet to support es2015+.
so typescript are transpiled and use in application. usually we minifest the js and run in app.
- download npm and code in the machine. package manager and the other is serverjs frame work. browser js has limitation like threading, file reading etc. but server has no restrictions.

## First look on project folder
- Application usually have src -> which contains source files. here app sub-dir contains applicaiton specific files. will add more when requirements increase.
- 1st step with boiler code would be -> install dependencies using npm.
  >npm install // dwns dependencies mentioned in pacakge.json and put it in /node_modules. no need to check in these files. add them entries in .gitignore 

# concept 1 - modules
modules - for code organisation and variable out of global space in js. 
- ECMA2015 has specification for modules. as per ecma2015, modules are files with export or import which becomes modules
- angular also has ecma2015 module concept. Also it has its own angular modules.
- typescript also has modules

ECMA2015 modules - organize the code.
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/module_2015.PNG "ECMA 2015 Modules")
Angular modules - organize the application.
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/module_Angular.PNG "Angular Modules")

# concepts 2 - components
we write many components and make them work together. we return results to angular module.
**components** = template + class +metadata
- **template** : view layout with binding and directive
- **class** : code to support the view. property + methods
- **metadata** : defined with decorator. extra info **for the angular module**
![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/component-eg.PNG "Angular Modules")
This has class component + metadata component
**meta data** - is A function that adds metadata to a class. prefixed with @. there are lot of decorators available in built.
selector value is used in the template associated with the class.
**import statement** - import from third party lib or own modules which exports. 
eg of angular own modules : @angular/core , @angular/animate, @angular/http, @angular/router

# concept 3 - bootstraping our application
we wrote component and templates. how to bring to the front end or to the angular app.
2 steps in bootstraping:
- index.html (single page application)
```
<div>
<pm-root></pm-root>
</div> 
```
// **when angular see directive .passes from bootstrap module.  it checks the app module**

- App module: atleast one app **module** requires to a application. 

//usually ng module, browser module and our bootstrap module is present.
```
code:
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core'; 
import { AppComponent } from './app.component';

@NgModule({ // it decorator and has  array of elements
  declarations: [  AppComponent  ], // declares all the modules used in front page. index can check the all the selectors from these components.
  imports: [    BrowserModule  ], // external modules or own available to all the components
  providers: [], // it is for services
  bootstrap: [AppComponent] // which is the first module to compile. this component contains the root selector in index.html
})
export class AppModule { }
```

# component as directive
directives - extending the html. if we give <pm-root> it will generates piece of code and attach to the dom

![Alt text](https://github.com/ponnarasuice/Angular-gettingstarted-ps/blob/master/readme_images/component as directive.PNG "component as directive")

### structural directives - built in directives to use in html
*nfIf  - condition in the template
*ngFor - can iterate the objects.
```
{{showImage ?'hide':'show'}}
<img *ngIf='showImage'>
```
###interpolation
from class property to template

in template - we can use {{title name}}
component - properties are declared for this purpose
```
<img [src]='product.imagesrc'> //it is recommended
<img src={{product.imagesrc}}>
```
### event binding
```
<button (click) ='toggleImage()'>
// all the events are listed here (https://developer.mozilla.org/en-US/docs/Web/Events)
export class Listcomponent{
  toggleImage():void{
    ////
  }
}
```
### 2 way binding
```
<input type='text' [{ngModel}]='listFilter'>
------
<h3>filtered by {{listFilter}}</h3>

class productlist{
  listFilter: string = 'cart';
}
// ngModel directives are available in angular form module
// so need to include it in app module
app.module.ts
import {formModule} from '@angular/forms';

imports[browsermodule, formmodule]

```
#components 
eg:
```
@Component({
  selector: 'pm-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Angular: Getting Started';
}
```
###strong typing
most of the properites of strong typing in type script
eg: private welcome:string = 'hello';

###Inerfaces
es2015 didnt support interfaces but typescript does. so it is used as data type in development only.
```
export interface Iproduct{
  productId:String;
  calculate(percent:number):number;
}
``` 
```
import {Iproduct} from './Product';

export class ProductComponent{

  products:Iproduct[]=[
    {
      "productId":2,
      "productname":'brush'
    },
    {
      .....
    }
  ];
}
```
###Life cycle hooks
create - perform initialization
render
create&renderchildren
process change - eg:onchanges - perform action after change to input property
destroy - eg:onDestroy -perform cleanup
```
import {component, OnInit} from '@angualr/core';
export class productcomponent implements OnInit{ // built in angular lifecycle hooks. use by implements the ng interface
  ..........
  ngOnInit():void{
    console.log('');
  }
}
```
###Pipes - transform the values before display. we have built-in pipes. can write custom pipes
```
inbuilt: use in template
{{product.price|currency}}
custom pipe:
import {Pipe,PipeTransform} from '@angualr/core';
@Pipe({
  name:'convertPipe';
})
export class convertto implements PipeTransform{
  transform(value:string,character:string){
    return value.replace(character,' ');
  }
}

in template:
<td>{{product.productcode | convertpipe:'-'}}</td> // here we are replace - with spaces
```

###filter the list in component
```
//listfilter='cart' change to have- getter and setter
//in setter assign value to listfilter
listfilter:string;
set listfilter(value:string){
  this.listfilter = value; // given in the input box
  this.filteredList = this.listfilter? this.performfilter:this.product; //have original product if something given in input box, it is filtered
}
filteredList:Iproduct[];
product:Iproduct[.....]//stores original values

//filter function
performfilter(filterBy:string):Iproduct[]{
  filterBy = filterBy.tolowercase();
  //this is inbuilt array function
  return this.products.filter((product:Iproduct)=>
      product.productname.tolowercase().indexOf(filterBy)!==-1);
}

template: 
<tr *ngFor='let product of filteredproducts'>
```
###summary is that
- 1 index.html having root directive like <pm-root>
- min 1 module which combines all the components in the application. it also specifies bootstrap html
- components = template + component + metadata. in component selector is given(we give this selector in the template). inline template or template url is given. also can give style sheets. class has property and methods. properties for 1 way binding. methods for event handling.
