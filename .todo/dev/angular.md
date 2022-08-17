Service Location
    this._location.path().split('/');

On peut injecter une directive dans le constructeur d'un composant

Comment résoudre un problème de dépendance circulaire ("Circular dependency in DI detected") à l'injection du NgControl?

    // Ne fonctionne pas

    constructor(
        private _ngControl: NgControl
    ) {}

    // Fonctionne

    private _ngControl: NgControl;

    constructor(
        private _injector: Injector
    ) {}

    public ngOnInit() {
        this._ngControl = this._injector.get(NgControl);
    }

Comment injecter Renderer2 dans un service?

    import { Injectable, RendererFactory2 } from '@angular/core';

    @Injectable({
        providedIn: 'root'
    })
    export class UserActivityManagerService {

        // Lifecycle

        constructor(private rendererFactory2: RendererFactory2) {
            const renderer = this.rendererFactory2.createRenderer(null, null);
        }
    }

Comment injecter un ViewContainerRef?

    @Directive({ selector: '[componentToInject]' })
    export class ComponentToInjectDirective implements OnChanges {

        // Implicit inputs

        @Input()
        public componentToInject: boolean;

        // Private properties

        private _isComponentAlreadyInjected: boolean;

        // Lifecycle

        constructor(
            @Self()
            private _template: TemplateRef<any>,
            private _vcr: ViewContainerRef
        ) { }

        ngOnChanges(changes: SimpleChanges) {
            if (!this._isComponentAlreadyInjected && changes.componentToInject.currentValue === true) {
                this._vcr.createEmbeddedView(this._template);
                this._isComponentAlreadyInjected = true;
            }
        }

    }

Read Token in ContentChild

    https://www.tektutorialshub.com/angular/contentchild-and-contentchildren-in-angular/


    
    For Example, consider the following projected content. The nameInput can be either a input element or a ngModel directive.
        <input #nameInput [(ngModel)]="name">

    @ContentChild('nameInput',{static:false}) nameVar; // Default read is ElementRef
    @ContentChild('nameInput',{static:false, read: NgModel}) nameVarAsNgModel;
    @ContentChild('nameInput',{static:false, read: ElementRef}) nameVarAsElementRef;
    @ContentChild('nameInput', {static:false, read: ViewContainerRef }) nameVarAsViewContainerRef;
 
 
