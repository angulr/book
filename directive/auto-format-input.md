# Auto Format Input [Example](https://plnkr.co/edit/zSv0p4I3rxqA3uu2JrGN?p=preview "Demo Plunker")





### Directive
``` ts
@Directive({
    selector: '[nhFormatInput]',
    host: {
        '(blur)': 'onBlur()',
    }
})
export class nhFormatInputDirective {
    el: any;
    @Input() nhFormatInput: string;

    static getFormattedValue(type: string, value: string): string {
        let formattedValue: any = {
            'income': AoFormatValue.formatIncome(value),
            'dob': AoFormatValue.formatDate(value),
            'ssn': AoFormatValue.formatSsn(value),
            'capitalize': AoFormatValue.capitalize(value)

        };
        return formattedValue[type];
    }

    constructor(private elementRef: ElementRef,
                private renderer: Renderer,
                private control: NgControl) {
    }

    onBlur() {
        if (this.control.value) {
            let newValue = nhFormatInputDirective.getFormattedValue(this.nhFormatInput, this.control.value);
            this.control.viewToModelUpdate(newValue);
            this.control.valueAccessor.writeValue(newValue);
            this.control.control.setValue(newValue);
        }
    }
}
```


### AoFormatValue Class
``` ts
export class AoFormatValue {
  static acceptableFormats: any[] = [
    /^(\d{2})(\d{2})(\d{4})$/,
    /^(\d{1,2})\/(\d{1,2})\/(\d{4})$/,
    /^(\d{1,2})-(\d{1,2})-(\d{4})$/,
    /^(\d{1,2})\s(\d{1,2})\s(\d{4})$/
  ];
  static formatIncome(val: any): string {
    let amt = val.trim();
    let regex = /^[0-9]{1,3}(?:,?[0-9]{3})*(?:\.[0-9]{1,9})?$/i;

    let valArray = amt.split(',');
    let formattedvalue: any[] = [];

    for (let i = 0; i < valArray.length; i++) {
      formattedvalue += valArray[i];
    }
    amt = formattedvalue;
    if (regex.test(amt)) {
      amt = Math.round(Number(amt.replace(/[,]/g, '')) / 1000) * 1000;
      val = amt < 1000 ? '1,000' : amt.toString().replace(/(\d)(?=(\d{3})+(?!\d))/g, '$1,');
    }
    return val;
  }

  static formatSsn(value: any): string {
    let match = value.match(/^([0-9]{3})-?([0-9]{2})-?([0-9]{4})$/);
    if (match) {
      value = match[1] + '-' + match[2] + '-' + match[3];
    }
    return value;
  }

  static formatDate(value: any): string {

    for (let i = 0; i < AoFormatValue.acceptableFormats.length; i++) {
      let match = value.match(AoFormatValue.acceptableFormats[i]);
      if (match) {
        let yyyy = match[3];
        let mm = match[1];
        let dd = match[2];
        if (this.isValidDate(mm, dd, yyyy)) {

          value = mm + '/' + dd + '/' + yyyy;
        }
      }
    }
    return value;
  }

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

  static capitalize(value: any): string {
    if (value) {
      value = value.toUpperCase();
    }
    return value;
  }
}
```


### Usages
``` html
<form [formGroup]="employmentForm">
  <input type="text" formControlName="price" name="price" placeholder="Format Price" nhFormatInput="income" />
  <br/>
  <input type="text" formControlName="date" name="date" placeholder="Format Date mm/dd/yyyy" nhFormatInput="dob" />
  <br/>
  <input type="text" formControlName="ssn" name="ssn" placeholder="Format Social Security Number" nhFormatInput="ssn" />
  <br/>
  <input type="text" formControlName="cap" name="cap" placeholder="Capitalize" nhFormatInput="capitalize" />
</form>
```

### [View and Download Demo](https://plnkr.co/edit/zSv0p4I3rxqA3uu2JrGN?p=preview "Demo Plunker")



