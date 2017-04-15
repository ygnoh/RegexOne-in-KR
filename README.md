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

The most common forms of whitespace you will use with regular expressions are the **space** ( ), the **tab (\t)**, the **new line (\n)** and the carriage return (**\r**) (useful in Windows environments), and these special characters match each of their respective whitespaces.

In addition, a **whitespace** special character **\s** will match **any** of the specific whitespaces above and is extremely useful when dealing with raw input text.

`\d\.\s+abc`는 어떤 것들과 매치될까?

---

### Lesson 10: Starting and ending

Imagine for example we wanted to match the word "success" in a log file. We certainly don't want that pattern to match a line that says "Error: unsuccessful operation"!

One way to tighten our patterns is to define a pattern that describes both the **start and the end of the line** using the special **^ (hat)** and **$ (dollar sign)** metacharacters.

In the example above, we can use the pattern **^success** to match **only** a line that begins with the word "success", but not the line "Error: unsuccessful operation".

> Note that this is different than the hat used inside a set of bracket **[^...]** for excluding characters.

And if you combine both the hat and the dollar sign, you create a pattern that matches the whole line completely at the beginning and end.

---

### Lesson 11: Match groups

Regular expressions allow us to not just match text but also to **extract information for further processing**.

This is done by defining **groups of characters** and capturing them using the special parentheses **(** and **)** metacharacters.

Any subpattern inside a pair of parentheses will be **captured** as a group. In practice, this can be used to extract information like phone numbers or emails from all sorts of data.

Imagine for example that you had a command line tool to list all the image files you have in the cloud. You could then use a pattern such as **^(IMG\d+\.png)$** to capture and extract the full filename, but if you only wanted to capture the filename without the extension, you could use the pattern **^(IMG\d+)\.png$** which only captures the part before the period.

---

### Lesson 12: Nested groups

When you are working with complex data, you can easily find yourself having to extract multiple layers of information, which can result in nested groups.

If each of image files had a sequential picture number in the filename, you could extract both the filename and the picture number using the same pattern by writing an expression like **^(IMG(\d+))\.png$** (using a nested parenthesis to capture the digits).

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

