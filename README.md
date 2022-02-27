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

### Subscription

```dart
상태관리Subscription =
    상태관리Cubit.stream.listen((상태관리State 상태관리State) {
    emit(state.copyWith(상태: 새로운상태));
});

BlocBuilder<상태관리Cubit, 상태관리State>(
    builder: (context, state) {
    return Text(
        '${state.activeTodoCount}개 남았습니다',
        style: const TextStyle(fontSize: 20.0, color: Colors.redAccent),
    );
    },
),
```

### MultiBlocProvider (many BlockProvider)

```dart
@override
Widget build(BuildContext context) {
    return MultiBlocProvider(
        providers: [
            BlocProvider<상태관리Cubit>(
                create: (context) => 상태관리Cubit(),
            ),
        ],
    )
}
```

### BlocListener

```dart
BlocListener<상태관리Cubit, 상태관리State>(
    listener: (context, state) {
    final int activeTodoCount = state.todos
        .where((Todo todo) => !todo.completed)
        .toList()
        .length;
    context
        .read<상태관리Cubit>()
        .상태관리처리함수(activeTodoCount);
    },
    child: BlocBuilder<상태관리Cubit, 상태관리State>(
    builder: (context, state) {
        return Text(
        '${state.activeTodoCount}개 남았습니다',
        style: TextStyle(fontSize: 20.0, color: Colors.redAccent),
        );
    },
    ),
),
```

### MultiBlocListener

```dart
return MultiBlocListener(
    listeners: [
    BlocListener<상태관리Cubit, 상태관리State>(
        listener: (context, state) {
        context.read<상태관리Cubit>().상태관리처리함수(
                context.read<상태관리Cubit>().state.filter,
                state.todos,
                context.read<상태관리Cubit>().state.searchTerm,
            );
        },
    ),
    ],
)
```

## Dependencies

```bash
flutter pub add equatable
flutter pub add flutter_bloc
flutter pub add uuid
```
