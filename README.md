## Regex from [RegexOne](http://regexone.com)

**markdown과 한글의 호환 문제 때문에(정말?) 몇 가지 markdown 문제가 존재할 수 있습니다.**

### Lesson 1. An Introduction, and the ABCs

Regualr expressions are extermely useful in extracting information from text such as code, log files, spreadheets, or even documents.

**Everything is essentially a character.**

---

### Lesson 1.5: The 123s

In fact, numbers 0-9 are also just characters.

The character **\d** can be used in place of **any digit from 0 to 9**. The preceding slash distinguishes it from the simple **d** character and indicates that it is a metacharacter.

---

### Lesson 2: The Dot

There is the concept of a **wildcard**, which is represented by the .(dot) metacharacter, and can **match any single character** (letter, digit, whitespace, everything).

In order to specifically match a period, you need to escape the dot by using a slash **\\.** accordingly.

즉, 그냥 **.**(dot)을 하면 모든 character에 대해 매치되고, **\\.**을 하면 **.**(dot)만을 매칭한다.

---

### Lesson 3: Matching specific characters

If we are matching phone numbers for example, we don't want to validate the letters "(abc) def-ghij" as being a valid number!

There is a method for **matching specific characters** using regular expressions, by defining them inside **square brackets**.

For example, the pattern **[abc]** will only match a **single** a, b, or c letter and nothing else.

즉, **[abc]**의 경우, a, b, c중에 **하나에만** 매칭된다.

---

### Lesson 4: Excluding specific characters

특정 character를 제외하고 싶을 수도 있다.

To represent this, we use a similar expression that **excludes specific characters** using the **square brackets** and the **^**(hat).

For example, the pattern **[^abc]** will match any **single** character **except for** the letters a, b, or c.

---

### Lesson 5: Character ranges

What if we want to match a character that can be in a sequential range characters?

Luckily, when using the square bracket notation, there is a shorthand for matching a character in list of **sequential characters** by using the **dash** to indicate a character range.

For example, the pattern **[0-6]** will only match any single digit character from zero to six, and nothing else.

Multiple character ranges can also be used in the same set of brackets, along with individual characters.

An example of this is the alphanumeric **\w** metacharacter which is equivalent to the character range **[A-Za-z0-9_]** and often used to match characters in English text.

즉 하나의 range **[...]**는 하나의 character에 매칭된다.

---

### Lesson 6: Catching some zzz's
*Note: Some parts of the repetition syntax below isn't supported in all regular expression implementations.*

How about the number of repetitions of characters that we want to match?

A convenient way is to specify how many repetitions of each character we want using the **curly braces** notation.

For example, **a{3}** will match the **a** character exactly three times.

**[wxy]{5}** (five characters, each of which can be a **w**, **x**, or **y**)

---

### Lesson 7: Mr. Kleene, Mr. Kleene

*Kleene는 정규표현식을 제안한 수학자 이름이다.*

A powerful concept in regular expressions is the ability to match an arbitrary number of characters.

__\d*__(0 or more) is called *Kleene Star*

__\d+__(1 or more) is called *Kleene Plus*

For example **a+** (one or more a's), **[abc]+** (one or more of any a, b, or c character) and __.*__ (zero or more of any character).

---

### Lesson 8: Characters optional

Another quantifier that is really common when matching and extracting text is the **?** (question mark) metacharacter which denotes **optionality**.

This metacharacter allows you to match either zero or one of the preceding character or group.

For example, the pattern **ab?c** will match either the strings "abc" or "ac" because the b is considered optional.

Use a slash **\?** to match a plain question mark character in a string.

---

### Lesson 9: All this whitespace

The most common forms of whitespace you will use with regular expressions are the **space** ( ), the **tab** (**\t**), the **new line** (**\n**) and the carriage return (**\r**) (useful in Windows environments), and these special characters match each of their respective whitespaces.

In addition, a **whitespace** special character **\s** will match **any** of the specific whitespaces above and is extremely useful when dealing with raw input text.

`\d\.\s+abc`는 어떤 것들과 매치될까?

---