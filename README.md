# Домашнее задание к занятию «Базы данных, их типы» - Куприянов Владимир.

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

---

### Задание 1. СУБД

### Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать 
правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для
каждой предметной области. 

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему? 
 
1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков.
СУБД должна гарантировать целостность и чёткую структуру данных.

1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы? 

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к 
маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? 
СУБД должны быть гибкими и быстрыми.

1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу 
и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это 
реализовать?

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов 
по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать
со связями.

1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД 
логистов?

1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

*Приведите ответ в свободной форме.*

1.1. - Подойдут реляционные базы данных и/либо базы данных SQL (MySQL, PostgreSQL, SQL). Их особенность состоит в надежности за счёт низкого риска потери данных, т.к. они заменяются в одной таблице и их целостность гарантирована.

1.1.* - Если хеширование стало занимать длительное время, подойдёт база данных типа "ключ-значение" (например Riak и Dynamo от Amazon) Т.к этот тип базы данных используют хеш-таблицу, с уникальным ключом и указателем на конкретный объект данных, а чтобы прочитать значение, нужно знать ключ и блок, поскольку ключ является хэшем (блоком + ключ). За счет кэширующих механизмов производительность должна возрасти. . .

1.2. - Для лендингов лучше использовать тип СУБД NoSQL: ключ-значение, т.к. они просты в настройке, прекрасно масштабируются и имеют быстрый отклик на запросы информации. Для CRMа  можно использовать графовую базу данных, для эффективности анализа клиентских запросов и предпочтений.

1.2.* - Да, можно. PostgreSQL и/или реляционную СУБД.

1.3. - В этом случае лучше использовать документоориентированные или иерархическую БД (NoSQL). Такая база имеет четкую структуру и зависимости, а также позволяет легко изменять ее и осуществлять поиск обучающего материала.

1.3.* - Лучше это реализовать используя MongoDB. При сложных операциях СУБД демонстрирует хорошие показатели, а с помощью идентификатора можно осуществлять манипуляции над объектом с высокой скоростью.

1.4. - Подойдет графовая СУБД, предназначенная для хранения информации, связанной с графами, где требуется хранить связи по разным критериям между пользователями, анализировать маршруты и выдавать из них наиболее подходящие.

1.4.* - Подключить можно, но это может привести к ряду проблем, во избежании которых лучше сделать отделу закупок отдельную БД. Так можно с намного большей вероятностью сохранить необходимую целостность данных, и вести учёт блокировки транзакций (напимер из за отсутствия товара на складе). Неплохим решением будет структурированная и надежная система - реляционная БД.

1.5.* Все перечисленные выше задачи, теоретически, можно решить, используя одну СУБД, но нужно учитывать, что разным отделам под их задачи стоят разные приоритеты. Например финансовым аналитикамнеобходима целостность и четкая структура, за счет которой будет потеря скорости обработки запросов. Сесть на два стула (надёжность и скорость) не получится, придётся чем то пожертвовать.

---

### Задание 2. Транзакции

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы 
транзакция завершилась успешно. Ориентируйтесь на шесть действий.

2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?

*Приведите ответ в свободной форме.*

2.1. - Вначале выбирается услуга "пополнение счета" и проверяется ее доступность (1).
Далее вводится данные банковской карты и пин-код, проверка корректности введенных данных, формируется транзакция с присвоением номера (2).
Затем происходит подтверждение внесённых данных (3).
После подтверждения эти данные направляются к оператору, который уже перенаправляет их банку получателю (4).
Банк-получатель проверяет полученные данные и данные счета, и, в зависимости от корректности (или не корректности) данных подтверждает (или отклоняет транзакцию) (5).
Наконец банк посылает ответ о результате выполнения транзакции оператору, а он направляет ее пользователю (6).
В результате счет либо пополнен либо пользователь увидит сообщение об отклонении транзакции.

2.1.* - Порядок практически не изменяется, за исключением того, что в базе данных оператора зафиксированно установленные пользователем данные для автоматического пополнения счета (данные карты, условия и срок пополнения), руководствуясь которыми и выполняется пополнение счета.

---

### Задание 3. SQL vs NoSQL

3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL. 

3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.

*Приведите ответ в свободной форме.*

3.1. - Преимущества SQL-систем по отношению к NoSQL:
1 - Целостность данных.
2 - Надежность.
3 - Поддержка транзакций.
4 - Строгие правила проектирования.
5 - Отображение данных в наиболее простой для пользователя форме.

3.1.* - На мой взгляд преимущества у NewSQL систем перед SQL и NoSQL - это:
<br>
Архитектура, обеспечивающая намного выше производительность узла, чем доступный из традиционных решений RDBMS. Системы NewSQL приблизительно в 50 раз быстрее, чем традиционный OLTP RDBMS.
SQL является основным механизм для взаимодействия.
ACID поддержка транзакций.
Механизм управления без применения блокировок, таким образом считывающие данные в реальном времени не будут находится в противоречии с записывающими, что исключает конфликт.
Удобное масштабирование, способное управлять большим количеством узлов, не перенося узкие места.

---

### Задание 4. Кластеры

Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу 
выделено 1000 машин. 

На основе какого критерия будете выбирать тип СУБД и какая модель *распределённых вычислений* 
здесь справится лучше всего и почему?

*Приведите ответ в свободной форме.*

---

Задания,помеченные звёздочкой, — дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже разобраться в материале.
