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



withLatestFrom
race()

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

