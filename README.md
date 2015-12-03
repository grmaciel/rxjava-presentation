# RxJava 
* Implementação na JVM do Reactive X

### Introdução
* Fluxo normal, você busca os dados
* RXJava, ele te envia os dados
* Iterable vs Observables
* Observer pattern que tomo bomba, adicionando 2 eventos
* Foco em operações assíncronas
* Massa de dados

|        | Single   | Multiple |
| -------|-------------| ------------- |
| Sync   | ```T getData()``` | ```Iterable <T> getData()```
| Async  | ```Future<T> getData()```  | ```Observable<T> getData()```

### Observable
```
Observable<T>
- onNext(T)
- onError(Exception)
- onCompleted()
```

### Subscriber
```
Subscriber<T> mySubscriber = new Subscriber<T>() {
            @Override
            public void onCompleted() {
            }

            @Override
            public void onError(Throwable e) {
            }

            @Override
            public void onNext(T result) {
            }
        };
```

### Thread
```
.subscribeOn(Schedulers.newThread())
.subscribeOn(Schedulers.io())
.observeOn(AndroidSchedulers.mainThread());
```

### Operadores




### Fontes
http://www.google.com
