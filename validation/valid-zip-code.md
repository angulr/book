# Valid Zip Code [Example](https://plnkr.co/edit/yIxL1dq4fFLkNznAaPUk?p=preview)

### Validation Function
``` ts
 validZipCode(): ValidatorFn {
   return (control: FormControl): { [key: string]: boolean } | null => {
       if (!control.value) {
           return null;
       }
       let zipCodeRegex = /^(?!0{5})(?!0{4})\d{5}$/;
       return control.value.match(zipCodeRegex) ? null : {'validZipCode': true};
   };
 };
```

### [View and Download Demo](https://plnkr.co/edit/yIxL1dq4fFLkNznAaPUk?p=preview)