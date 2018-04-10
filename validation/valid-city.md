# Valid Duplicates [Example](https://plnkr.co/edit/cndyKcgxfXFnQKbexWbl?p=preview)

### Validation Function
``` ts
  validDuplicates(list: any): ValidatorFn {
    return (c: FormControl): {[key: string]: boolean} | null => {
      if (list && c.value) {
        for (let i = 0; i < list.length; i++) {
          if (list[i].toUpperCase() === c.value.toUpperCase()) {
            return {'validDuplicates': true};
          }
        }
      }
      return null;
    };
  };
```

### [View and Download Demo](https://plnkr.co/edit/cndyKcgxfXFnQKbexWbl?p=preview)