# Mymodule 

[Repository: github.com/vovs03/mymodule](https://github.com/vovs03/mymodule)

Lesson 3

## Practic

- `go mod init github.com/<myname></myname>/mymodule` 
  - > инициализация модуля
- `go mod tidy`
  - > Обновление зависимостей модуля
- `go list -mod=mod -m all`
  - > Просмотр всех зависимостей

### Граф зависимостей

> `go mod graph`

```terminal
mymodule [master] % go mod graph
github.com/vovs03/mymodule github.com/gorilla/websocket@v1.4.2
github.com/vovs03/mymodule github.com/valyala/fasthttp@v1.25.0
github.com/valyala/fasthttp@v1.25.0 github.com/andybalholm/brotli@v1.0.2
github.com/valyala/fasthttp@v1.25.0 github.com/klauspost/compress@v1.12.2
github.com/valyala/fasthttp@v1.25.0 github.com/valyala/bytebufferpool@v1.0.0
github.com/valyala/fasthttp@v1.25.0 github.com/valyala/tcplisten@v1.0.0
github.com/valyala/fasthttp@v1.25.0 golang.org/x/crypto@v0.0.0-20210513164829-c07d793c2f9a
github.com/valyala/fasthttp@v1.25.0 golang.org/x/net@v0.0.0-20210510120150-4163338589ed
github.com/valyala/fasthttp@v1.25.0 golang.org/x/sys@v0.0.0-20210514084401-e8d321eab015
github.com/klauspost/compress@v1.12.2 github.com/golang/snappy@v0.0.3
golang.org/x/crypto@v0.0.0-20210513164829-c07d793c2f9a golang.org/x/net@v0.0.0-20210226172049-e18ecbb05110
golang.org/x/crypto@v0.0.0-20210513164829-c07d793c2f9a golang.org/x/sys@v0.0.0-20201119102817-f84b799fce68
golang.org/x/crypto@v0.0.0-20210513164829-c07d793c2f9a golang.org/x/term@v0.0.0-20201126162022-7de9c90e9dd1
golang.org/x/crypto@v0.0.0-20210513164829-c07d793c2f9a golang.org/x/text@v0.3.3
golang.org/x/net@v0.0.0-20210510120150-4163338589ed golang.org/x/sys@v0.0.0-20210423082822-04245dca01da
golang.org/x/net@v0.0.0-20210510120150-4163338589ed golang.org/x/term@v0.0.0-20201126162022-7de9c90e9dd1
golang.org/x/net@v0.0.0-20210510120150-4163338589ed golang.org/x/text@v0.3.6
golang.org/x/net@v0.0.0-20210226172049-e18ecbb05110 golang.org/x/sys@v0.0.0-20201119102817-f84b799fce68
golang.org/x/net@v0.0.0-20210226172049-e18ecbb05110 golang.org/x/term@v0.0.0-20201126162022-7de9c90e9dd1
golang.org/x/net@v0.0.0-20210226172049-e18ecbb05110 golang.org/x/text@v0.3.3
golang.org/x/term@v0.0.0-20201126162022-7de9c90e9dd1 golang.org/x/sys@v0.0.0-20201119102817-f84b799fce68
golang.org/x/text@v0.3.3 golang.org/x/tools@v0.0.0-20180917221912-90fa682c2a6e
golang.org/x/text@v0.3.6 golang.org/x/tools@v0.0.0-20180917221912-90fa682c2a6e
```

### Проверка ветви графа

- `go mod why -m github.com/andybalholm/brotli`
  - > Проверить ветвь графа до конкретного модуля можно, использовав команду why:

```terminal
mymodule [master●] % go mod why -m github.com/andybalholm/brotli
# github.com/andybalholm/brotli
github.com/vovs03/mymodule
github.com/valyala/fasthttp
github.com/andybalholm/brotli
```

### Дерево зависимостей - графический вид

Для создания визуального графа зависимостей была использована утилита [modv](https://github.com/poloxue/modv)

#### :green_apple: MacOS

- [x] `go mod graph | modv | dot -T png | open -f -a /Applications/Preview.app`

> Результат

![open_jZiU972F](https://user-images.githubusercontent.com/21124057/120212281-731b6900-c23a-11eb-8d84-65b1dbf7a11a.jpg)
