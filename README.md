# Документирование javadoc

javadoc — это генератор документации в HTML-формате из комментариев исходного кода Java и определяет стандарт для документирования классов Java. Для создания доклетов и тэглетов, которые позволяют программисту анализировать структуру Java-приложения, javadoc также предоставляет API. В каждом случае комментарий должен находиться перед документируемым элементом.

---
Чтобы включить контент в Javadoc, необходимо  использовать следующий комментарий:

/**
*
*
*
*
*/
---
## Дескрипторы 

Дескрипторы javadoc, начинающиеся со знака @, называются автономными и должны помещаться с начала строки комментария (лидирующий символ * игнорируется). Дескрипторы, начинающиеся с фигурной скобки, например {@code}, называются встроенными и могут применяться внутри описания.

Комментарии документации применяют для документирования классов, интерфейсов, полей (переменных), конструкторов и методов. В каждом случае комментарий должен находиться перед документируемым элементом.
| Дескриптор                     | Применение                  |                          Описание                         |
| :-------------:                |:----------------------------:| :------------------------------------------------------: |
| @author                        | 	Класс, интерфейc             |                     Автор                               |
| @version                       | Класс, интерфейс              |  Версия. Не более одного дескриптора на класс           |
| @since                         | Класс, интерфейс, поле, метод |Указывает, с какой версии доступно                       |
|      @see                      | Класс, интерфейс, поле, метод |Ссылка на другое место в документации                    |
| @param                         | Метод                         | Входной параметр метода                                 |
| @return                        |  Метод                        |Описание возвращаемого значения                          |
| @exception имя_класса описание |Метод                  |Описание исключения, которое может быть послано из метода        |
| @throws имя_класса описание    |  Метод                        |Описание исключения, которое может быть послано из метода|
|@deprecated                     | Класс, интерфейс, поле, метод | Описание устаревших блоков кода                         |
|{@link reference}               | Класс, интерфейс, поле, метод |Ссылка                                                   |
| {@value}                       | Статичное поле                |Описание значения переменной                             |
---
## Порядок тегов
Oracle определил  следующий порядок:
* @author (classes and interfaces)
* @version (classes and interfaces)
* @param (methods and constructors)
* @return (methods)
* @throws (@exception is an older synonym)
* @see
* @since
* @serial
* @deprecated

---
## @author

Комментируя лучшие практики Javadoc, некоторые люди рекомендуют использовать @author, потому что значение автора легко теряет актуальность, а элемент управления исходным кодом обеспечивает лучшее указание на последнего автора.

[Javadoc coding standards](https://blog.joda.org/2012/11/javadoc-coding-standards.html)

---
## @Param  

применяются только к методам и конструкторам, которые принимают параметры.Также  могут применяться к классам -дженерикам, которые работают с различными типами объектов.

```java
/**
* @param <T> This describes my type parameter
*/
    class MyClass<T>{

        }
```
---

## @return 
только методы получают тэг @return. Если метод имеет модификатор void, он ничего не возвращает. Если в нем нет void, нужно включить тэг @return, чтобы избежать ошибки при компиляции Javadoc.

---

## @throws 

@throws добавляются в методы или классы только в том случае, если метод или класс генерируют ошибку определенного типа
```java
@throws IOException if your input format is invalid
```
---
## Комментарии к конструкторам

Рекомендуется включать конструктор в класс. Однако, если конструктор отсутствует, Javadoc автоматически создает конструктор в Javadoc, но исключает любое описание конструктора.
Конструкторы имеют тэги @param, но не тэги @return. Все остальное так же, как и с методами.

---

## Комментарии к полям

Поля имеют только описания. Можно добавлять комментарии в поле, если бы поле было чем-то, что пользователь будет использовать.

---

## Кейсы, где комментарии не нужны

Oracle говорит, что есть три сценария, где комментарии к документу наследуются, поэтому вам не нужно включать комментарии в эти сценарии:

* когда метод в классе переопределяет метод в суперклассе;
* когда метод в интерфейсе переопределяет метод в суперинтерфейсе;
* когда метод в классе реализует метод в интерфейсе

[How to write Javadoc comments]([https://blog.joda.org/2012/11/javadoc-coding-standards.html](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html#tag))


---
## @see 

Тэг @see предоставляет ссылку. 
Существуют различные способы обозначить то, на что надо ссылаться, чтобы создать ссылку. При ссылке на поле, конструктор или метод в том же поле, используется #.
При ссылке на другой класс, сначала пишется имя этого класса, затем # и имя конструктора, метода или поля.
При ссылке на класс в другом пакете, сначала указывается имя пакета, затем класс и так далее. Пример из Oracle:

```java
@see #field
@see #Constructor(Type, Type...)
@see #Constructor(Type id, Type id...)
@see #method(Type, Type,...)
@see #method(Type id, Type, id...)
@see Class
@see Class#field
@see Class#Constructor(Type, Type...)
@see Class#Constructor(Type id, Type id)
@see Class#method(Type, Type,...)
@see Class#method(Type id, Type id,...)
@see package.Class
@see package.Class#field
@see package.Class#Constructor(Type, Type...)
@see package.Class#Constructor(Type id, Type id)
@see package.Class#method(Type, Type,...)
@see package.Class#method(Type id, Type, id)
```
---

## Ссылки

Создавать ссылки на другие классы и методы можно используя тэг {@link}.
Пример создания ссылки из [Javadoc coding standards](https://blog.joda.org/2012/11/javadoc-coding-standards.html)

```java
/**
* First paragraph.
* <p>
* Link to a class named 'Foo': {@link Foo}.
* Link to a method 'bar' on a class named 'Foo': {@link Foo#bar}.
* Link to a method 'baz' on this class: {@link #baz}.
* Link specifying text of the hyperlink after a space: {@link Foo the Foo class}.
* Link to a method handling method overload {@link Foo#bar(String,int)}.
*/
public ...
```

Для ссылки на другой метод в том же классе используется формат: {@link #baz}. Чтобы связать метод с другим классом, используется формат: {@link Foo # baz}. Тем не менее, не надо мудрить с гиперссылкой. При обращении к другим классам можно использовать тэги <code>.

---
## Дополнительная информация о Javadoc
    
    [JavaDoc-Oracle](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html)
