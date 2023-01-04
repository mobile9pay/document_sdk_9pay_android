# Các API hỗ trợ webview gameplay cho Mobile



## Changelog

- Update ngày 04/01/2023

# 1, Tạo màn loading

### Mô tả

- Widget WebviewGame cần truyền param WebViewGameArguments. Ở đây có 1 trường là Widget loadingWidget. Nếu muốn tạo màn loading cho webview thì truyền UI màn loading vào đây, nếu ko truyền gì sẽ mặc định là widget Sizedbox
- WebviewGame sẽ cập nhật tiến độ loading qua bloc ProcessLoadingCubit.


### Ví dụ

Thêm UI LoadingGameplayTet cho webview game tết

```dart
        WebviewGame(
          args: WebViewGameArguments(
            url: args.url,
            title: 'Đập niêu',
            header: state,
            loadingWidget: const LoadingGameplayTet(),
          ),
        );
```
Cập nhật tiến độ trong widget LoadingGameplayTet bằng cách

```dart
    BlocSelector<ProcessLoadingCubit, ProcessLoadingState, double>(
      selector: (state) => state.process / 100,
      builder: (_, process) {
        return Padding(
          padding: const EdgeInsets.symmetric(horizontal: 20),
          child: Container(
            decoration: BoxDecoration(
              color: const Color(0xFFFFF6D2),
              borderRadius: BorderRadius.circular(20),
            ),
            padding: const EdgeInsets.all(2),
            child: LinearPercentIndicator(
              animation: true,
              padding: EdgeInsets.zero,
              backgroundColor: const Color(0xFFFFF6D2),
              progressColor: const Color(0xFFFDAB31),
              lineHeight: 8.0,
              percent: process,
              animateFromLastPercent: true,
              animationDuration: 1000,
              barRadius: const Radius.circular(20),
            ),
          ),
        );
      },
    );
```