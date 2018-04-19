# Test HTTP in Service Using MockBackend

## Test

```typescript
import {
  fakeAsync,
  inject,
  TestBed,
  tick
} from '@angular/core/testing';
import {
  HttpModule,
  XHRBackend,
  ResponseOptions,
  Response,
  RequestMethod
} from '@angular/http';
import {
  MockBackend,
  MockConnection
} from '@angular/http/testing';

import {QuoteService} from './quote.service';

const mockResponse = [{
  "title": "Man",
  "pageid": 15822899
}];

describe('Search service', () => {

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [HttpModule],
      providers: [
        {
          provide: XHRBackend,
          useClass: MockBackend
        },
        QuoteService
      ]
    });
  });

  it('should get search results', fakeAsync(
    inject([
      XHRBackend,
      QuoteService
    ], (mockBackend: XHRBackend, QuoteService: QuoteService) => {

      const expectedUrl = 'src/data.json';

      mockBackend.connections.subscribe(
        (connection: MockConnection) => {
          expect(connection.request.method).toBe(RequestMethod.Get);
          expect(connection.request.url).toBe(expectedUrl);

          connection.mockRespond(new Response(
            new ResponseOptions({ body: mockResponse })
          ));
        });

      QuoteService.search('data')
        .subscribe(res => {
          console.log(res)
          expect(res).toEqual(mockResponse);
        });
    })
  ));

  it('should set foo with a 1s delay', fakeAsync(
    inject([QuoteService], (quoteService: QuoteService) => {
      quoteService.setFoo('food');
      tick(1000);
      expect(quoteService.foo).toEqual('food');
    })
  ));

});
```

## Implementation

```typescript
import {Http} from '@angular/http';
import {Injectable, Inject} from '@angular/core';
import {Observable} from 'rxjs';
import 'rxjs/add/operator/map'

@Injectable()
export class QuoteService {
  constructor (private http: Http) {}

  search(term: string): Observable<any> {
    return this.http.get('src/'+ term+ '.json').map((response) => response.json());
  }

  setFoo(value: string): void {
    return setTimeout(() => {
      this.foo = value;
    }, 1000);
  }
}
```

> To Test **JSONP **and **XHR Back-Ends **we can use `MockBrowserJsonp` and `XHRBackend` respectively.

## [View and Download Demo](https://plnkr.co/edit/Lzoqt1WYIr5y5Bz1Pyqa?p=preview)

