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

## 3.2 Таблица совместимости типов

|Операция|	Допустимые типы | Результирующий тип| 
|---------|------------|----------|----------|
|`E + E`|		Int, Int8, Int16, Int32, Int64, UInt, UInt8, UInt16, UInt32, UInt64|Int (после приведения)|
|`E - E`|		Int, Int8, Int16, Int32, Int64, UInt, UInt8, UInt16, UInt32, UInt64|Int (после приведения)|
|`E * E`|	Int, Int8, Int16, Int32, Int64, UInt, UInt8, UInt16, UInt32, UInt64|	Int (после приведения)|
|`E / E`|		Int, Int8, Int16, Int32, Int64, UInt, UInt8, UInt16, UInt32, UInt64|Int (после приведения)|	
|`return E`|	Тип E должен совпадать с типом возврата функции|—|	

## 4. Структура AST
### 4.1 Описание типов узлов
```
// Типы данных
enum class Type {
    INT, INT8, INT16, INT32, INT64,
    UINT, UINT8, UINT16, UINT32, UINT64,
    STRING, BOOL,
    ERROR
};

// Базовый класс узла AST
class ASTNode {
public:
    virtual ~ASTNode() = default;
    virtual void print(int indent = 0) const = 0;
    virtual std::string getNodeType() const = 0;
};

// Программа (корневой узел)
class ProgramNode : public ASTNode {
public:
    std::unique_ptr<FunctionDeclNode> function;
    
    void print(int indent = 0) const override;
    std::string getNodeType() const override { return "Program"; }
};

// Объявление функции
class FunctionDeclNode : public ASTNode {
public:
    std::string name;
    std::vector<std::unique_ptr<ParamNode>> params;
    Type returnType;
    std::unique_ptr<ReturnNode> returnStmt;
    
    void print(int indent = 0) const override;
    std::string getNodeType() const override { return "FunctionDecl"; }
};

// Параметр функции
class ParamNode : public ASTNode {
public:
    std::string name;
    Type type;
    
    void print(int indent = 0) const override;
    std::string getNodeType() const override { return "Param"; }
};

// Оператор return
class ReturnNode : public ASTNode {
public:
    std::unique_ptr<ExprNode> expr;
    
    void print(int indent = 0) const override;
    std::string getNodeType() const override { return "Return"; }
};

// Базовый класс для выражений
class ExprNode : public ASTNode {
public:
    Type type;
    virtual Type getType() const { return type; }
};

// Идентификатор (переменная/параметр)
class IdNode : public ExprNode {
public:
    std::string name;
    
    void print(int indent = 0) const override;
    std::string getNodeType() const override { return "Id"; }
};

// Числовой литерал
class NumberNode : public ExprNode {
public:
    int value;
    
    void print(int indent = 0) const override;
    std::string getNodeType() const override { return "Number"; }
};

// Бинарная операция
class BinaryOpNode : public ExprNode {
public:
    std::unique_ptr<ExprNode> left;
    std::string op;  // +, -, *, /
    std::unique_ptr<ExprNode> right;
    
    void print(int indent = 0) const override;
    std::string getNodeType() const override { return "BinaryOp"; }
};
```
### 4.2 Рисунок AST для верной строки
### Входная программа:
`fun calc(a: Int, b: Int): Int { return a + b };`
## AST в графическом виде:
<img width="1773" height="656" alt="Снимок экрана 2026-04-06 144414" src="https://github.com/user-attachments/assets/aa97c2dd-8991-479a-9b7f-f9595aff5af9" />

## 4.3 Формат вывода AST в программе
<img width="1919" height="1027" alt="image" src="https://github.com/user-attachments/assets/aabd3f89-d2e6-4cb4-a301-a37fd991b139" />

<img width="1919" height="1033" alt="image" src="https://github.com/user-attachments/assets/78dd1013-fcb2-4ab6-ae8a-4642e75b103c" />

<img width="1919" height="1034" alt="image" src="https://github.com/user-attachments/assets/99c6e99d-b3cf-4ad2-889c-7c09342aa3fe" />

<img width="1915" height="1028" alt="image" src="https://github.com/user-attachments/assets/8ff463fe-e1dc-42f8-9a11-c912f07dd3c9" />

<img width="1919" height="1029" alt="image" src="https://github.com/user-attachments/assets/64f100f1-6b25-4375-9c42-6c681c443ef9" />

## 6. Инструкция по запуску
### 6.1 Требования
Python 3.8 или выше

Операционная система: Linux, macOS или Windows

Дополнительные библиотеки не требуются (используется только стандартная библиотека)

### 6.2 Установка и запуск
```
# Переход в директорию проекта
cd lab5-semantic-analyzer

# Запуск программы (без дополнительных установок)
python src/main.py test/valid.txt

# Или с использованием Python 3 (Linux/macOS)
python3 src/main.py test/valid.txt
```
### 6.3 Структура проекта

lab5-semantic-analyzer/
├── README.md                    # Документация
├── src/                         # Исходные файлы
│   ├── __init__.py
│   ├── main.py                  # Точка входа
│   ├── lexer.py                 # Лексический анализатор
│   ├── parser.py                # Синтаксический анализатор
│   ├── ast.py                   # Определения узлов AST
│   └── semantic.py              # Семантический анализатор
├── test/                        # Тестовые файлы
│   ├── valid.txt                # Корректная программа
│   ├── duplicate.txt            # Дубликат параметра
│   ├── undeclared.txt           # Необъявленная переменная
│   ├── type_mismatch.txt        # Несовместимость типов
│   ├── string_op.txt            # Строковая операция
│   ├── div_zero.txt             # Деление на ноль
│   └── missing_expr.txt         # Отсутствие выражения
└── screenshots/                 # Скриншоты работы программы
    ├── test1_valid.png
    └── ...

### 6.4 Использование программы
```
# Базовый запуск с анализом файла
python src/main.py input.txt

# Вывод AST в JSON формате
python src/main.py input.txt --json

# Тихий режим (только ошибки)
python src/main.py input.txt --quiet

# Вывод справки
python src/main.py --help
```
### 6.5 Пример сеанса работы (Python)
```
$ python src/main.py test/valid.txt

=== Лексический анализ ===
Успешно: 15 токенов

=== Синтаксический анализ ===
Успешно: программа соответствует грамматике

=== AST ===
Program
└── FunctionDecl: sum
    ├── ReturnType: Int
    ├── Param: a : Int
    ├── Param: b : Int
    └── Body: Return
        └── BinaryOp: +
            ├── Id: a (Int)
            └── Id: b (Int)

=== Семантический анализ ===
Проверка уникальности параметров... ✓
Проверка наличия выражения после return... ✓
Проверка типов в выражении... ✓
Проверка совместимости типов return... ✓

Результат: Ошибок не найдено.
```
### Короткая версия (самое главное):
```
# Клонируйте/перейдите в папку проекта
cd lab5-semantic-analyzer

# Запустите программу
python src/main.py test/valid.txt
```
