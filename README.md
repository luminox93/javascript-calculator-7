
![Header](https://readme-decorate.vercel.app/api/get?type=rectangle&text=%5B1%EC%A3%BC%EC%B0%A8%5D+%EB%AC%B8%EC%9E%90%EC%97%B4+%EB%8D%A7%EC%85%88+%EA%B3%84%EC%82%B0%EA%B8%B0&width=750&height=250&fontSize=32&fontWeight=800&useGradient=true&fontColor=%23fff&backgroundColor=%23c9c9c9&gradientColor1=%23B3CCFF&gradientColor2=%23F2B8FF)


## 📚 과제 진행 요구 사항
- 저장소를 포크하고 클론한 후, 기능을 구현하기 전 README.md에 구현할 기능 목록을 정리합니다.
- 기능 목록에 맞춰 Git의 커밋 단위를 나눠 커밋합니다.
- AngularJS Git Commit Message Conventions을 참고하여 커밋 메시지를 작성합니다.

## ✨ 기능 요구 사항

- 입력된 문자열에서 숫자를 추출하여 더하는 계산기를 구현합니다.
- 쉼표(`,`) 또는 콜론(`:`)을 구분자로 가지는 문자열을 전달할 경우, 구분자를 기준으로 분리한 각 숫자의 합을 반환합니다.
  - 예: `"" => 0`, `"1,2" => 3`, `"1,2:3" => 6`
- 커스텀 구분자를 지정할 수 있습니다. 커스텀 구분자는 문자열 앞부분의 `//`와 `\n` 사이에 위치하는 문자를 사용합니다.
  - 예: `"//;\n1;2;3" => 6`
- 잘못된 값을 입력할 경우 "[ERROR]"로 시작하는 메시지와 함께 Error를 발생시킵니다.

## 🛠 프로그래밍 요구 사항
- Node.js 20.17.0 버전에서 실행 가능해야 한다.
- 프로그램 실행의 시작점은 App.js의 run()이다.
- package.json 파일은 변경할 수 없으며, 제공된 라이브러리와 스타일 라이브러리 이외의 외부 라이브러리는 사용하지 않는다.
- 프로그램 종료 시 process.exit()를 호출하지 않는다.
- 프로그래밍 요구 사항에서 달리 명시하지 않는 한 파일, 패키지 등의 이름을 바꾸거나 이동하지 않는다.
- 자바스크립트 코드 컨벤션을 지키면서 프로그래밍한다.
- 기본적으로 JavaScript Style Guide를 원칙으로 한다.


## 📂 파일 구조

```
Project

```

## 🚀 설치 및 실행

```bash
# 종속성 설치
npm install

# 프로젝트 실행
npm start
```

## 💡 주요 기능

### 1. 숫자 추출 및 합산 기능

- **기능:** 입력된 문자열에서 숫자를 추출하고, 추출한 숫자들의 합을 반환합니다.
- **동작 방식:**
  - 쉼표(`,`) 또는 콜론(`:`)을 기본 구분자로 사용하여 문자열을 숫자로 분리합니다.
  - 문자열이 빈 값일 경우 `0`을 반환합니다.
  - 분리된 문자열이 하나의 양수만 있을 경우 그 숫자를 그대로 반환합니다.
  - 분리된 문자열이 여러 개의 양수일 경우, 각 숫자를 더한 값을 반환합니다.
  - 유효하지 않은 값이 입력될 경우 에러를 발생시키고 종료합니다.
- **예시:** 
  - 입력: `"1,2,3"` → 출력: `6`
  - 입력: `"0,1,3"` → 출력: `4`
  - 입력: `"a,1,3"` → `[ERROR] 잘못된 입력입니다.` 메세지 출력 후 종료

### 2. **커스텀 구분자 사용**

- **설명:** 사용자가 문자열 앞부분에 커스텀 구분자를 지정할 수 있으며, 기본 구분자에 더해 해당 구분자를 사용해 숫자를 추출하고 합산합니다.
- **동작 방식:**
  - 문자열은 `//{구분자}\n` 형식으로 시작해야 하며, `{구분자}` 부분에 원하는 구분자를 설정할 수 있습니다.
  - 커스텀 구분자는 한 글자 또는 여러 글자로 구성될 수 있습니다.
  - 커스텀 구분자 또한 문자열 덧셈 계산기의 기본 규칙을 따릅니다.
- **예시:**
  - 입력: `"//;\n1;2;3"` → 출력: `6` (구분자는 세미콜론 `;`)
  - 입력: `"//***\n1***2***3"` → 출력: `6` (구분자는 `***`)
  - 입력: `"//<\nA<2;3"` → `[ERROR] 잘못된 입력입니다.` 메세지 출력 후 종료 (구분자는 `<`, `;`)

### 3. **에러 처리**

- **설명:** 사용자가 잘못된 입력을 했을 경우 적절한 에러 메시지를 출력하고, 애플리케이션은 종료됩니다.
- **동작 방식:**
  - 입력에 음수가 포함될 경우, `[ERROR] 음수는 입력할 수 없습니다.` 메시지와 함께 예외를 발생시킵니다.
  - 잘못된 구분자가 사용되거나, 숫자가 아닌 값이 입력될 경우 `[ERROR] 잘못된 입력입니다.` 메시지와 함께 예외가 발생합니다.
- **예시:**
  - 입력: `"-1,2"` → 출력: `[ERROR] 음수는 입력할 수 없습니다.`
  - 입력: `"1,,2"` → 출력: `[ERROR] 잘못된 입력입니다.`

### 4. **입력 및 출력 처리**

- **설명:** 사용자로부터 문자열 입력을 비동기적으로 받아서 계산 결과를 출력합니다.
- **동작 방식:**
  - Console API를 사용하여 입력을 받습니다. (`Console.readLineAsync()`)
  - 계산이 완료된 후 결과를 출력합니다. (`Console.print()`)
- **예시:**
  - 사용자 입력: `"1,2:3"`
  - 출력: `결과: 6`

## 📋 구현해야 할 기능 목록

### 1. **입력 기능**
- [x] 사용자로부터 입력을 받을 수 있어야 한다.
- [x] `Console.readLineAsync()`를 사용하여 입력을 받아야 한다.
- [x] 입력 값이 주어졌을 때, 이를 검증 함수에 넘겨 검증해야 한다.
- [x] 검증 함수에서 검증된 값이 유효한 경우에만 다음 단계로 진행한다.

### 2. **숫자 추출 기능**
- [x] 쉼표(`,`) 또는 콜론(`:`)을 기준으로 문자열을 분리할 수 있어야 한다.
- [x] 커스텀 구분자가 있다면 기존 구분자와 커스텀 구분자를 통해 문자열을 분리할 수 있어야 한다.
- [x] 문자열을 분리한 후 숫자 검증 함수를 통과해야 다음 단계로 진행한다.

### 3. **숫자 합산 기능**
- [x] 분리된 숫자들을 모두 더한 값을 반환할 수 있어야 한다.
  - [x] 빈 문자열이 입력되었을 경우 `0`을 반환해야 한다.
  - [x] 하나의 양수만 있을 경우 해당 양수를 그대로 반환해야 한다.
  - [x] 여러 개의 양수가 있을 경우 각 양수를 합산하여 반환해야 한다.

### 4. **커스텀 구분자 기능**
- [x] 문자열에 커스텀 구분자를 지정할 수 있어야 한다.
- [x] 커스텀 구분자는 `//`로 시작하여 `\n`으로 끝나야 한다.
  - [x] 예: `"//;\n1;2;3"`
- [x] 커스텀 구분자를 기준으로 문자열을 분리할 수 있어야 한다.
- [x] 기본 구분자(쉼표, 콜론)와 함께 커스텀 구분자를 사용할 수 있어야 한다.
  - [x] 예: `"//;\n1,2;3"`

### 5. **에러 처리 기능**
- [x] 입력된 값에 음수가 포함되어 있을 경우 에러를 발생시켜야 한다.
- [x] 양수가 아닌 값이 포함되어 있을 경우 에러를 발생시켜야 한다.
- [x] 입력된 값에 구분자가 아닌 문자열이 포함되어 있을 경우 에러를 발생시켜야 한다.

### 6. **출력 기능**
- [x] 결과 값과 에러 메시지를 모두 출력할 수 있어야 한다.
- [x] 어떤 에러 메세지를 출력할지 입력받고 해당 에러 메세지를 출력할 수 있어야 한다.
- [x] 어떤 값을 출력할지 입력받고 해당 값을 출력할 수 있어야 한다.
  - [x] 결과 값은 `결과: {값}` 형식으로 출력해야 한다.
- [x] `Console.print()`를 사용하여 출력해야 한다.

~~### 6. **에러 메시지 상수 관리**~~
- [ ] 에러 메시지는 상수로 정의하여 관리되어야 한다.
  - [ ] `ERROR_INVALID_INPUT`: 잘못된 입력입니다.
  - [ ] `ERROR_NEGATIVE_NUMBER`: 음수는 입력할 수 없습니다.
  - [ ] `ERROR_INVALID_NUMBER`: 숫자가 아닙니다.
  - [ ] `ERROR_INVALID_DELIMITER`: 잘못된 구분자입니다.
- [x]단순 [ERROR] 출력으로 변경
