# Simple Service

## Test

{% code-tabs %}
{% code-tabs-item title="message.service.spec.ts" %}
```typescript
import { MessageService } from './message.service';

describe('🢂 MessageService', () => {
  let service: MessageService

  beforeEach(() => {
    
  })

  it('➜  should have no messages to start', () => {
    service = new MessageService
    
    expect(service.messages.length).toBe(0);
  })

  it('➜  should add a message when add is called', () => {
    service = new MessageService
    
    service.add('message1');

    expect(service.messages.length).toBe(1);
  })

  it('➜  should add a message when add is called', () => {
    service = new MessageService
    service.add('message1');

    service.clear()

    expect(service.messages.length).toBe(0);
  })
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Implementation

{% code-tabs %}
{% code-tabs-item title="message.service.ts" %}
```typescript
import { Injectable } from '@angular/core';

@Injectable()
export class MessageService {
  messages: string[] = [];

  add(message: string) {
    this.messages.push(message);
  }

  clear() {
    this.messages = [];
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## All Test Preview

{% embed url="https://stackblitz.com/edit/angulr-test?embed=1&view=preview" %}



