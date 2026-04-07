# Лабораторная работа 5. Построение AST и проверка контекстно-зависимых условий

**Автор:** Савченко Владислав

**Группа:** АВТ-313

**Вариант:** 75

**Дата выполнения:** 2026-04-06

---

## 1. Цель работы

Изучить назначение и принципы работы семантического анализатора в структуре компилятора. Освоить методы построения абстрактного синтаксического дерева (AST) и проверки контекстно-зависимых условий (семантических правил) для заданной синтаксической конструкции.

---

## 2. Вариант задания

### 2.1 Тема работы

Семантический анализатор для упрощённого языка с функциями, типами и арифметическими выражениями.

### 2.2 Грамматика языка

`S -> fun id ( P ) : T { return E } ;`
`P -> id : T | id : T , P`
`T -> Int | Int8 | Int16 | Int32 | Int64 | UInt | UInt8 | UInt16 | UInt32 | UInt64 | String | Bool`
`E -> id | number | ( E ) | E + E | E - E | E * E | E / E`


### 2.3 Примеры верных строк (синтаксически и семантически корректных)

```c
// Пример 1: функция сложения двух чисел
fun sum(a: Int, b: Int): Int { return a + b };

// Пример 2: функция с умножением и вычитанием
fun calc(x: Int, y: Int): Int { return x * y - 5 };

// Пример 3: функция без параметров
fun main(): Int { return 42 };

// Пример 4: функция с булевым возвращаемым типом
fun isPositive(n: Int): Bool { return n > 0 };

// Пример 5: функция со строковым типом
fun greet(name: String): String { return name };

// Пример 6: функция со скобками в выражении
fun complex(a: Int, b: Int, c: Int): Int { return a + (b * c) };

```
## 3. Контекстно-зависимые условия (семантические проверки)
### 3.1 Перечень реализованных проверок

|№|	Проверка | Пример ошибки | Сообщение об ошибке |
|---------|------------|----------|----------|
|1|	Уникальность имён параметров функции|`	fun f(a: Int, a: Int): Int { return 0 };`|	`	Semantic error: duplicate parameter name 'a`|
|2|	Использование объявленных идентификаторов|	`fun f(x: Int): Int { return y };`|	`Semantic error: variable 'y' not declared` |
|3|	Совместимость типов в return|	`fun f(): Int { return true };	`|`	Semantic error: expected Int, found Bool`|
|4|	Совместимость типов в бинарных операциях|	`fun f(): Int { return "hello" + 5 };`|	`Semantic error: operator '+' requires numeric operands (String, Int)`|
|5|	Наличие выражения после return|	`fun f(): Int { return };`|	`Semantic error: missing expression in return statement`|
|6|	Числовые операнды для арифметических операций|	`fun f(): Int { return true + false };`|	`Semantic error: operator '+' requires numeric operands (Bool, Bool)`|
|7|	Деление на ноль (константное выражение)|	`fun f(): Int { return 5 / 0 };`|	`Semantic error: division by zero`|
