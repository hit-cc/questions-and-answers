# what is an Angular ?

Angular is an open-source TypeScript based framework developed by Google for building web and mobile applications. 
It follows a component-based architecture and provides features like two-way data binding, dependency injection, and routing. 
It allows developers to create dynamic and responsive web applications efficiently.


## Lifecycles of angular components.

In Angular, components have various lifecycle hooks that allow you to perform actions at different stages of a component's lifecycle. 

  - ngOnChanges: This event is called when the input properties of a component change. It receives a SimpleChanges object that contains the previous and current values of the input properties.

  - ngOnInit: This event is called once, after the component has been initialized and its input properties have been set. It is commonly used for initialization tasks, such as retrieving data from a server.

  - ngDoCheck: This event is called during every change detection cycle. It is used to detect and respond to changes that Angular cannot automatically detect.

  - ngAfterContentInit: This event is called after the component's content has been projected into its view. It is commonly used when a component needs to interact with its projected content, such as querying child components or manipulating the DOM.

  - ngAfterContentChecked: This event is called after the component's content has been checked for changes. It is commonly used when a component needs to perform additional operations after its content has been updated.

  - ngAfterViewInit: This event is called after the component's view and child views have been initialized. It is commonly used when a component needs to interact with its view, such as querying elements or setting up event listeners.

  - ngAfterViewChecked: This event is called after the component's view and child views have been checked for changes. It is commonly used when a component needs to perform additional operations after its view has been updated.

  - ngOnDestroy: This event is called just before the component is destroyed. It is commonly used for cleanup tasks, such as unsubscribing from observables or releasing resources.

These lifecycle hooks provide opportunities to perform actions such as initializing data, subscribing to observables, cleaning up resources, or interacting with the DOM at specific points in a component's lifecycle.



# Key features of Angular.

    1. Two-way data binding: 
    Angular provides a powerful data binding system that allows changes in the model to automatically reflect in the view and vice versa.

    2. Component-based architecture: 
    Angular follows a component-based architecture where the application is divided into reusable and independent components, making it easier to manage and maintain the code.

    3. Dependency injection: 
    Angular has a built-in dependency injection system that helps manage dependencies between different components and services, making the code more modular and testable.

    4. Routing: 
    Angular has a powerful routing system that allows developers to define and navigate between different views in the application, enabling the creation of single-page applications.

    5. Forms: 
    Angular provides a robust and flexible form handling mechanism, including features like form validation and error handling.

    6. Directives: 
    Angular provides a set of built-in directives that allow developers to extend HTML with new attributes and behaviors, making it easier to manipulate the DOM and create dynamic web applications.

    7. Testing: 
    Angular has built-in testing utilities and tools that make it easier to write unit tests and ensure the quality and reliability of the application.

    8. Internationalization (i18n): 
    Angular supports internationalization and provides tools to easily translate and localize applications.

    9. Mobile development: 
    Angular has features and tools that facilitate the development of mobile applications, including responsive design and touch support.

    10. Performance optimization: 
    Angular provides features like lazy loading and Ahead-of-Time (AOT) compilation to optimize the performance of the application.

    11. CLI (Command Line Interface): 
    Angular has a powerful command line interface that helps with scaffolding, building, and testing applications, making development tasks more efficient.

    12. Active community and ecosystem: 
    Angular has a large and active community of developers, which means there are plenty of resources, tutorials, and libraries available for support and enhancement of Angular applications.


## Data binding and types.

In Angular, data binding is a powerful feature that allows you to establish a connection between the component's data and the template, enabling automatic synchronization and updating of values. There are four types of data binding in Angular:

1. Interpolation (One-way binding):
Interpolation allows you to embed expressions within double curly braces {{ }} in the template. The expression is evaluated and the result is displayed in the rendered view. It is a one-way binding from the component to the template.

Example: 

`<h1>{{ title }}</h1>`

