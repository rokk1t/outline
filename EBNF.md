# Extended Backus–Naur Form (EBNF). Расширенная Бэкус — Наурова форма
Конспект к видео [Что такое расширенная форма Бэкуса-Наура? Душкин объяснит](https://youtu.be/xtjvAsrpKf4)
Терминальные символы записываются в виде "terminal symbols"/'terminal symbols', а нетерминальные в UPPER CASE.
1. Concatenation. Конкатенация.
Operator: `,`
EBNF: `A = B, C`
Chomsky Notation: $\alpha \to \beta\gamma$
Может опускаться.
2. Option. Опция.
Operator: `|`
EBNF: `A = b | c`
Chomsky Notation: $\alpha \to \beta,\; \alpha \to \gamma$
3. Condition. Условие.
Operator: `[]`
EBNF: `A = [b]`
Chomsky Notation: $\alpha \to \beta,\; \alpha \to \epsilon$ , где $\epsilon$ — пустая строка
`B` может отсутствовать.
4. Repetition. Повторение.
EBNF: `A = {b}`
Operator: `{}`
Chomsky Notation: $\alpha \to \epsilon, \alpha \to \beta\alpha$
`B` может повторяться 0 или более раз.
5. Grouping / Группировка
Operator: `()`
EBNF: `A = (b|c),d`
Chomsky Notation: $\alpha \to \beta\delta, \alpha \to \gamma\delta$
- Пример #1:
```EBNF
EBNF = { OPERATOR }.
OPERATOR = IDENTIFICATOR '=' EXPRESSION.
EXPRESSION = TERMINAL { '|' TERMINAL }.
TERMINAL = FACTOR { ',' FACTOR }.
FACTOR = IDENTIFICATOR | CHAIN | '[' EXPRESSION ']' | '(' EXPRESSION ')' | '{' EXPRESSION '}'.
IDENTIFICATOR = ('"' { A-Z } '"') | ('\'' { A-Z } '\'').
CHAIN = ('"' { a-z } '"') | ('\'' { a-z } '\''). // неполный перечень массива символов. Там ещё UTF-8 и другие.	
```
- Пример #2:
```EBNF
Object = 'object' StringLiteral '{' Code ( Object | Data )* '}'
```
$A \to \alpha$: Акцентирование внимания
from https://docs.soliditylang.org/en/latest/yul.html#specification-of-yul-object
***
## Little Dictionary:
- **Формальная грамматика**: задаётся (описывается / определяется) как множество правил вида $\alpha \to \beta$, где $\alpha, \beta$  — любая строка из терминальных и/или нетерминальных символов.  $\alpha \in (N \cup T)^+, N \neq \emptyset$, где $N$ — это множество нетерминальных символов, $T$ — это множество терминальных символов.
	- **Контекстно-свободная грамматика**: $\subset$ Формальная грамматика. Задаётся (описывается, определяется) как множество правил вида $A \to \alpha$, где $A$  — это один нетерминальный символ.
		- **Регулярная грамматика**: $\subset \text{Контекстно-свободная грамматика}$
			- **Праволинейная**: Задаётся как множество правил вида $A \to \alpha B$, где $B$  — это один нетерминальный символ.
			- **Леволинейная**: Задаётся как множество правил вида $A \to B \alpha$
- **Формальный математический аппарат**: это множество математических методов (как изучается?) и математических объектов (что изучается).
- **Никлаус Вирт**: предложил Extended Backus–Naur Form
- **BNF/EBNF**: контекстно свободных грамматик
- **Avram Noam Chomsky**: придумал формальный математический аппарат
	- **Chomsky Notation**: Cпособ записи правил грамматики в теории формальных языков.
- **Терминальные символы / Терминалы / $\alpha$**: Конкретные строки или символы, которые появляются в финальном выводе, например, 'object', {, }.
- **Нетерминальные символы / Нетерминалы / $A, B$**: Абстрактные элементы, используемые для построения иерархии языка. Они раскрываются до терминальных символов через применение правил.
***
External Links: 
***
Internal Links: 
***
Tags: 
***
Nested Tags: 
***
Search: 
***
***