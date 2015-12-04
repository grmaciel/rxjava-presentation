# RxJava 
* Implementação na JVM do Reactive X

### Introdução
* Android data load / AsynTask
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
```
service.getSharePerformance(matchId)
                .map(extractImageUrl())
                .flatMap(downloadImage())
```

```
private Func1<DTO, String> extractUrl() {
        return new Func1<DTO, String>() {
            @Override
            public String call(DTO dto) {
                return dto.url;
            }
        };
    }
```

```
private Func1<String, Observable<Bitmap>> downloadImage() {
        return new Func1<String, Observable<Bitmap>>() {
            @Override
            public Observable<Bitmap> call(String path) {
                try {
                    return Observable.just(Picasso.with(context)
                            .load(path)
                            .get());
                } catch (IOException e) {
                    return Observable.error(e);
                }
            }
        };
    }
```
```
summonerDataRetrievalEvents
            .subscribeOn(Schedulers.io())
            .filter(new IsSummonerPresent())
            .map(new ExtractSummoerInfo())
            .map(new ExtractSummonerRegion())
            .map(new CheckIsCacheValid())
            .flatMap(new RegionToMessagesRequestObservable());
```



### Fontes
http://www.google.com