2. Property binding (One-way binding):
Property binding allows you to bind a component property to an element property in the template using square brackets []. The component property value is assigned to the element property, and any changes to the component property will update the element property.

Example: 

`<img [src]="imageUrl">`

3. Event binding (One-way binding):
Event binding allows you to bind an event in the template to a method in the component using parentheses (). When the event is triggered, the associated method is executed in the component.

Example: 

`<button (click)="handleClick()">Click me</button>`

4. Two-way binding:
Two-way binding is a combination of property binding and event binding. It allows you to bind a component property to an element property and establish a two-way synchronization between them. Any changes to the component property or the element property will automatically update the other.

Example: 

`<input [(ngModel)]="name">`

These types of data binding in Angular provide a flexible and efficient way to handle data flow between the component and the template, allowing for dynamic and interactive user interfaces.


## Dependency Injection:

In Angular, Dependency Injection (DI) is a design pattern that allows components and services to have their dependencies provided to them by an external entity. This helps to decouple the components and services from the creation and management of their dependencies, making them more modular, reusable, and testable.

To illustrate DI in Angular, let's consider an example:

1. Define a Service:

```typescript
@Injectable()
export class UserService {
  getUsers() {
    return ['John', 'Jane', 'Bob'];
  }
}
```

2. Use the Service in a Component:

```typescript
@Component({
  selector: 'app-user-list',
  template: `
    <h2>User List</h2>
    <ul>
      <li *ngFor="let user of users">{{ user }}</li>
    </ul>
  `
})
export class UserListComponent {
  users: string[];

  constructor(private userService: UserService) { }

  ngOnInit() {
    this.users = this.userService.getUsers();
  }
}
```

3. Register the Service in a Module:

```typescript
@NgModule({
  declarations: [
    UserListComponent
  ],
  providers: [
    UserService
  ]
})
export class AppModule { }
```

In this example, we have a `UserService` class that provides a `getUsers()` method to retrieve a list of users. The `UserListComponent` has a dependency on the `UserService` and uses it to fetch the users in its `ngOnInit()` lifecycle hook.

To enable DI, we annotate the `UserService` class with the `@Injectable()` decorator. Then, in the `UserListComponent`, we declare a constructor parameter with the type `UserService` and mark it as `private`. This tells Angular to inject an instance of `UserService` when creating the `UserListComponent`.

Finally, we register the `UserService` in the `providers` array of the module that contains the `UserListComponent`. This makes the `UserService` available for injection throughout the module.

By using DI, Angular takes care of creating and managing instances of the `UserService` and injecting them into the `UserListComponent`. This promotes loose coupling and makes it easier to swap dependencies or mock them during testing.


## Angular Universal:

Angular Universal is a server-side rendering (SSR) solution for Angular applications. 
It allows you to render your application on the server and send the pre-rendered HTML to the client, improving the initial loading time and enabling search engine optimization (SEO). Angular Universal works by running your Angular application on a Node.js server and generating HTML on the server side, which is then sent to the client.


## Pipe Chaining:

Pipe chaining in Angular refers to the ability to apply multiple pipes consecutively to transform data in a template. By using the pipe operator (|), you can chain multiple pipes together to perform a series of transformations on a value. 
For example, you can chain the `uppercase` and `date` pipes to convert a string to uppercase and then format it as a date.


## Custom Pipe:

In Angular, a custom pipe allows you to create your own reusable transformation logic for data displayed in templates. 
Custom pipes are defined using the `@Pipe` decorator and implementing the `PipeTransform` interface. 
They can be used to format, filter, or transform data in various ways. Custom pipes can be applied in templates using the pipe operator (|) followed by the name of the custom pipe.

## Pipes Types
In Angular, pipes are used for data transformation in templates. There are two types of pipes: pure pipes and impure pipes.

