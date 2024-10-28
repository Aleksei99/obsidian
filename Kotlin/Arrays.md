#creation_date:  2024-10-28 10:34
#modification_date: Monday 28th October 2024 10:34:11
Error generating daily quote

# Arrays
#Arrays #kotlin 

> [!DESCRIPTION] 
> - 1. С помощью встроенной функции arrayOf() можно передать набор значений, которые будут составлять массив: 
> - 2. Мы можем проверить наличие или отсутствие элементов в массиве с помощью операторов in и !in:
> - 3. Для упрощения создания массива в Kotlin определены дополнительные типы `BooleanArray`, `ByteArray`, `ShortArray`, `IntArray`, `LongArray`, `CharArray`, `FloatArray` и `DoubleArray`
### Code example 
```kotlin 
 val numbers: Array<Int> = arrayOf(1, 2, 3, 4, 5) //1

 println(4 in numbers) // true`
 println(2 !in numbers)// false`

val numbers: IntArray = intArrayOf(1, 2, 3, 4, 5)
val doubles: DoubleArray = doubleArrayOf(2.4, 4.5, 1.2)
```

# Var args
#vararg #kotlin

> [!DESCRIPTION] 
> - 1.Функция может принимать переменное количество параметров одного типа. Для определения таких параметров применяется ключевое слово vararg
> - 2.  Оператор * позволяет передать параметру в качестве значения элементы из массива:
### Code example 
```kotlin 
fun printStrings(vararg strings: String){
    for (str in strings)
        println(str)
}

fun main() {
    printStrings("Tom","Bob","Sam")
    printStrings("Kotlin", "JavaScript","Java","C#","C++")
}


// Operator *
fun changeNumbers(vararg numbers: Int, koef: Int){
    for(number in numbers)
        println(number * koef)
}

fun main() {
    val nums = intArrayOf(1, 2, 3, 4)
    changeNumbers(*nums, koef=2)
}
```