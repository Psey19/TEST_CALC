# HomeWork_OOP7

Данная программа работает по следующему принципу:
1) вы вводите первое вещественное число;
2) вы вводите второе вещественное число;
3) вы выбираете нужную арифметическую операцию из списка, подтвердив выбор соответствующим номером в списке;
4) получаете результат.

Соблюдена архитектура по паттерну Model-View-Controller.
В данной программе я решил учесть добавление новых арифметических операция, в данный момент Сложение, Умножение, Деление.
Чтобы программа не сыпалась я завязал классы, зависящие от набора арифметических операций на интерфесах, а именно:
1) LogSumMultyDiv -  Логгер для Сложения, Умножения, Деления
2) SumMultyDivModelGen - Генератор Модели арифметической операции на основе выбора из списка операций Сложения, Умножения, Деления
3) ViewSumMultyDiv - Вьюер для вывода результата, предоставления выбора арифметической операции из списка операций Сложения, Умножения, Деления.
   Также в данном классе я инициализирую Логгер и Генератор Модели, поскольку они все объединены одним набором арифметических операций
   (Возможно это является нарушением SOLID SRP, но зато у меня появляется возможность инициализировать Контроллер по выбранному Вьюеру и ничего в нем не менять
   при добавлении еще одной арифметической операции, мне будет достаточно создать новую модель, новый Логгер, включающий ее, новый Генератор модели, включающий ее,
   новый вьюер, включающий ее и в Main инициализировать контроллер по этому вьюеру)

Соблюдены принципы SOLID, такие как: 
1) SRP. Каждый класс выполняет свой функционал и имеет одну ответственность.
2) DIP. В классе Controller мы создаём экземпляр View, создаём конструктор на его основе и в работе метода ButtonClick используем методы нашего вьера, созданного на основе View.
   С натяжкой или в чистом виде тот же принцип соблюдается в классе ViewSumMultyDiv, поскольку там наш метод возвращает экземпляр Логгера и экземпляр Генератора Модели, тут я не уверен полностью.

Паттерны проектирования:
1) Фабричный метод. Его я использовал в Генераторе Модели. Создал интерфейс ModelGen с методом createModel, который реализуется в классе SumMultyDivModelGen (по параметру номера выбранной нам арифметической операции
   будет создаваться новая Модель для этой операции, а именно: new SumModel(), new MultiplyModel(), new DivisionModel()).

