# Prohibited Word

## Validation Function

```typescript
  prohibitedWord(): ValidatorFn {
    return (c: FormControl): { [key: string]: boolean } | null => {
      if (c.value) {
        let regEx = new RegExp(/^.*\b(prone)\b.*?$/i);
        if (regEx.test(c.value) {
          return { 'prohibitedWord': true };
        }
      }
      return null;
    };
  };
```

## [View and Download Demo](https://plnkr.co/edit/sk3zRWvmpAeATHtpoJj6?p=preview)

