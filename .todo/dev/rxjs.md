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
throttleTime -> Emit first value then ignore for specified duration


withLatestFrom
race() -> The observable to emit first is used.

mergeMap vs switchMap
    import { interval, take, tap, timer } from 'rxjs';
    import { mergeMap } from 'rxjs/operators';

    interval(1000)
    .pipe(
        take(2),
        tap(() => console.log('tap source')),
        mergeMap(() => {
        return timer(3000).pipe(tap(() => console.log('tap mergeMap')));
        })
    )
    .subscribe(() => {
        console.log('subscribe');
    });


    import { interval, take, tap, timer } from 'rxjs';
    import { switchMap } from 'rxjs/operators';

    interval(1000)
    .pipe(
        take(2),
        tap(() => console.log('tap source')),
        switchMap(() => {
        return timer(3000).pipe(tap(() => console.log('tap switchMap')));
        })
    )
    .subscribe(() => {
        console.log('subscribe');
    });

Comment faire en sorte que le debounceTime ne fonctionne qu'à partir de la 2e valeur émise?
    concat(
        this._pollingRefreshNowSource.pipe(take(1)),
        this._pollingRefreshNowSource.pipe(debounceTime(5000), take(1))
    ).pipe(
        repeat(),
        untilDestroyed(this)
    ).subscribe(() => {
        ...
    });

Comment transormer chaque item d'un tableau en observable et concaténer le tout dans un tableau sous forme d'observable ?

    return from(breakTicketsDto).pipe(
            concatMap(breakTicketModel => {
                return this.decollapseConversationListSection(breakTicketModel).pipe(
                    delay(1000)
                );
            }),
            toArray(),
            mapTo(null)
        );

from vs of

    from([1, 2, 3]) -> Emet 3 valeurs
        1 -> 1
        2 -> 2
        3 -> 3
    of([1, 2, 3]); -> Emet une valeur = [1, 2, 3]

Comment émettre une valeur par défaut?

    Opérateur startWith