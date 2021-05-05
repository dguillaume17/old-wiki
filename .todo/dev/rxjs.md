# DEV / RxJS

[_TODO_]

## Fonctions

* of()
* from()
* fromEvent()
* timer()
* iif()
* combineLatest()

## Opérateurs

* pipe()
* tap()
* delay() -> attendre un délais avant d'émettre la valeur émise par la source
* debounce() -> émettre la valeur émise par la source après un  délais, uniquement si la source n'a pas émis une nouvelle valeur entre temps
* map()
* concatMap()
* mergeMap()
* takeUntil()
* filter()

* throttleTime()
* debounceTime()
* repeatWhen()

Both throttleTime and debounceTime ignore the events which come in the meantime, but throttleTime emits right away, while debounceTime waits for additional delay.
