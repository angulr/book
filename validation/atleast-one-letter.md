# Atleast One Letter

## Validation Function

```typescript
 validAtleastoneletter(): ValidatorFn {
     return (control: FormControl): { [key: string]: boolean } | null => {
         if (!control.value) {
             return null;
         }
         return /[a-zA-Z]/.test(control.value) ? null : {'atleastoneletter': true};
     };
 };
```

## [View and Download Demo](https://plnkr.co/edit/W2G2JXMEjGBNy9oAMUT0?p=preview)

