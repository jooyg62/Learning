go module refrence 내용을 정리합니다. ( https://go.dev/ref/mod )

Go 의존성을 관리하는 시스템으로써 Go Modules system 에 대해 알아보려합니다.

모듈은 배포된 패키지들의 모음집이고, 1) 저장소나 2) 모듈 프록시 서버로부터 다운로드 받을 수 있습니다.

모듈은 "golang.org/x/net" 와 같이 경로로 구분이 되는데 이 내용은 각종 의존성을 포함하여 go.mod 파일에 기록되어 있습니다.

아래의 명령어를 통해 의존성을 관리하기 위한 go.mod 파일을 생성합니다.

init 뒤 인자에는 자신의 워크스페이스에 해당하는 임의의 제목을 입력하여줍니다.

# go.mod 파일 초기화
go mod init {my module name}

go.mod 파일이 생성되었고, go.mod 파일이 있는 폴더가 module 의 루트 폴더입니다.

main 모듈은 go 명령어로부터 호출되어진 폴더를 포함하는 모듈입니다.

go get 명령어를 통해 pkg 를 다운받습니다.

# pkg 다운로드
go get github.com/jooyg62/keyboard

go.mod 파일내 의존성 패키지가 추가된 내용을 확인하실 수 있습니다.

삽질 1) 처음 go.mod 파일을 생성할때, 내가 다운받으려는 모듈명(`github.com/jooyg62/keyboard`)으로 명명하여 패키지가 다운로드(`go get`) 되지 않는 이슈가 있었다.
아마 자기 자신의 패키지를 참조하기 때문인 이유인 것 같고, 아래와 같이 무한 사이클로 모듈이 import 된다는 error 을 받았던 것이였다..
```
package command-line-arguments
        imports github.com/jooyg62/keyboard/detail
        imports github.com/jooyg62/keyboard/detail: import cycle not allowed
```

삽질 2) GOPATH 를 다른 곳에 지정해두어서 모듈을 다운로드(`go get`) 받을 때 다른 경로에 파일이 생성되었었다..



