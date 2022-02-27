# flutter_todo_cubit

플루터 투두앱(cubit)

## 프로젝트 설명

큐빗을 통한 상태관리

## 구조

### cubit / state

```tree
cubits
├──상태관리구분
│   ├── 상태관리할구분_cubit.dart
│   ├── 상태관리할구분_state.dart
```

### MultiBlocProvider (many BlockProvider)

```dart
@override
Widget build(BuildContext context) {
    return MultiBlocProvider(
        providers: [
            BlocProvider<상태관리할구분Cubit>(
                create: (context) => 상태관리할구분Cubit(),
            ),
        ],
    )
}
```

## Dependencies

```bash
flutter pub add equatable
flutter pub add flutter_bloc
flutter pub add uuid
```
