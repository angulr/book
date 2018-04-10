# Test HTTP in Service Without MockBackend [Example](https://plnkr.co/edit/nD13QzlTovkZCqH1iR0s?p=preview)

### Test

``` ts
import {
  fakeAsync,
  inject,
  TestBed,
  tick
} from '@angular/core/testing';
import {
  Http,
  ResponseOptions,
  Response,
  RequestMethod
} from '@angular/http';
import {
  MockBackend,
  MockConnection
} from '@angular/http/testing';
import { Observable } from 'rxjs/Observable';
import 'rxjs/add/observable/of';
import {QuoteService} from './quote.service';

const mockResponse = [{
  "title": "Man",
  "pageid": 15822899
}];

describe('Search service', () => {
  let mockHttp: Http;
  beforeEach(() => {
    // new mockHttp
    mockHttp = { get: null } as Http;

    spyOn(mockHttp, 'get').and.returnValue(Observable.of({
      json: () => mockResponse
    }));
    
    TestBed.configureTestingModule({
      providers: [
        {
          provide: Http,
          useValue: mockHttp // Should be useValue instead of useClass
        },
        QuoteService
      ]
    });
  });
   
  it('should get search results', fakeAsync(
    inject([QuoteService], QuoteService => {
      const expectedUrl = 'src/data.json';
      QuoteService.search('data')
        .subscribe(res => {      
          expect(mockHttp.get).toHaveBeenCalledWith(expectedUrl);
          expect(res).toEqual(mockResponse);
        });
    })
  ));
});
```

### Implementation

``` ts
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


### [View and Download Demo](https://plnkr.co/edit/nD13QzlTovkZCqH1iR0s?p=preview)

