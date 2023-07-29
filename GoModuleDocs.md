go module refrence 내용을 정리합니다. ( https://go.dev/ref/mod )

Go 의존성을 관리하는 시스템으로써 Go Modules system 에 대해 알아보려합니다.

모듈은 배포된 패키지들의 모음집이고, 저장소나 모듈 프록시 서버로부터 다운로드 받을 수 있습니다.

모듈은 "golang.org/x/net" 와 같이 경로로 구분이 되는데 이 내용은 각종 의존성을 포함하여 go.mod 파일에 기록되어 있습니다.

go.mod 파일이 있는 폴더가 module 의 루트 폴더이고, main 모듈은 go 명령어로부터 호출되어진 폴더를 포함하는 모듈입니다.

처음 go.mod 파일을 생성하여줄때, 내가 다운받으려는 패키지(github.com/jooyg62/keyboard)로 명명하여 패키지가 다운로드(go get) 되지 않는 이슈가 있었다.

# go.mod 파일 초기화
go mod init {my module name}

# pkg 다운로드
go get github.com/jooyg62/keyboard
...

