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



{% embed data="{\"url\":\"https://stackblitz.com/edit/angulr-test-component?embed=1&file=src/app/verify-methods-and-properties.component.spec.ts\",\"type\":\"link\",\"title\":\"angulr-test-component - StackBlitz\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"caption\":\"DEMO\"}" %}

