## RX JS

  **Q-1** :   What is RxJS ? explain in breaf.

  **Ans:  RxJS**, which stands for Reactive Extensions for JavaScript.
    - It is a popular library for reactive programming in JavaScript and TypeScript.
    - It provides a set of powerful tools and patterns for working with asynchronous and event-based data streams
    - RxJS allows developers to work with streams of data in a more elegant and declarative manner.
    - Here are some key concepts and components of RxJS:

  **1 : Observables**: Observables are the core building blocks of RxJS. 
            They represent a stream of data that can change over time. These data streams can come from various sources, such as user input, HTTP requests, or timer events.

  **2 : Observers:** Observers are entities that subscribe to observables to receive and react to data emitted by the observable. 
            An observer consists of three optional callback functions: 
                next (handles data emissions), 
                error (handles errors), 
                complete (handles the completion of the stream).

  **3 : Operators:** Operators are functions that allow you to manipulate, transform, filter, and combine data streams. 
            RxJS provides a rich set of operators like map, filter, merge, combineLatest, and many more. 
            These operators make it easier to work with and manipulate data streams.

  **4 : Subscription**: A subscription represents the connection between an observer and an observable. 
            It allows the observer to receive data from the observable. 
            Subscriptions can be used to manage resources and unsubscribe when they are no longer needed to prevent memory leaks.

   **5 : Schedulers**: Schedulers are used to control when and how the work associated with observables is executed. 
            They help manage concurrency and can be particularly useful for tasks like delaying, throttling, or running code on specific threads.

   **6 : Subjects**: Subjects are both observables and observers. They can be used to multicast data to multiple subscribers.

There are various types of subjects in RxJS, including Subject, BehaviorSubject, ReplaySubject, and AsyncSubject.

   Here's a simple example of using RxJS to create an observable, subscribe to it, and manipulate its data
     

```import { Observable, from } from 'rxjs';
import { map, filter } from 'rxjs/operators';
const numbersObservable = from([1, 2, 3, 4, 5]);
        numbersObservable
        .pipe(
            filter((num) => num % 2 === 0), // Filter even numbers
            map((num) => num * 2) // Double each number
        )
        .subscribe({
            next: (result) => console.log(result), // Output: 4, 8
            error: (error) => console.error(error),
            complete: () => console.log('Done'),
        });
   ```
        
  In this example, we create an observable from an array of numbers, use the filter and map operators to transform the data, and subscribe to the observable to receive and log the results.
