# Validate Age

## Validation Function

```typescript
  validateDate(minAge: number, maxAge: number, isCustodialMinor: boolean): ValidatorFn {
      return (c: FormControl): { [key: string]: boolean } | null => {
          let value = c.value;
          if (!value) {
              return null;
          }
          let ageError = isCustodialMinor ? 'validMinorAge' : 'validAge';
          for (let i = 0; i < this.acceptableFormats.length; i++) {
              let match = value.match(this.acceptableFormats[i]);
              if (match) {
                  let yyyy = match[3];
                  let mm = match[1];
                  let dd = match[2];
                  if (this.isValidDate(mm, dd, yyyy)) {
                      if (this.isValidAge(mm, dd, yyyy, minAge, maxAge)) {
                          return null;
                      } else {
                          return { 'validAge': true };
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

## Helper Functions

```typescript
 isValidAge(MM: any, DD: any, YYYY: any, minAge: any, maxAge: any) {
     let actualAge = this.calculateAge(MM, DD, YYYY);
     return (actualAge >= minAge && actualAge < maxAge);
 }

 calculateAge(MM: any, DD: any, YYYY: any) {
     let now = new Date();
     let tday = now.getDate();
     let tmo = now.getMonth();
     let tyr = now.getFullYear();
     let age = tyr - YYYY;
     tmo = tmo + 1;
     if (tmo < MM) {
         age--;
     }
     if (MM === tmo && tday < DD) {
         age--;
     }
     return age;
 }

 isValidDate(MM: any, DD: any, YYYY: any): boolean {
     if (MM < 1 || MM > 12) {
         return false;
     }
     let monthLength = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];
     // Adjust for leap years
     if (YYYY % 400 === 0 || (YYYY % 100 !== 0 && YYYY % 4 === 0))                     {
         monthLength[1] = 29;
     }

     // Check the range of the day
     if (DD <= 0 || DD > monthLength[MM - 1]) {
         return false;
     }
     return true;
 }
```

## [View and Download Demo](https://plnkr.co/edit/Kt7gjnizY8CutfWUN3HC?p=preview)

