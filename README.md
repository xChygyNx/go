# GoCalculator

Калькулятор учитывающий порядок операций и скобки.  

##### Доступные операции  
'+', '-', '*', '/' - стандартные математические операции  
'^' - возведение в степень (теперь и в отрицательную)

### Usage 
Для запуска калькулятора в корневой папке проекта выполните go run cmd/calculator.go, после чего вам будет предложено ввести выражение.  
Программа работает в цикле, т.е. после решения примера поступит предложение ввести следующий пример.  
Для выхода из программы введите "exit" (без кавычек)  

##### Некоторые правила ввода примера  
Ввод примера в целом осуществляется в свободной форме.  Числа и действия могут быть разделены пробельными символами, могут быть написаны без них. Но вот несколько неинтуитивных правил:  
1) Для записи отрицательного числа '-' в начале обязательно должен писаться слитно с последующими числами, иначе калькулятор воспримет его как математическое действие (вычитание)  
2) При записи наподобие "42." программа сочтет данное число как целое, то есть просто "42"  
3) При записи наподобие ".42" программа сочтет данное число как дробное, с целой частью равной нулю, то есть как "0.42"  
4) Возведение в дробную степень будет отбрасывать дробную часть у степени, т.е. "2 ^ 6.33" будет считываться как "2 ^ 6"  

##### Калькулятор проверяет:  
1) Что в введенном выражение состоит только из цифр, математических операций, простых скобок и побельных символов. При наличии других символов выдаст ошибку  
2) правильную расстановку скобок (каждая открывающая скобка имеет закрывающую и что нет закрывающих скобок, если перед этим не было открывающей)  
3) правильное соотношение чисел и действий
4) нет деления на 0
