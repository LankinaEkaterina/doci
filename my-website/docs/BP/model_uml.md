---
title: UML
sidebar_position: 2
---

:::note
Use-case и сценарий
:::

### Диаграмма вариантов использования на языке UML:

```plantuml

@startuml

actor Организатор as a
actor Участник as b

usecase "Создать мероприятие" as UC1
usecase "Редактировать мероприятие" as UC2
usecase "Удалить мероприятие" as UC3
usecase "Зарегистрироваться на мероприятие" as UC4
usecase "Отменить регистрацию на мероприятие" as UC5
usecase "Просмотр ленты мероприятий" as UC6
usecase "Просмотр карточки мероприятия" as UC7
usecase "Поиск мероприятия" as UC8
usecase "Создать личный кабинет" as UC9
usecase "Редактировать личный кабинет" as UC10
usecase "Удалить личный кабинет" as UC11
usecase "Просмотр истории созданных / посещенных мероприятий" as UC12
usecase "Просмотр календаря мероприятий" as UC13

a -- UC1
UC1 <.. UC2: extend
UC1 <.. UC3: extend

b <|-- a

b -- UC4
UC4 <.. UC5: extend

b -- UC6
b -- UC7
b -- UC8
b -- UC9

UC9 <.. UC10: extend
UC9 <.. UC11: extend
UC9 <.. UC12: extend
UC9 <.. UC13: extend

@enduml

```

### Диаграмма последовательности на языке UML:
Диаграмма последовательности для Use-case Регистрация участника на мероприятие

```plantuml

@startuml

skinparam sequenceMessageAlign center

actor "Авторизованный пользователь (Участник)" as u
participant "Система регистрации на мероприятие" as s
database "База данных" as db

autonumber

u -> s: Переход на страницу мероприятия
activate s
s -> db: Запрос данных о мероприятии
activate db
db -> s: Данные о мероприятии
deactivate db
s -> u: Отображение информации о мероприятии,\nкнопки "Зарегистрироваться" и поля для отметки\n о согласии на обработку персональных данных
deactivate s

u -> s: Нажатие на кнопку "Зарегистрироваться" и\n отметка в поле о персональных данных 
activate s
s -> db: Запись о регистрации пользователя
activate db
db -> s: Подтверждение об успешной записи
deactivate db
s -> u: Сообщение об успешной записи на мероприятие
deactivate s

@enduml

```