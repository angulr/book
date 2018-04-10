# Asynchronous Action [Example](https://plnkr.co/edit/iXkHYNOeEoewGS4OXWbm?p=preview)

### Test

``` ts
import { QuoteService } from './quote.service';
import { App } from './app';
import { provide } from '@angular/core';
import {
  async,
  inject,
  TestBed,
  fakeAsync,
  tick
} from '@angular/core/testing';

class MockQuoteService {
  public quote: string = 'Test quote';

  getQuote() {
    return Promise.resolve(this.quote);
  }
}

describe('Testing Quote Component', () => {

  let fixture;

  beforeEach(() => {
    TestBed.configureTestingModule({
      declarations: [
        App
      ],
      providers: [
        { provide: QuoteService, useClass: MockQuoteService }
      ]
    });
    fixture = TestBed.createComponent(App);
    fixture.detectChanges();
  });

  it('Should get quote', fakeAsync(() => {
    fixture.componentInstance.getQuote();
    tick();
    fixture.detectChanges();
    const compiled = fixture.debugElement.nativeElement;
    expect(compiled.querySelector('.class').innerText).toEqual('Test quote');
  })));
});
```

### Component

``` ts
import { Component } from '@angular/core';
import { QuoteService } from './quote.service';

@Component({
  selector: 'my-quote',
  template: '<h3>Random Quote</h3> <div>{{quote}}</div>'
})

export class QuoteComponent {
  quote: string;

  constructor(private quoteService: QuoteService){};

  getQuote() {
    this.quoteService.getQuote().then((quote) => {
      this.quote = quote;
    });
  };
}
```

### Service

``` ts
export class QuoteService {
  public quote: 'Test quote';

  getQuote() {
    return new Promise<string>((resolve, reject) => {
      resolve(this.quote);
    });
  }
}
```

### [View and Download Demo](https://plnkr.co/edit/iXkHYNOeEoewGS4OXWbm?p=preview)