1. **Pure Pipes**:
   - Pure pipes are stateless. They do not maintain any internal state.
   - They are executed only when Angular detects a pure change to the input value (i.e., the input value or its reference has changed).
   - Pure pipes are more efficient because they are called only when necessary.
   - Example: The `UpperCasePipe` is a pure pipe that transforms a string to uppercase.

   ```html
   {{ 'hello' | uppercase }} <!-- Output: 'HELLO' -->
   ```

2. **Impure Pipes**
   
   - Impure pipes may have internal state or perform costly operations that are not dependent on the input value.
   - They are executed every time change detection runs, regardless of whether the input value has changed.
   - Impure pipes can impact performance if used carelessly because they run frequently.
   - Example: The `DatePipe` is an impure pipe that formats a date. Since it doesn't rely solely on the input, it's impure.

   ```html
   {{ today | date:'short' }}
   ```

Here's a comparison with an example:

```typescript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'custom'
})
export class CustomPipe implements PipeTransform {
  transform(value: string): string {
    return value + ' transformed';
  }
}
```

Using this pipe in a template:

```html
<!-- Pure Pipe -->
{{ 'hello' | custom }} <!-- Output: 'hello transformed' -->

<!-- Impure Pipe -->
{{ 'hello' | custom }} <!-- Output: 'hello transformed' -->
```

In this example, whether you use the `CustomPipe` as a pure or impure pipe, the result is the same. However, if you had some costly operations or internal state management within `CustomPipe`, it would be better to use it as an impure pipe only when necessary to avoid unnecessary computations.

## Async Pipe:

The Async Pipe in Angular is a built-in pipe that simplifies the handling of asynchronous data streams, particularly Observables or Promises, in templates. 
The Async Pipe subscribes to an Observable or Promise and automatically updates the view with the latest emitted value. It also handles the unsubscribing process when the component is destroyed, preventing memory leaks. The Async Pipe is commonly used to display data that is fetched asynchronously from APIs or services directly in the template.
    
Using the Async Pipe eliminates the need for manual subscription management and simplifies the code, making it more readable and maintainable.


## Interceptor:

Interceptors in Angular are used to intercept HTTP requests and responses globally, allowing you to modify or handle them before they reach the server or the client. 
Interceptors are implemented by creating a class that implements the `HttpInterceptor` interface and providing custom logic in the `intercept` method. Interceptors can be used for tasks such as adding headers, handling errors, or modifying request/response data.


## router-outlet:

`router-outlet` is a directive in Angular that acts as a placeholder for dynamically loaded components based on the current route. It is used in the template of the component that represents the main container for routing in an Angular application. The router-outlet directive is responsible for rendering the appropriate component based on the current route configuration.

## AuthGuard:

AuthGuard is an implementation of the Angular `CanActivate` interface that is used to protect routes and control access to certain parts of an application. It allows you to define rules and conditions that must be met before a user can access a specific route. AuthGuard is commonly used for implementing authentication and authorization logic in Angular applications.


## ng-container:

`ng-container` is a structural directive in Angular that provides a way to group multiple elements without adding an extra element to the DOM. It is useful when you need to apply structural directives like `ngIf` or `ngFor` to a group of elements without adding an extra wrapper element.

## Custom Directive:

In Angular, a custom directive is a reusable component-like feature that allows you to extend the functionality of HTML elements or components. Custom directives can be used to manipulate the DOM, add behavior, or modify the appearance of elements. They are defined using the `@Directive` decorator and can be applied to elements using attribute selectors.

## Form Types:

In Angular, there are different types of forms that can be used to handle user input and perform form validation. The main types are:
    
- Template-driven forms: These forms rely on directives and two-way data binding to handle form controls and validation. They are easier to set up but offer less control and flexibility compared to reactive forms.

- Reactive forms: These forms are based on reactive programming principles and use an explicit approach to handle form controls and validation. They provide more control and flexibility, making them suitable for complex forms and dynamic form scenarios.

## Sharing Data Between Components:

There are several ways to share data between components in Angular:
  
