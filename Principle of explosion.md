# Math-Boolean Algebra-Principle of explosion
1. $\mathbb{A} \to \mathbb{B} = C$
	- $\mathbb{A} = true = \mathbb{A} \land \neg \mathbb{A}$
	- $\mathbb{B} = true|false$
	- $\mathbb{C} = true|false = \text{ImplicationResult}(\mathbb{A}, \mathbb{B})$

- **If**|Если:
	- condition $\mathbb{A} = true$,
- **then**|то:
	- $\mathbb{B} = true|false$.
- **$\mathbb{C}$**:
	 - $\mathbf{Set}(\mathbb{A}, \mathbb{B}) \to true|false.$
	 - Note: $\mathbb{C} = \mathbb{B}$
***
2. $\mathbb{A} \to \mathbb{B} = true|false$
	- $\mathbb{A} = \mathbb{A} \land \neg \mathbb{A} = false$
	- $\mathbb{B} = true|false$

- **If**|Если
	- condition $\mathbb{A} = \mathbb{A} \land \neg \mathbb{A} = false$,
- **then**|то
	- $\mathbb{B} = true|false$.
- $\mathbb{C}$: 
	-  $\mathbf{Set}(\mathbb{A}, \mathbb{B}) \to false$.
## Связь с Haskell
- `absurd Void -> a`
	- `Void =` $\mathbb{A} = true$
	- `a =` $\mathbb{B}$
	- `absurd =` $\mathbb{C}$
***
## Miscellaneous:
***
## Little Dictionary:
***
## External Links:
- https://ru.wikipedia.org/wiki/Принцип_взрыва
- https://ru.wikipedia.org/wiki/Закон_противоречия
- 
***
Internal Links:
$\bigtriangleup$ [[Math-Boolean Algebra]]
$\bigcirc$ [[Haskell-0Haskell]]
$\bigtriangledown$ 
***
Tags:
***
Nested Tags:
***
Search:
***
***
