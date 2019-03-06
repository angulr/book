# Valid Name

## Validation Function

```typescript
validName(): ValidatorFn {
        return (control: FormControl): { [key: string]: boolean } | null => {
            if (!control.value) {
                return null;
            }
            let regex = new RegExp('^[a-zA-Z \.\'\-]{1,' + control.value.length + '}$');
            let regex2 = new RegExp('[a-zA-Z]+');
            let isValid = true;
            if (!control.value.match(regex)) {
                // must not have invalid characters
                isValid = false;
            } else if (!control.value.match(regex2)) {
                // must have at least one alphabet character
                isValid = false;
            } else if (control.value.indexOf('.') === 0) {
                // must not start with a period
                isValid = false;
            } else if (control.value.indexOf('.') > 0 && control.value.indexOf('.') !== control.value.lastIndexOf('.')) {
                // must not have more than one period
                isValid = false;
            } else if (control.value.indexOf('\'') === 0) {
                // must not start with apostrophe
                isValid = false;
            } else if (control.value.indexOf('\'') >= 0 && control.value.indexOf('\'') !== control.value.lastIndexOf('\'')) {
                // must not have more than one apostrophe
                isValid = false;
            } else if (control.value.indexOf('-') === 0) {
                // must not start with a dash
                isValid = false;
            } else if (control.value.indexOf('--') !== -1) {
                // must not have two consecutive dashes
                isValid = false;
            } else if (control.value.indexOf(' ') === 0) {
                // must not start with a space
                isValid = false;
            } else if (control.value.indexOf('  ') !== -1) {
                // must not have two consecutive spaces
                isValid = false;
            }
            return isValid ? null : { 'invalidName': true };
        };
    };
}
```

## [View and Download Demo](https://plnkr.co/edit/YH0BPIV9R39iTIzAUOpc?p=preview)

