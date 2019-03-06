# Custom Rx Blink Component

## Blink Component

{% code-tabs %}
{% code-tabs-item title="blink.component.ts" %}
```typescript
import { Component, OnInit,Input, OnDestroy, HostBinding } from '@angular/core';
import { Observable } from 'rxjs';
import 'rxjs/add/observable/timer';
import 'rxjs/add/observable/merge';
import 'rxjs/add/operator/takeWhile';
import 'rxjs/add/operator/mapTo';

@Component({
  selector: 'blink',
  template: `<ng-content></ng-content>`
})
export class BlinkComponent implements OnInit, OnDestroy {
  private blinker$: Observable<string>;

  @Input() active: boolean = true;
  @Input() visibleMS: number = 0;
  @Input() inVisibleMS: number = 200;
  @Input() totalMS: number = 400;

  @HostBinding('style.visibility')
  private visibility: string;

  constructor() {
    // Visible for 750 ms and then invisible for 250 ms, for a total period of 1 second.
    const show$ = Observable.timer(this.visibleMS, this.totalMS);
    const hide$ = Observable.timer(this.inVisibleMS, this.totalMS);

    this.blinker$ = Observable.merge(
      show$.mapTo('visible'),
      hide$.mapTo('hidden')
    );
  }

  ngOnInit() {
    this.blinker$
      .takeWhile(() => this.active)
      .subscribe((newVisiblity: string) => this.visibility = newVisiblity);
  }

  ngOnDestroy() {
    this.active = false;
  }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Using Blink Component

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```typescript
<hello name="{{ name }}"></hello>
<p>
  <blink [active]="true">Start editing to see some magic happen :)</blink>
</p>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## [View and Download Demo](https://stackblitz.com/edit/blink)

