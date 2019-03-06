# Verify DOM Text

## Test

{% code-tabs %}
{% code-tabs-item title="app.component.spec.ts" %}
```typescript
import { ComponentFixture, TestBed, async, fakeAsync, tick } from '@angular/core/testing';
import { AppComponent } from './app.component';
import { By } from '@angular/platform-browser';

describe('Component: AuthGreeter', () => {
  let fixture, greeter, element;

  //setup
  beforeEach(() => {
    TestBed.configureTestingModule({
      declarations: [AppComponent],
    });

    fixture = TestBed.createComponent(AppComponent);
    greeter = fixture.componentInstance;
    element = fixture.nativeElement;
  });

  //specs
  it('should render `Hello Superman!` (async)', async(() => {
    //trigger change detection
    fixture.detectChanges();
    fixture.whenStable().then(() => {
      expect(element.querySelector('h1').innerText).toBe('Hello Superman!');
    });
  }));
}) 

```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Implementation

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>Hello {{ name }}!</h1>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})

export class AppComponent {
  name = 'Superman';
  message: string = '';
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





