# Các API hỗ trợ webview gameplay cho FE

Đây là các hàm mới được thêm vào webview cho gameplay. Các hàm đã có từ trước đó vẫn giữ nguyên nên sẽ không đề cập.
<br/><br/>
## Changelog

- Update ngày 19/12/2022: Khởi tạo file và viết hàm call API
- Update ngày 26/12/2022: Thêm hàm đóng webview, show toast

<br/><br/>

# 1, Gọi api qua app


### Cách dùng

```javascript
 window.flutter_inappwebview.callHandler("call_api", data)
```

### Thông tin

- endpoint:(string) Endpoint cần gọi API.
- data(Object): Param gọi lên
- method:(string) Phương thức gọi lên. Có 3 phương thức: POST, GET, DELETE. Mặc định sẽ là GET
- shouldEncrypt:(bool) Có mã hóa dữ liệu không.

### Ví dụ

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
# 2. Đóng webview

## Cách đóng

```javascript
 window.flutter_inappwebview.callHandler("close_webview", '')
```

## Ví dụ cách đóng

```javascript
function closeWebview() {
  window.flutter_inappwebview.callHandler("close_webview", '');
}
```
<br/><br/>
# 3, Hiển thị toast

### Cách hiển thị

```javascript
 window.flutter_inappwebview.callHandler("show_toast", '')
```

### Tham số cần truyền

- status:(string) Trả về trạng thái của toast. Chỉ nhận hai giá trị SUCCESS [Thành công] và FAILED [Thất bại]
- message(string): Nội dung hiển thị trên toast
- Cần truyền dúng 2 tham số mới hiển thị toast

###  Ví dụ hiển thị toast

```javascript
function showToast() {
  let data = {
    status: "FAILED",
    message: 'Yêu cầu không thành công',
  };
  window.flutter_inappwebview.callHandler("show_toast", data);
}
```
