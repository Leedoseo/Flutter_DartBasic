# Dart 기초 문법 정리

## ✅ 1. 변수 선언

```dart
// main 함수 + print() 예시
void main() {
  // 콘솔에 출력
  print('hello world');
}
```
```dart
// var 선언 예시
void main() {
  var name = '이도서';
  print(name);

  name = '도서';
  print(name);
}
```
```dart
// dynamic 선언 예시
void main() {
  dynamic name = '이도서';
  print(name.runtimeType); // String

  name = 1;
  print(name.runtimeType); // int
}
```
```dart
// final vs const 예시
void main() {
  final String name = '이도서';
  name = 'Leedoseo'; // 런타임 에러

  const String name2 = '도서';
  name2 = 'Doseo'; // 컴파일 타임 에러
}
```
- `var`: 처음 대입된 값의 타입으로 고정됨 → 이후 타입 변경 시 에러
- `dynamic`: 타입 자유로움, 오타나 실수에 민감함 → 주의 필요
- `final`: 런타임 상수에 적합
- `const`: 컴파일 타임 상수로, 완전 고정값에 적합

```dart
// DateTime으로 차이 확인
void main() {
  final DateTime now = DateTime.now();
  print(now); // 정상 출력됨
}

void main() {
  const DateTime now = DateTime.now();
  print(now); // 에러 발생
}
```
- `DateTime`: Dart에서 날짜와 시간 정보를 다룰 수 있게 해주는 `class`
  - 주요속성
    - `print(now.year);`      // 연도 (예: 2025)
    - `print(now.month);`     // 월 (1~12)
    - `print(now.day);`       // 일
    - `print(now.hour);`      // 시
    - `print(now.minute);`    // 분
    - `print(now.second);`    // 초

---

## ✅ 2. 컬렉션

### ▶ List (배열)
```dart
void main() {
  // 리스트에 넣을 타입을 <> 사이에 명시할 수 있음.
  List<String> blackPinkList = ['리사', '지수', '제니', '로제'];
  
  print(blackPinkList);
  print(blackPinkList[0]);
  print(blackPinkList[3]);
  
  print(blackPinkList.length);
  
  blackPinkList[3] = '이도서';
  print(blackPinkList);
}
```
### ▶ List-add함수
```dart
void main() {
  List<String> blackPinkList = ['리사', '지수', '제니', '로제'];
  
  blackPinkList.add('이도서'); // 리스트 끝에 추가
  
  print(blackPinkList);
}
```

### ▶ List-where함수
```dart
void main() {
  List<String> blackPinkList = ['리사', '지수', '제니', '로제'];
  
  final newList = blackPinkList.where(
    (name) => name == '리사' || name == '지수',
  );
  
  print(newList);
  print(newList.toList()); // Iterable을 List로 다시 변환할 때 .toList() 사용
}
```

### ▶ List-map함수
```dart
void main() {
  List<String> blackPinkList = ['리사', '지수', '제니', '로제'];
  
  final newBlackPink = blackPinkList.map(
    (name) => '블랙핑크 $name',
  );
  print(newBlackPink);
  
  // Interable을 List로 다시 변환하고 싶을 때 .toList() 사용
  print(newBlackPink.toList());
}
```

### ▶ List-reduce함수
```dart
void main() {
  List<String> blackPinkList = ['리사', '지수', '제니', '로제'];
  
  final allMembers = blackPinkList.reduce((value, element) => value + ', ' + element);
  
  print(allMembers);
}
```

### ▶ List-fold함수
```dart
void main() {
  List<String> blackPinkList = ['리사', '지수', '제니', '로제'];
  
  // reduce() 함수와 마찬가지로 각 요소를 순회하며 실행됨.
  final allMembers = blackPinkList.fold<int>(0, (value, element) => value + element.length);
  
  print(allMembers);
}
```

### ▶ Set (중복 불가)
```dart
void main() {
  Set<String> blackPink = {"로제", "지수", "리사", "제니", "제니"};
  
  print(blackPink);
  print(blackPink.contains("로제"));
  print(blackPink.toList());
  
  List<String> blackPink2 = ["로제", "지수", "지수"];
  print(Set.from(blackPink2));
}
```

### ▶ Map (딕셔너리)
```dart
void main() {
  Map<String, String> dictionary = {
    "Harry Potter" : "해리포터",
    "Ron Weasley" : "론 위즐리",
    "Hermione Granger" : "헤르미온느 그레인저",
  };
  print(dictionary["Harry Potter"]);
  print(dictionary["Hermione Granger"]);
}
```

### ▶ Map타입 키와 값 반환 받기
```dart
void main() {
  Map<String, String> dictionary = {
    "Harry Potter" : "해리포터",
    "Ron Weasley" : "론 위즐리",
    "Hermione Granger" : "헤르미온느 그레인저",
  };
  print(dictionary.keys);
  print(dictionary.values);
  print(dictionary.keys.toList());
  print(dictionary.values.toList());
}
```
### ▶ enum
```dart
enum Status {
  approved,
  pending,
  rejected,
}

void main() {
  Status status = Status.approved;
  print(status); // Status.approved
  print(status.index); // 0
}
```

---

## ✅ 3. 연산자

