# Testing Pipe

## Test

{% code-tabs %}
{% code-tabs-item title="strength.pipe.spec.ts" %}
```typescript
import { StrengthPipe } from './strength.pipe';

describe('🢂 StrengthPipe', ()=>{
  it('➜  should display weak if strength is 5', () => {
    let pipe = new StrengthPipe()
    expect(pipe.transform(5)).toEqual('5 (weak)');
  })

  it('➜  should display weak if strength is 10', () => {
    let pipe = new StrengthPipe()
    expect(pipe.transform(10)).toEqual('10 (strong)');
  })
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Implementation

{% code-tabs %}
{% code-tabs-item title="strength.pipe.ts" %}
```typescript
import { Pipe, PipeTransform } from '@angular/core';
@Pipe({
  name: 'strength'
})
export class StrengthPipe implements PipeTransform {
  transform(value: number): string {
    if(value < 10) {
      return value + " (weak)";
    } else if(value >= 10 && value < 20) {
      return value + " (strong)";
    } else {
      return value + " (unbelievable)";
    }
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

## All Test Preview

{% embed url="https://stackblitz.com/edit/angulr-test?embed=1&view=preview" %}







