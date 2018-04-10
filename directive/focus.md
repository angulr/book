# Focus [Example](https://plnkr.co/edit/uZBhfa2yFiYYV5ftpy3Q?p=preview "Demo Plunker")

### Directive
``` ts
@Directive({
  selector: '[nh-focus]'
})
export class nhFocusDirective implements AfterViewInit, DoCheck {
  private hasFocusBeenSetOnce: boolean = false;
  private initialised: boolean = false;
  constructor(private el: ElementRef) {}

  ngAfterViewInit() {
    this.initialised = true;
    this.ngDoCheck();
  }

  ngDoCheck() {
    if (!this.initialised) { return; }
    const visible = !!this.el.nativeElement.offsetParent;
    if (visible && !this.hasFocusBeenSetOnce) {
      setTimeout(() => {
        this.el.nativeElement.focus();
        this.hasFocusBeenSetOnce = true;
      }, 1);
    }
  }
}
```

### Usages
``` html
<input type="text" placeholder="Focus" nh-focus="true"/>
```

### [View and Download Demo](https://plnkr.co/edit/uZBhfa2yFiYYV5ftpy3Q?p=preview "Demo Plunker")