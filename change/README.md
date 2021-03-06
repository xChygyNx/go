# Change

Классическая задача динамического программирования, в которой необходимо посчитать наименьшее возможное количество монет заданного номинала которой можно набрать необходимую сумму. Программа не только считает наименьшее количество монет, но и выводит номиналы этих монет.  

### Usage  
Исполняемый файл находится в папке cmd, запустить его можно командой go run change.go из папки cmd, или командой go run ./cmd/change.go из корневой папки. Схема команды следующая (приведенная схема работает для папки cmd):  
###### go run change.go "coins_nominals" target  
coins_nominals - список номиналов монет, целые положительные числа  
target         - сумма, которую необходимо набрать монетами заданных номиналов  
если какое до условие не выполняется, программа выведет инструкцию и допущенную ошибку  
Список номиналов монет можно задавать в произвольном порядке  
При корректном вводе программа начнет подбор монет. Может сложится ситуация, когда монетами заданного номинала нельзя набрать необходимую сумму. В этом случае программа сообщит об этом. В случае если сумму заданными монетами набрать возможно, будет выведен наименьший набор монет, которыми можно набрать заданную сумму.  

### Алгоритм  
Создается массив чисел который будет показывать минимальное количество монет необходимых для набора заданной суммы, и одновременно отображение, ключами которого является сумма, а значениями - список монет, которыми данную сумму можно набрать.  
Первому элементу массива даем значение 0 (логично, что сумму равную 0 можно набрать 0 монетами), дальше запускается внешний цикл по увеличению суммы от 1 до необходимой суммы и внутренний цикл по перебору монет всех доступных номиналов. Дальше начинает заполняться массив количества монет. Происходит это следующим образом:  
1) из текущей суммы отнимается номинал текущей монеты  
2) если полученную сумму можно набрать данными монетами (1 результат который запустит цепочку расчета уже есть - 0 можно набрать 0 монет), то берется число монет необходимую для набора этой суммы и увеличивается на 1 (пример, если надо набрать 7 и мы сейчас проверяем монету достоинством 2, то мы проверяем, можно ли заданными монетами набрать 7-2=5, если можно, то 7 можно набрать количеством монет, которыми можно набрать сумму 5 + 1 монета (монетами, необходимыми для набора 5 + монета достоинством 2))
3) сверяем, что полученное количество монет меньше, чем уже записанное в данную ячейку (возможно данную сумму можно набрать несколькими разными способами, нам нужен наименьший по количеству монет). Если это так, мы вписываем новую сумму в массив. Так же для данной суммы вписываем в отображение список монет, коиорая нужна для набора "текущая сумма - номинал текущей монеты" и добавляем к ней текущую монету.  
4) так доходим до требуемой суммы.  
После прохода цикла необходимый набор монет будет записан в отображении по ключу равной заданной сумме

### Tests & Benchmarks  
В папке change есть тесты и бенчмарки. Запускаются стандартно:  
###### go test
и  
###### go test -v --bench .
