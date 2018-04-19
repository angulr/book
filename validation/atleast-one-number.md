# Atleast One Number

## Validation Function

```typescript
 validAtleastonenumber(): ValidatorFn {
     return (control: FormControl): { [key: string]: boolean } | null => {
         if (!control.value) {
             return null;
         }
         return /[0-9]/.test(control.value) ? null : {'atleastonenumber': true};
     };
 };
```

## [View and Download Demo](https://plnkr.co/edit/lsM5U95lDDsdUaSgu5E3?p=preview)

