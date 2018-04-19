# Default Pipe

## DefaultPipe

```typescript
import { Pipe } from '@angular/core';

@Pipe({name: 'default', pure: true})
export class DefaultPipe {
   transform(value: any, defaultValue: any): any {
       return value || defaultValue;
   }
}
```

## [View and Download Demo](https://plnkr.co/edit/BUP3HRHOBsgsAbDVJ4pG?p=preview)

