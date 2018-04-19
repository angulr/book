# Alpha Numeric

## Validation Function

```typescript
  alphaNumeric(allowedPhrase: string): ValidatorFn {
    return (c: FormControl): { [key: string]: boolean } | null => {
      if (c.value) {
        allowedPhrase = allowedPhrase ? allowedPhrase : '';
        let regEx = new RegExp(/^[a-zA-Z0-9]*$/);
        if (!regEx.test(c.value.replace(allowedPhrase.toUpperCase(), '').replace(allowedPhrase.toLowerCase(), ''))) {
          return { 'alphanumeric': true };
        }
      }
      return null;
    };
  };
```

## [View and Download Demo](https://plnkr.co/edit/GNlWc1wXWMjfhjQEL2FN?p=preview)

