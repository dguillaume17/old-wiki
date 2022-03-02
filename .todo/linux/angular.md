@ViewChild, @ViewChildren, @ContentChild and @ContentChildren

The difference between @ViewChildren and @ContentChildren is that @ViewChildren look for elements in Shadow DOM while @ContentChildren look for them in Light DOM.


Shadow DOM - is an internal DOM of your component that is defined by you (as a creator of the component) and hidden from an end-user. For example:
@Component({
  selector: 'some-component',
  template: `
    <h1>I am Shadow DOM!</h1>
    <h2>Nice to meet you :)</h2>
    <ng-content></ng-content>
  `;
})
class SomeComponent { /* ... */ }
Light DOM - is a DOM that an end-user of your component supply into your component. For example:
@Component({
  selector: 'another-component',
  directives: [SomeComponent],
  template: `
    <some-component>
      <h1>Hi! I am Light DOM!</h1>
      <h2>So happy to see you!</h2>
    </some-component>
  `
})
class AnotherComponent { /* ... */ }

As the name suggests, @ContentChild and @ContentChildren queries will return directives existing inside the <ng-content></ng-content> element of your view, whereas @ViewChild and @ViewChildren only look at elements that are on your view template directly.