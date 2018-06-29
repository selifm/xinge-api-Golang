# xinge
腾讯信鸽push Golang lib

## 用法

### 安装
`$ go get github.com/FrontMage/xinge`

### 安卓单账号push
```go
import (
    "net/http"
    "io/ioutil"
    "encoding/json"
    "fmt"
    "github.com/FrontMage/xinge"
    "github.com/FrontMage/xinge/req"
    "github.com/FrontMage/xinge/auth"
)

func main() {
    auther := auth.Auth{AppID: "AppID", SecretKey: "SecretKey"}
    pushReq, _ := req.NewSingleAndroidAccountPush("account", "title", "content")
    auther.Auth(pushReq)

    c := &http.Client{}
    rsp, _ := c.Do(pushReq)
    defer rsp.Body.Close()
    body, _ := ioutil.ReadAll(rsp.Body)

    r := &xinge.CommonRsp{}
    json.Unmarshal(body, r)
    fmt.Printf("%+v", r)
}
```

### 苹果单账号push
```go
import (
    "net/http"
    "io/ioutil"
    "encoding/json"
    "fmt"
    "github.com/FrontMage/xinge/req"
    "github.com/FrontMage/xinge/auth"
)

func main() {
    auther := auth.Auth{AppID: "AppID", SecretKey: "SecretKey"}
    pushReq, _ := req.NewSingleIOSAccountPush("account", "title", "content")
    auther.Auth(pushReq)

    c := &http.Client{}
    rsp, _ := c.Do(pushReq)
    defer rsp.Body.Close()
    body, _ := ioutil.ReadAll(rsp.Body)

    r := &xinge.CommonRsp{}
    json.Unmarshal(body, r)
    fmt.Printf("%+v", r)
}
```

### 安卓多账号push
`WIP`

### iOS多账号push
`WIP`

### 设备push
`WIP`

### 标签push
`WIP`