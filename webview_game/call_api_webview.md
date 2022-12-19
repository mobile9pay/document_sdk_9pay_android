# API call webview

Update ngày 10/08/2022

## Ví dụ

```javascript
function getWebValue() {
  let data = {
    endpoint: "/api/challenges",
    data: null,
    method: "POST",
    shouldEncrypt: true,
  };
  window.flutter_inappwebview
    .callHandler("call_api", data)
    .then(function (result) {
      alert(JSON.stringify(result));
      document.getElementById("app_version_name").innerHTML =
        "system version : " + JSON.parse(JSON.stringify(result)).error_code;
    });
}
``` 

## Thông tin

- endpoint:(string) Endpoint cần gọi API.
- data:(map<String, String>): Param gọi lên
- method:(string) Phương thức gọi lên. Có 3 phương thức: POST, GET, DELETE. Mặc định sẽ là GET
- shouldEncrypt:(bool) Có mã hóa dữ liệu không.
