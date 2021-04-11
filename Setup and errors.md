# ant-design-project

* [Setup](#setup)

* [Config Errors](#errors)

## Set up an angular project with antdesign <a name="setup"></a>

install angular
```
$ npm install -g @angular/cli 
```

craate new project
```
$ ng new NAME
```

install ng-zorro-antd
```
$ cd PROJECT-NAME
$ ng add ng-zorro-antd
```

#### Import styles:

Under Angular.json:

```
{
  "styles": 
  [
     "node_modules/ng-zorro-antd/ng-zorro-antd.min.css",
     "src/theme.less",
     "src/styles.scss"
  ],
}
```

Import the pre-built stylesheet in style.css

```
@import "~ng-zorro-antd/ng-zorro-antd.min.css";
```
Import the less stylesheet in style.less
```
@import "~ng-zorro-antd/ng-zorro-antd.less";
```

Import component module

you have to add component module into yur module files
ep:
```
import { NgModule } from '@angular/core';
import { NzButtonModule } from 'ng-zorro-antd/button';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    NzButtonModule
  ]
})
export class AppModule { }
```

## Common Errors<a name="errors"></a>

1. Error: 'nz-card' is not a known element.

Make sure import the component modules that you want to use into the module.ts file

2. error NG6002: Appears in the NgModule.imports of WelcomeModule, but could not be resolved to an NgModule class.
    
    This likely means that the library (ng-zorro-antd/card) which declares NzCardModule has not been processed correctly by ngcc, or is not compatible with Angular Ivy. 
    Check if a newer version of the library is available, and update if so. Also consider checking with the library's authors to see if the library is expected to be compatible with Ivy.

[Solved](https://github.com/NG-ZORRO/ng-zorro-antd/issues/6359) : 

1. Update Angular and TypeScript ect, run npm update
2. add ``` "aot" : true ``` in your angular json file under build and configurations 
3. add this into tsconfig.app.json file 

```
"angularCompilerOptions": {
    "enableIvy": true
  },
```
4. delete your package-lock.json / yarn.lock files, remove node_modules directory, run npm i / yarn commands







