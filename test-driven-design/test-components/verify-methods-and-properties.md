# Verify Methods and Properties

## Test

```typescript
import {MessageComponent} from './message.component';

describe('Testing message state in message.component', () => {
  let app: MessageComponent;

  beforeEach(() => {
    app = new MessageComponent();
  });

  it('should set new message', () => {
    app.setMessage('Testing');
    expect(app.message).toBe('Testing');
  });

  it('should clear message', () => {
    app.clearMessage();
    expect(app.message).toBe('');
  });
});
```

## Implementation

```typescript
import {Component} from '@angular/core';

@Component({
  selector: 'display-message',
  template: '<h1>{{message}}</h1>'
})

export class MessageComponent {
  public message: string = '';

  constructor() {}

  setMessage(newMessage: string) {
      this.message = newMessage;
  }

  clearMessage() {
    this.message = '';
  }
}
```

## [View and Download Demo](https://plnkr.co/edit/5bRWPGmjMgRZIlVXQn5d?p=preview)

