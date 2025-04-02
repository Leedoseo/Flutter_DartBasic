# Dart 기초 문법 정리

## ✅ 1. 변수 선언

```dart
// main 함수 + print() 예시
void main() {
  // 콘솔에 출력
  print('hello world');
}

// var 선언 예시
void main() {
  var name = '이도서';
  print(name);

  name = '도서';
  print(name);
}


```

- `var`: 처음 대입된 값의 타입으로 고정됨 → 이후 타입 변경 시 에러
- `dynamic`: 타입 자유로움, 오타나 실수에 민감함 → 주의 필요
- `final`: 런타임 상수에 적합
- `const`: 컴파일 타임 상수로, 완전 고정값에 적합

---

## ✅ 2. 컬렉션

### ▶ List (배열)
```dart
List<String> fruits = ['apple', 'banana']; // 순서대로 0번쨰, 1번째...
fruits.add('orange'); // 뒤에 2번째 배열에 orange를 추가
print(fruits[0]); // 'apple' // 0번째 배열을 출력
```

### ▶ Set (중복 불가)
```dart
Set<int> numbers = {1, 2, 3, 1};
print(numbers); // {1, 2, 3} 1이 중복이기 때문에 1은 하나만 출력
```

### ▶ Map (딕셔너리)
```dart
Map<String, int> scores = {'math': 90, 'english': 85};
print(scores['math']); // 90
```

---

## ✅ 3. 연산자

### ▶ 산술/비교/논리
```dart
int a = 10, b = 3;
print(a + b);
print(a / b);
print(a > b);
```

### ▶ null 관련 연산자
```dart
String? name;
print(name ?? "Guest");

int? score;
score ??= 100;
```

### ▶ 타입 체크 연산자
```dart
var value = "hello";
print(value is String);
print(value is! int);
```

---

## ✅ 4. 제어문

### ▶ 조건문
```dart
int score = 85;
if (score >= 90) {
  print("A");
} else if (score >= 80) {
  print("B");
} else {
  print("C");
}
```

### ▶ switch 문
```dart
String grade = "B";
switch (grade) {
  case "A":
    print("Excellent");
    break;
  case "B":
    print("Good");
    break;
  default:
    print("Keep going");
}
```

### ▶ 반복문
```dart
for (int i = 0; i < 3; i++) {
  print(i);
}

List names = ['Lee', 'Kim', 'Park'];
for (var name in names) {
  print(name);
}

int i = 0;
while (i < 3) {
  print(i);
  i++;
}

do {
  print(i);
  i++;
} while (i < 3);
```

---

## ✅ 5. 함수 & 람다

### ▶ 기본 함수
```dart
int add(int a, int b) {
  return a + b;
}
```

### ▶ 네임드/포지셔널 파라미터
```dart
void greet({String name = "Guest"}) {
  print("Hello, $name");
}

void showInfo([String? info]) {
  print(info ?? "No info");
}
```

### ▶ 람다 함수
```dart
var square = (int x) => x * x;
print(square(4)); // 16
```

### ▶ typedef
```dart
typedef Operation = int Function(int, int);

int calculate(int a, int b, Operation op) {
  return op(a, b);
}

int multiply(int a, int b) => a * b;
print(calculate(2, 3, multiply));
```

---

## ✅ 6. 예외 처리

```dart
try {
  int result = 10 ~/ 0;
} catch (e) {
  print("에러 발생: $e");
} finally {
  print("항상 실행됨");
}
```

### ▶ on 키워드 사용 예시
```dart
try {
  throw FormatException("잘못된 형식");
} on FormatException catch (e) {
  print("포맷 예외: $e");
}
```

---