### ▶ 산술/비교/논리
```dart
void main() {
  double number = 2;

  print(number + 2);
  print(number - 2);
  print(number * 2);
  print(number / 2);
  print(number % 3);
}
```
```dart
void main() {
  int number1 = 1;
  int number2 = 2;

  print(number1 > number2);
  print(number1 < number2);
  print(number1 >= number2);
  print(number1 <= number2);
  print(number1 == number2);
  print(number1 != number2);
}
```
```dart
void main() {
  bool result = 12 > 10 && 1 > 0;
  print(result);

  bool result2 = 12 > 10 && 0 > 1;
  print(result2);

  bool result3 = 12 > 10 || 1 > 0;
  print(result3);

  bool result4 = 12 > 10 || 0 > 1;
  print(result4);

  bool result5 = 12 < 10 || 0 > 1;
  print(result5);
}
```

### ▶ null 관련 연산자
```dart
void main() {
  double? number; // null 허용
  print(number);

  number ??= 3; // null일 때만 대입
  print(number);

  number ??= 4; // 이미 값이 있으므로 대입되지 않음
  print(number);
}
```

### ▶ 타입 비교 연산자
```dart
void main() {
  int number1 = 1;

  print(number1 is int);
  print(number1 is String);
  print(number1 is! int);
  print(number1 is! String);
}
```

---

## ✅ 4. 제어문

### ▶ if, else if, else문
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
```dart
void main() {
  int number = 2;

  if (number % 3 == 0) {
    print("3의 배수입니다.");
  } else if (number % 3 == 1) {
    print("나머지가 1입니다.");
  } else {
    print("맞는 조건이 없습니다.");
  }
}
```

### ▶ switch 문 + enum
```dart
enum Status {
  approved,
  pending,
  rejected,
}

void main() {
  Status status = Status.approved;

  switch (status) {
    case Status.approved:
      print("승인 상태입니다.");
      break;
    case Status.pending:
      print("대기 상태입니다.");
      break;
    case Status.rejected:
      print("거절 상태입니다.");
      break;
    default:
      print("알 수 없는 상태입니다.");
  }

  print(Status.values); // 모든 enum 값 출력
}
```

### ▶ 반복문
```dart
// for문, for...in문
void main() {
  for (int i = 0; i < 3; i++) {
    print(i);
  }
}

void main() {
  List<int> numberList = [3, 6, 9];

  for (int number in numberList) {
    print(number);
  }
}
```
```dart
// while 문
void main() {
  int total = 0;
  while (total < 10) {
    total += 1;
  }
  print(total);
}

// do...while 문
void main() {
  int total = 0;
  do {
    total += 1;
  } while (total < 10);
  print(total);
}
```

---

## ✅ 5. 함수 & 람다

### ▶ 기본 함수
```dart
int addTwoNumbers(int a, int b) {
  return a + b;
}

void main() {
  print(addTwoNumbers(1, 2));
}
```

### ▶ 네임드/포지셔널 파라미터
```dart
// 네임드 파라미터
void greet({required String name, required int age}) {
  print('👋 Hello, \$name! You are \$age years old.');
}

void main() {
  greet(name: '이도서', age: 30);
}
```
```dart
// 포지셔널 파라미터
void greet(String name, int age) {
  print('👋 Hello, \$name! You are \$age years old.');
}

void main() {
  greet('이도서', 25);
}
```
### ▶ 기본값이 있는 포지셔널 파라미터와 네임드 파라미터 기본값 적용
```dart
// 기본값이 있는 포지셔널 파라미터
int addTwoNumbers(int a, [int b = 2]) {
  return a + b;
}

void main() {
  print(addTwoNumbers(1));
}
```

```dart
// 네임드 파라미터 기본값 적용
int addTwoNumbers({
  required int a,
  int b = 2,
}) {
  return a + b;
}

void main() {
  print(addTwoNumbers(a: 1));
}
```

### ▶ 포지셔널 + 네임드 파라미터 섞어서 사용
```dart
int addTwoNumbers(
  int a, {
  required int b,
  int c = 4,
}) {
  return a + b + c;
}

void main() {
  print(addTwoNumbers(1, b: 3, c: 7));
}
```

### ▶ 익명/람다 함수
```dart
// 익명 함수로 List의 모든 값들을 더하는 로직
void main() {
  List<int> numbers = [1, 2, 3, 4, 5];
  
  final allMembers = numbers.reduce((value, element) {
    return value + element;
  });
  
  print(allMembers);
}
```
```dart
// 람다 함수로 List의 모든 값들을 더하는 로직
void main() {
  List<int> numbers = [1, 2, 3, 4, 5];
  
  final allMembers = numbers.reduce((value, element) => value + element);
  
  print(allMembers);
}
```

### ▶ typedef와 활용 예제
```dart
typedef Operation = void Function(int x, int y);

void add(int x, int y) {
  print("결과값 : \${x + y}");
}

void subtract(int x, int y) {
  print("결과값 : \${x - y}");
}

void main() {
  Operation oper = add;
  oper(1, 2);

  oper = subtract;
  oper(1, 2);
}
```
```dart
typedef Operation = void Function(int x, int y);

void add(int x, int y) {
  print("결과 값 : \${x + y}");
}

void calculate(int x, int y, Operation oper) {
  oper(x, y);
}

void main() {
  calculate(1, 2, add);
}
```

---

## ✅ 6. 예외 처리 (try...catch)

### ▶ 에러 없는 코드예제
```dart
void main() {
  try {
    final String name = "이도서의 코딩 노트";
    print(name);
  } catch(error) {ㅇ
    print(error);
  }
}
```

### ▶ 에러 있는 코드예제(throw 키워드 사용) // throw => 에러 발생 키워드
```dart
void main() {
  try {
    final String name = "이도서의 코딩 노트";

    throw Exception("이름이 잘못됐음!");

    print(name);
  } catch(error) {
    print(error);
  }
}
```
---
