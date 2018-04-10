# WindowRefService [Example](https://plnkr.co/edit/tKWYo5ua3NMMhnko8Eca?p=preview)
The window object represents an open window in a browser. It has several useful Browser Property like `closed`, `localStorage`, `location`, etc.

In AngularJS 1 we had `$window` mainly used for mocking  unit tests. But in Angular 2+ we don't have any such services so I have created a simple window service...

### Window Service
``` ts
import { Injectable } from '@angular/core';
function _window(): any {
  // return the global native browser window object
  return window;
}
@Injectable()
export class WindowRefService {
  get nativeWindow(): any {
    return _window();
  }
}
```

### [View and Download Demo](https://plnkr.co/edit/tKWYo5ua3NMMhnko8Eca?p=preview)