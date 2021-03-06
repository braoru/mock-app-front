Mock App Front-end
==================

## Install needed binaries
### npm
```
npm install
```
### Angular CLI
```
npm install -g @angular/cli
```
## Generate code from scratch
### Initialize Angular project
```
ng new mock-app-front
```
### Setup Bootstrap (incl. ngx-bootstrap)
#### Install the needed NPM dependencies
```
cd mock-app-front
npm install jquery popper.js ajv bootstrap ngx-bootstrap ng-event-source --save
```
#### Import CSS
In the file .\.angular-cli.json, add the following path to the array apps.styles :
```
../node_modules/bootstrap/dist/css/bootstrap.min.css
```
#### Import module
Open ./src/app/app.module.ts and the modules you need to "@NgModule.imports".
e.g. :
```
import { BsDropdownModule } from 'ngx-bootstrap/dropdown';
import { TooltipModule } from 'ngx-bootstrap/tooltip';
import { ModalModule } from 'ngx-bootstrap/modal';
//...
@NgModule({
  //...,
  imports: [
    //...,
    BsDropdownModule.forRoot(),
    TooltipModule.forRoot(),
    ModalModule.forRoot()
  ],
  //...
})
export class AppModule { }
```
### Setup Font Awesome
#### Install the needed NPM dependency
```
cd mock-app-front
npm install font-awesome angular-font-awesome --save
```
#### Import CSS
In the file .\.angular-cli.json, add the following path to the array apps.styles :
```
../node_modules/font-awesome/css/font-awesome.css
```
#### Import module
Open ./src/app/app.module.ts and add the following :
```
import { AngularFontAwesomeModule } from 'angular-font-awesome';
//...
@NgModule({
  //...
  imports: [
    //...,
    AngularFontAwesomeModule
  ],
  //...
})
export class AppModule { }
```
### Setup OIDC
#### Install the needed NPM dependency
```
cd mock-app-front
npm install angular-oauth2-oidc --save
```
#### Import module
Open ./src/app/app.module.ts and add the following :
```
import { OAuthModule } from 'angular-oauth2-oidc';
//...
@NgModule({
  //...
  imports: [
    //...,
    OAuthModule.forRoot()
  ],
  //...
})
export class AppModule { }
```

## Internationalization
### Generate the translation file
```
cd mock-app-front
ng xi18n --locale en --outputPath src/locale
```
It generates the file ./src/locale/messages.xlf.
### Translate the file
Copy messages.xlf to messages.fr.xlf. Open it, create a new <target/> node after each <source/> node containing the translated version.
### Run the application in a given language
```
cd mock-app-front
ng serve -aot --i18nFile=src/locale/messages.fr.xlf --i18nFormat=xlf --locale=fr --open
```

## Add a new component
```
cd mock-app-front
ng generate component name-of-your-component
```
Then add the component in src\app\app.component.spec.ts :
```
...
import { NameOfYourComponentComponent } from './name-of-your-component/name-of-your-component.component';
...
  beforeEach(async(() => {
    TestBed.configureTestingModule({
      declarations: [
        AppComponent,
        ...,
        NameOfYourComponentComponent
      ],
    }).compileComponents();
  }));
...
```

## Build
```
```

## Run
```
cd mock-app-front
ng serve --open
```

## Run Jasmine unit tests with Karma
```
cd mock-app-front
ng test
```

## Bibliography
* [ngx-bootstrap](https://valor-software.com/ngx-bootstrap/#/)
* [angular-font-awesome](https://github.com/baruchvlz/angular-font-awesome)
* [How to Add Bootstrap to an Angular CLI project](https://loiane.com/2017/08/how-to-add-bootstrap-to-an-angular-cli-project/)
* [Angular Internationalization (i18n)](https://angular.io/guide/i18n)
