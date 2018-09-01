# Blink with CSS

## CSS Style for Blink

{% code-tabs %}
{% code-tabs-item title="app.component.css" %}
```css
.blinking{
    animation:blinkingText 0.3s;
}

@keyframes blinkingText{
    0%{     color: #000;    }
    49%{    color: transparent; }
    50%{    color: transparent; }
    99%{    color:transparent;  }
    100%{   color: #000;    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Using NgClass

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<p [ngClass]="{'blinking':blink}">
  Blink with CSS
</p>
<button (click)="blinkMe()">Blink</button>

```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Click Event to activate Blink

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: [ './app.component.css' ]
})
export class AppComponent  {
  name = 'Angular';
  blink = false;

  blinkMe(){
    this.blink = true;
    setTimeout(function(){
      this.blink = false;
    }.bind(this)
    ,300)
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

In the above function `blinkMe`  we have to `bind(this)`  because if the enclosing function is a function\(\) and not an arrow function, we are updating a different `this` . Arrow functions does not have `this`, however, an arrow function can access `this` from the enclosed function.  

## [View and Download Demo](https://stackblitz.com/edit/blink-css)

