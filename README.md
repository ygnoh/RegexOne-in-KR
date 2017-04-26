## Regex from [RegexOne](http://regexone.com)

**markdown과 한글의 호환 문제 때문에(정말?) 몇 가지 markdown 문제가 존재할 수 있습니다.**

### Lesson 1. 소개

정규표현식(regular expression, regexp, 또는 regex)은 코드나 로그파일, 스프레드시트 등의 텍스트에서 정보를 추출하는데에 매우 유용합니다.

**모든 것은 근본적으로 문자(character)입니다.**

---

### Lesson 1.5: 숫자 매치하기

실제로, 0~9로 이루어진 숫자들도 그저 문자들에 불과합니다.

**\d**는 0에서 9까지의 숫자를 매치할 수 있습니다. **\\**는 문자 d와 구분하기 위해 쓰이고, 그것이 메타 문자(metacharacter)라는 것을 알려줍니다.

---

### Lesson 2: 마침표(.)의 쓰임

__.__(마침표)은 어떠한 문자와도 매치됩니다. 문자, 숫자, 공백 등 모든 것과 매치됩니다.

마침표를 매치시키고 싶다면, 슬래시를 이용하여야합니다. __\.__은 마침표와 매치됩니다.

즉, 그냥 __.__(마침표)를 하면 모든 문자에 대해 매치되고, __\.__을 하면 마침표만을 매칭합니다.

---

### Lesson 3: 특정 문자와 매치하기

예를 들어 우리가 휴대폰 번호를 매칭하고 싶을 때, "(abc) def-ghij" 등은 적절한 숫자가 아닐 겁니다.

이런 경우, 대괄호를 이용한다면 특정 문자들을 매칭시킬 수 있습니다.

하나의 **[..]**는 하나의 문자와 매칭됩니다.

예를 들면, **[abc]** 패턴은 a, b, c 중의 **하나의** 문자와만 매칭이 됩니다.

---

### Lesson 4: 특정 문자 제외시키기

특정 character를 제외하고 싶을 수도 있습니다.

이런 경우에도 비슷하게, 대괄호와 **^ (hat)**을 이용하여 특정 문자들을 제외하여 매칭을 찾을 수도 있습니다.

예를 들어, **[^abc]**는 a, b, c를 **제외한** 한 문자와 매칭이 됩니다.

---

### Lesson 5: 문자의 범위

원하는 범위 내에 속하는 문자와 매치하고 싶다면 어떻게 해야할까요?

운이 좋게도, 대괄호와 **-(dash)**를 사용한다면 손쉽게 처리할 수 있습니다.

예를 들어, **[0-6]** 패턴은 0에서 6사이의 한 문자와만 매칭됩니다.

또한 여러 개의 범위도 한 대괄호 내에서 사용될 수 있습니다.

즉, **[A-Za-z0-9_]**은 A-Z, a-z, 0-9, _ 중에서 한 문자와 매치됩니다.

참고로 **\w**와 완전히 일치하고, 영어 텍스트에서 문자를 매치시키기 위해 자주 쓰입니다.

---

### Lesson 6: 특정 횟수로 반복되는 문자 매치시키기

*주의: 이 lesson의 몇몇 부분은 모든 정규식 implementation에 대해 지원되지 않을 수도 있습니다.*

만약 우리가 반복 문자를 매치하고 싶다면 어떻게 해야할까요?

한가지 간편한 방법은 우리가 원하는 각각의 문자가 몇번이나 반복 되는지를 중괄호를 통해 구체화 해주는 것입니다.

예를 들어, **a{3}**은 **a**가 정확히 3번 반복되는 경우에만 매치될 것입니다.

더 나아가서, **[wxy]{5}**은 **x**, **y**, **z** 문자들이 5번 반복되는 경우에 매치될 것입니다.

---

### Lesson 7: 임의의 횟수로 반복되는 문자 매치시키기

*Kleene: 정규표현식을 제안한 미국의 수학자.*

정규표현식의 한 가지 강력한 기능은 임의의 횟수로 반복되는 문자를 매치시킬 수 있다는 것입니다.

>__\d*__(0 이상)는 *Kleene Star*라고 부릅니다.
>__\d+__(1 이상)은 *Kleene Plus*라고 부릅니다.

예를 들어서, **a+**는 한번 이상 **a**가 반복되는 경우 매치되고, **[abc]+**는 **a** 또는 **b** 또는 **c**가 한번 이상 반복될 때 매치됩니다.

또한, __.*__는 어떠한 문자든 0번 이상 반복될 때 매치됩니다.

---

### Lesson 8: 문자를 선택적으로 매치시키기

문자의 반복 횟수와 관련하여 또 다른, 매우 자주 쓰이는 것은 **?** 입니다.

이 매타 문자는 **?** 앞의 문자 혹은 그룹이 0번, 또는 1번 등장하는 것을 매치합니다.

