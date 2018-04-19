# Tracking Pipe

## Tracking Pipe

```typescript
import { ChangeDetectorRef, NgZone, Pipe } from '@angular/core';
import{ TrackingService } from './tracking.service';

@Pipe({name: 'track', pure: true})
export class TrackingPipe {
   constructor(
       private trackingService: TrackingService,
       private changeDetector: ChangeDetectorRef,
       private zone: NgZone,
   ) {
   }

   transform(value: string): string {
       Promise.resolve().then(() => {
        this.trackingService.addWordUsed(value);
        this.zone.run(() => this.changeDetector.markForCheck()); 
       });
       return value;
   }
}
```

## Tracking Service

```typescript
import {Injectable} from '@angular/core';

@Injectable()
export class TrackingService {
  private wordsUsed: Set<string> = new Set<string>();

  public addWordUsed(word: string) {
    this.wordsUsed.add(word);
  }

  public getWords(): string[] {
    return Array.from(this.wordsUsed);
  }
}
```

## [View and Download Demo](https://plnkr.co/edit/TkQR0SfAQqJ4MlHlswSe?p=preview)

