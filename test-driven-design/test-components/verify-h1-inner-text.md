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

{% embed data="{\"url\":\"https://stackblitz.com/edit/angulr-test-component?embed=1&file=src/app/app.component.spec.ts\",\"type\":\"link\",\"title\":\"angulr-test-component - StackBlitz\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"caption\":\"DEMO\"}" %}

  


