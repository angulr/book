# Validate Date

## Validation Function

```typescript
  validateDate(): ValidatorFn {
      return (c: FormControl): { [key: string]: boolean } | null => {
          let value = c.value;
          if (!value) {
              return null;
          }
          for (let i = 0; i < HnFormatValue.acceptableFormats.length; i++) {
              let match = value.match(HnFormatValue.acceptableFormats[i]);
              if (match) {
                  let yyyy: string = match[3];
                  let mm: string = match[1];
                  let dd: string = match[2];
                  if (HnFormatValue.isValidDate(Number(mm), Number(dd), Number(yyyy))) {
                      let givenDate: Date = new Date(Number(yyyy), Number(mm) - 1, Number(dd));
                      let today: Date = new Date();
                      let minDate: Date = new Date(1800, 0, 1);
                      if (yyyy && yyyy.length === 4 && yyyy.charAt(0) === '0') {
                          return { 'validDate': true };
                      } else if (givenDate < minDate || givenDate > today) {
                          return { 'validDate': true };
                      } else {
                          return null;
                      }
                  } else {
                      return { 'validDate': true };
                  }
              }
          }
          return { 'validDate': true };
      };
  };
```

## Helper Functions isValidDate and acceptableFormats

```typescript
export class HnFormatValue {
  static acceptableFormats: any[] = [
    /^(\d{2})(\d{2})(\d{4})$/,
    /^(\d{1,2})\/(\d{1,2})\/(\d{4})$/,
    /^(\d{1,2})-(\d{1,2})-(\d{4})$/,
    /^(\d{1,2})\s(\d{1,2})\s(\d{4})$/
  ];

  static isValidDate(MM: any, DD: any, YYYY: any): boolean {
    if (MM < 1 || MM > 12) {
      return false;
    }
    let monthLength = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];

    // Adjust for leap years
    if (YYYY % 400 === 0 || (YYYY % 100 !== 0 && YYYY % 4 === 0)) {
      monthLength[1] = 29;
    }

    // Check the range of the day
    if (DD <= 0 || DD > monthLength[MM - 1]) {
      return false;
    }
    return true;
  }
}
```

## [View and Download Demo](https://plnkr.co/edit/W8p5YP49SEcLzGPM6a25?p=preview)