- Using @Input and @Output decorators: @Input allows a parent component to pass data to a child component, while @Output allows a child component to emit events to a parent component.

- Using a shared service: Components can communicate with each other through a shared service by injecting it into the components and using it to store and retrieve data.

- Using route parameters or query parameters: Components can share data by passing parameters through the URL using route parameters or query parameters.

- Using state management libraries: Libraries like NgRx or Akita can be used to manage application state and share data between components.


## What is Directives ? Types of Directives and usage of directives.

In Angular, directives are a way to extend the functionality of HTML elements or create custom HTML elements. 
They allow you to manipulate the DOM, apply styles, handle events, and more.

There are three types of directives in Angular:

1. Component Directives: 

These are the most common type of directives and are used to create reusable UI components. Components have their own templates, styles, and behavior. They are declared using the `@Component` decorator.

Example:
```typescript
@Component({
  selector: 'app-custom-component',
  template: '<h1>Hello, World!</h1>'
})
export class CustomComponent { }
```

2. Attribute Directives: 

These directives are used to change the appearance or behavior of an existing element by applying attribute-like behavior to them. They are declared using the `@Directive` decorator.

Example:
```typescript
@Directive({
  selector: '[appCustomDirective]'
})
export class CustomDirective {
  constructor(private elementRef: ElementRef) {
    this.elementRef.nativeElement.style.color = 'red';
  }
}
```

3. Structural Directives: 

These directives are used to change the structure of the DOM by adding or removing elements. They are denoted by an asterisk (*) prefix in their syntax and are declared using the `@Directive` decorator.

Example:
```html
<div *ngIf="isLoggedIn">Logged in</div>
```

In this example, the `*ngIf` directive is a structural directive that conditionally adds or removes the `<div>` element based on the value of the `isLoggedIn` property.

Directives can be used in various ways in Angular, such as:

- Applying attribute-based behavior to elements.
- Manipulating the DOM.
- Controlling the visibility or behavior of elements.
- Creating reusable UI components.
- Implementing custom validation logic.
- Enhancing the functionality of existing elements or components.

By using directives, you can extend the capabilities of HTML and create more dynamic and interactive web applications in Angular.

Here is a list of commonly used directives in Angular along with their types:

1. ngIf: Structural Directive
   - Usage: Conditionally adds or removes an element from the DOM based on a condition.
   - Example: `<div *ngIf="showElement">Content to be shown</div>`

2. ngFor: Structural Directive
   - Usage: Renders a template for each item in a collection.
   - Example: `<li *ngFor="let item of items">{{ item }}</li>`

3. ngStyle: Attribute Directive
   - Usage: Dynamically applies CSS styles to an element.
   - Example: `<div [ngStyle]="{ 'color': textColor, 'font-size': fontSize }">Styled Content</div>`

4. ngClass: Attribute Directive
   - Usage: Dynamically adds or removes CSS classes from an element.
   - Example: `<div [ngClass]="{ 'highlight': isHighlighted, 'bold': isBold }">Styled Content</div>`

5. ngModel: Attribute Directive
   - Usage: Creates a two-way data binding between a form control and a component property.
   - Example: `<input [(ngModel)]="name">`

6. ngSwitch: Structural Directive
   - Usage: Conditionally renders a template based on a provided value.
   - Example:
     ```html
     <div [ngSwitch]="color">
       <div *ngSwitchCase="'red'">Red Color</div>
       <div *ngSwitchCase="'blue'">Blue Color</div>
       <div *ngSwitchDefault>Default Color</div>
     </div>
     ```

7. ngClass, ngStyle, ngModel, and ngSwitch are Attribute Directives and ngIf and ngFor are Structural Directives.

These are just a few examples of the directives available in Angular. Directives allow you to manipulate the DOM, apply styles, handle events, and more, providing a powerful way to extend the functionality of HTML elements or create custom HTML elements in Angular.