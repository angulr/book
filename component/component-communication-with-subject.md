# Component Communication with Subject [Example](https://plnkr.co/edit/6DN45y?p=preview)


### Observable.subscribe()
The observable subscribe method is used to subscribe to messages that are sent to an observable.

### Subject.next()
The subject next method is used to send messages to an observable which are then sent to all subscribers of that observable.

### Message Service
``` ts
import { Injectable } from '@angular/core';
import { Observable } from 'rxjs';
import { Subject } from 'rxjs/Subject';
 
@Injectable()
export class MessageService {
    private subject = new Subject<any>();
 
    sendMessage(message: string) {
        this.subject.next({ text: message });
    }
 
    clearMessage() {
        this.subject.next();
    }
 
    getMessage(): Observable<any> {
        return this.subject.asObservable();
    }
}
```

### App Component

```
import {Component, OnDestroy} from '@angular/core'
import { Subscription } from 'rxjs/Subscription';
import { MessageService } from './message.service';
import { HomeComponent } from './home.component';


@Component({
  selector: 'my-app',
  template: `
    <div *ngIf="message" class="alert alert-success">
      {{message.text}}
    </div>
    <home></home>
  `,
})
export class App implements OnDestroy{
  message: any;
  subscription: Subscription;

  name:string;
  constructor(private messageService: MessageService) {
    this.name = `Angular! v${VERSION.full}`
    this.subscription = this.messageService.getMessage()
      .subscribe(message => { 
        this.message = message; 
      });
  }
  
  ngOnDestroy() {
    // unsubscribe to ensure no memory leaks
    this.subscription.unsubscribe();
  }
}
```

### Home Component

``` ts
import { Component } from '@angular/core';
import { MessageService } from './message.service';

@Component({
    selector: 'home',
    template : `
    <div class="col-md-6 col-md-offset-3">
      <h1>Home</h1>
      <button (click)="sendMessage()">Send Message</button>
      <button (click)="clearMessage()">Clear Message</button>
    </div>
    `
})
 
export class HomeComponent {
    constructor(private messageService: MessageService) {}
    
    sendMessage(): void {
        // send message to subscribers via observable subject
        this.messageService.sendMessage('Message from Home Component to App Component!');
    }

    clearMessage(): void {
        // clear message
        this.messageService.clearMessage();
    }
}
```


### [View and Download Demo](https://plnkr.co/edit/6DN45y?p=preview)