# Mocking to Isolate Code

## Isolate Component Code

{% code-tabs %}
{% code-tabs-item title="heroes.component.ts" %}
```typescript
  getHeroes(): void {
    this.heroService.getHeroes()
    .subscribe(heroes => this.heroes = heroes);
  }

  add(name: string): void {
    name = name.trim();
    var strength = 11
    if (!name) { return; }
    this.heroService.addHero({ name, strength } as Hero)
      .subscribe(hero => {
        this.heroes.push(hero);
      });
  }

  delete(hero: Hero): void {
    this.heroes = this.heroes.filter(h => h !== hero);
    this.heroService.deleteHero(hero).subscribe();
  }
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Test for Above Isolated Code

{% code-tabs %}
{% code-tabs-item title="heroes.component.spec.ts" %}
```typescript
import { HeroesComponent } from "./heroes.component";
import { of } from "rxjs";

describe('HeroesComponent', () => {
  let component: HeroesComponent;
  let HEROES;
  let mockHeroService;

  beforeEach(() => {
    HEROES = [
      {id:1, name: 'SpiderDude', strength: 8},
      {id:2, name: 'Wonderful Woman', strength: 24},
      {id:3, name: 'SuperDude', strength: 55}
    ]

    mockHeroService = jasmine.createSpyObj(['getHeroes', 'addHero', 'deleteHero'])

    component = new HeroesComponent(mockHeroService);
  })

  describe('delete', () => {

    it('should remove the indicated hero from the heroes list', () => {
      mockHeroService.deleteHero.and.returnValue(of(true))
      component.heroes = HEROES;

      component.delete(HEROES[2]);

      expect(component.heroes.length).toBe(2);
    })

    it('should call deleteHero', () => {
      mockHeroService.deleteHero.and.returnValue(of(true))
      component.heroes = HEROES;

      component.delete(HEROES[2]);

      expect(mockHeroService.deleteHero).toHaveBeenCalledWith(HEROES[2]);
    })
  })
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

