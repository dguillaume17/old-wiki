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
