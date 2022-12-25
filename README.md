# Postgres-trainer
Простой sql - тренажер на базе PostgreSQL и FastAPI прямо у вас в браузере.

Позволяет создать тренеровочную базу данных всего одним нажатием клавиши и точно также быстро ее удалить. Вы можете делать все, что угодно с вашим экземпляром БД не опасаясь последствий. Нажатием клавиши "New database" вы создадите новый docker - контейнер с наполненной данными БД.
За основу взята БД Nordwind от Microsoft, которой вполне достаточно для тренировки sql - запросов практически любой сложности.
В качестве редактора кода используется [Ace editor](https://ace.c9.io/), который обеспечивает подсветку синтаксиса и автокомплит.
Для удобства добавлена визуальная схема БД.

## Использование

Для использования вам необходим Docker, инструкцию по установке на вашу операционную систему вы можете найти [здесь](https://docs.docker.com/engine/install/).
После установки Docker клонируйте репозиторий в удобную для вас деректорию:

```git clone https://github.com/NikSan3452/Postgres-trainer.git```

Перейдите в папку src и последовательно выполните команды в терминале:

 - ```cd src```

Установка необходимых зависимостей
- ```pip install -r requirements.txt```

Загрузит и создаст образ python и FastAPI сервер
- ```docker-compose -f docker-compose.yml build```

Загрузит и создаст образ PostgresSQL с готовой БД внутри
- ```docker-compose -f docker-compose.db.yml build```

Запуск сервера
- ```docker-compose -f docker-compose.yml up```

Далее перейдите по адресу ```http://127.0.0.1:8000/``` в своем браузере.
Всё готово, можно работать. Для остановки сервера нажмите ctrl+c в терминале.

Чтобы создать экземпляр БД нажмите кнопку "New database" и дождитесь создания контейнера с БД(15 секунд), после загрузки вы должны увидеть в окне вывода результатов текст - "Новая база данных успешно создана". Чтобы удалить текущий экземпляр - нажмите delete, при этом в окне вывода результатов должен появиться текст - "База данных удалена". Для выполнения запросов к БД введите запрос и нажмите кнопку "Run". 

```Внимание!``` Результаты работы удаляются сразу после остановки контейнера, поэтому не используйте тренажер для реальных задач.

```Внимание!``` ***Во время работы тренажера используются cookie, поэтому их очистка приведет к некоректной работе, воизбежании этого не удаляйте cookie во время работы. Если по какой-то причине вы удалил cookie, остановить сервер или зайдите в Docker и вручную удалите контейнер, а затем вновь запустите сервер. Далее создайте новую БД. Срок действия Cookie по умолчанию составляет 30 дней. Этот параметр можно изменить в файле src/core/config.py. После окончания работы обязательно нажмите кнопку delete или очистите cookie.***
