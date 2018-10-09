# Verify Methods and Properties

## Test

{% code-tabs %}
{% code-tabs-item title="verify-methods-and-properties.component.spec.ts" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

## Implementation

{% code-tabs %}
{% code-tabs-item title="verify-methods-and-properties.component.ts" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

## All Test Preview

{% embed url="https://stackblitz.com/edit/angulr-test?embed=1&view=preview" %}



