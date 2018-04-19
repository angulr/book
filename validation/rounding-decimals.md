# Rounding Decimals

## Validation Function

```typescript
  roundingDecimals(maxNumber: number): ValidatorFn {
      return (c: FormControl): { [key: string]: boolean } | null => {
          let value = c.value;
    if (!value) {
      return null;
    }
    let valArray = value.toString().split(',');
    let formattedvalue: any = [];
    let regex = /^[0-9]{1,3}(?:,?[0-9]{3})*(?:\.[0-9]{1,9})?$/i;
    for (let i = 0; i < valArray.length; i++) {
      formattedvalue += valArray[i];
    }
    value = formattedvalue;
    if (!regex.test(value)) {
      return {'decimalnumber': true};
    } else if (value > maxNumber) {
      return {'maxnumber': true};
    } else {
      return null;
    }
      };
  };
```

## [View and Download Demo](https://plnkr.co/edit/dYzICF32iYCbEuJIYkR2?p=preview)