예를 들어서, **ab?c**는 **abc** 또는 **ac**와 매치됩니다. 왜냐하면 **b**는 **?**에 의해 선택적으로 고려되기 때문입니다.

만약 진짜 물음표 "?"를 매치시키고 싶다면, 슬래시를 사용하여 **\?**를 통해 매치시킬 수 있습니다.

---

### Lesson 9: 공백 매치시키기

정규표현식과 함께 쓰이는 가장 흔한 공백의 형태는 **space ( )**, **tab (\t)**, **new line (\n)**, 그리고 windows에서 유용한 **return (\r)** 입니다.

또한, 이런 공백들은 위의 괄호 안에 적힌 각자의 패턴에 의해 매치됩니다.

추가적으로, **\s**는 위의 제시된 모든 공백들과 매치할 수 있는데, 이것은 raw input 텍스트에 대해 진짜 매우 엄청 유용합니다.

> **Quiz**. `\d\.\s+abc`는 어떤 것들과 매치할 수 있을까요?

---

### Lesson 10: 처음과 시작 지정하기

우리가 "success"라는 단어를 로그 파일에서 매치시키고 싶다고 생각해봅시다. 당연히 우리는 해당 패턴이 "Error: unsuccessful operation" 같은 것들에 매치되게 하고 싶지는 않을 겁니다.

패턴을 확실히 하는 한 가지 방법은 특별한 메타 문자 **^ (hat)**과 **$**을 이용해서 처음과 끝을 명시해주는 것입니다.

위의 예에서, **^success**라는 패턴을 통해 오직 success로 시작하는 줄만 매치시킬 수 있습니다.

> **[^...]**에 쓰였던 **^**과는 다르다는 것에 주의합시다.

만약 **^**, **$**를 모두 사용한다면, 완전하게 처음과 끝이 매치되는 줄만 매치할 수 있습니다.

---

### Lesson 11: 그룹 단위로 매치시키기

정규표현식은 문장 매칭 뿐만 아니라, **추가적인 프로세싱을 위한 정보를 추출**하는 것도 가능하게 해줍니다.

이것은 **문자들의 그룹**을 정의하고 그들을 메타문자인 괄호 **(**, **)**를 통해 캡쳐함으로써 가능합니다.

괄호 쌍 사이에 있는 부분패턴은 그룹으로서 캡쳐될 것입니다. 실제적으로 이것은 전화번호나 이메일 등을 데이터로부터 추출하는데에 사용될 수 있습니다.

당신의 클라우드에 저장된 이미지 파일들을 커맨드 라인 도구를 사용하여 출력한다고 생각해봅시다. 파일 이름을 캡쳐하고 추출하기 위해 당신은 **^(IMG\d+\.png)$**과 같은 패턴을 사용할 것입니다. 하지만 만약 당신이 확장자를 제외하고 파일 이름만을 캡쳐하고 싶다면 **^(IMG\d+)\.png$**와 같은 패턴들을 사용할 것입니다.

---

### Lesson 12: 중첩 그룹

복잡한 데이터를 다룰 때, 많은 경우, 여러 층의 정보를 추출해야만 할 것입니다. 이것은 중첩 그룹이 될 수 있습니다.

만약 이미지 파일이 그들 파일 이름에 순차적인 번호를 가지고 있다면, 당신은 파일 이름과 사진 번호를 하나의 패턴을 사용해서 추출할 수 있습니다. **^(IMG(\d+))\.png$**와 같은 패턴을 통해서 말입니다. (숫자를 캡쳐하기 위해 중첩 괄호를 사용했습니다.)

---

### Lesson 13: More group work

For example, if I knew that a phone number may or may not contain an area code, the right pattern would test for the existence of the whole group of digits **(\d{3})?** and not the individual characters themselves (which would be wrong).

grouping을 통해 한 글자 단위의 연산이 아닌, 한 group단위의 연산을 가능하게 한다.

---

### Lesson 14: It's all conditional

Specifically when using groups, you can use the **| (logical OR, aka. the pipe)** to denote **different possible sets of characters**.

For example, **([cb]ats*|[dh]ogs?)** would match either cats or bats, or, dogs or hogs.

Writing patterns with many conditions can be hard to read, so you should consider making them separate patterns if they get too complex.

---

### Lesson 15: Other special characters

Regular expressions provides a way of specifying the opposite sets of each of these metacharacters by using their upper case letters.

For example, **\D** represents any **non-digit** character, **\S** any **non-whitespace** character, and **\W** any **non-alphanumeric** character (such as punctuation).

Additionally, there is a special metacharacter **\b** which matches the boundary between a word and a non-word character. It's most useful in capturing entire words (for example by using the pattern **\w+\b**).

One concept that we will not explore in great detail in these lessons is **back referencing**, mostly because it varies depending on the implementation. However, many systems allow you to reference your captured groups by using **\0** (usually the full matched text), **\1** (group 1), **\2** (group 2), etc.

