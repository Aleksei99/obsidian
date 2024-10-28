#creation_date:  2024-10-28 15:27
#modification_date: Monday 28th October 2024 15:27:45
Error generating daily quote

# scope functions
#scope #functions #let #with

### let
> [!DESCRIPTION] 
> - `let` - Распространенным сценарием, где применяется данная функция, представляет проверка на null 

```kotlin 
	inline fun <T, R> T.let(block: (T) -> R): R

	val sam = Person("Sam", "sam@gmail.com")
    sam.email?.let{ println("Email: $it") }// Email: sam@gmail.com`

    // аналог без функции let
    if(sam.email!=null) println("Email:${sam.email}")
```

### with
> [!DESCRIPTION] 
> - `with` - применяется, когда надо выполнить над объектом набор операций как единое целое 

```kotlin
	inline fun <T, R> with(receiver: T, block: T.() -> R): R

	val tom = Person("Tom", -19,null)

    with(tom) {
        if(email==null) email = "${name.lowercase()}@gmail.com"
        if(age !in 1..110) age = 18
    }
```

### run
> [!DESCRIPTION] 
> - `run` - похожа на функцию with за тем исключением, что run реализована как функция расширения. 

```kotlin
	inline fun <T, R> T.run(block: T.() -> R): R

	val tom = Person("Tom", null)
    val emailOfTom = tom.run {
        if(email==null)
            email = "${name.lowercase()}@gmail.com"
        email
    }
```

### apply
> [!DESCRIPTION] 
> - `apply` - Распространенным сценарием применения является построение объекта в виде реализации вариации паттерна "Строитель": 

```kotlin
inline fun T.apply(block: T.() -> Unit): T

fun main() {  
  
    val bob = Employee()  
    bob.name("Bob")  
        .age(26)  
        .company("JetBrains")  
    println("${bob.name} (${bob.age}) - ${bob.company}") // Bob (26) - JetBrains  
}  
  
data class Employee(var name: String = "", var age: Int = 0, var company: String = "") {  
    fun age(_age: Int): Employee = apply { age = _age }  
    fun name(_name: String): Employee = apply { name = _name }  
    fun company(_company: String): Employee = apply { company = _company }  
}
```

### also
> [!DESCRIPTION] 
> - `also` - подходит для выполнения дополнительных действий (например, логирования), не изменяя объект.

``` kotlin
inline fun T.also(block: (T) -> Unit): T

val file = File("test.txt").also {
	println("Путь к файлу: ${it.absolutePath}") 
}
```