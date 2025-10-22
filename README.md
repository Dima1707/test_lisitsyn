Задача 1
<img width="1624" height="812" alt="BPMN Заявки" src="https://github.com/user-attachments/assets/d7953ca1-1857-465f-b3af-84dced5477b1" />
Задача 2

User Story : Я как пользователя, хочу добавить свой товар в личный кабинет, чтобы продавать его другим пользователям


Use Case 

Акторы: Пользоваетель(владелец ЛК маркетплейса), Система маркетплейса(обрабатывает запросы)

1 Пользователь переходит в личный кабинет,

2 Система переводит его в ЛК,

3 Пользователь нажимает на кнопку “Товары”,

4 Система переводит его на страницу с товарами продавца,

5 Пользователь нажимает кнопку “Опубликовать”,

6 Система переводит на страницу с добавлением товара,

7 Пользователь вводит данные о товаре ,добавляет фото и нажимает “Опубликовать”,

8 Система проверяет валидность данных и если все правильно, публикует товар и обновляет витрину продавца,

9 Пользователь получает уведомление, что товар удачно опубликован,

10Пользователь видит товар у себя на витрине.

Альтернатинвные шаги

5.1 Система не может обработать запрос, превышен лимит запросов и ошибка 500

8.1 Валидация не прошла(неверный формат фото, или слишком много символов в строке) 

Задача 3

Задача 3.1

![Api описание](https://github.com/user-attachments/assets/acce06d5-68c3-47bb-9a91-a2e8682e7377)

![Ограничения API](https://github.com/user-attachments/assets/2dbb0ac6-9d9d-45c3-aea8-bbfbecd888e7)

![Успешные ответы](https://github.com/user-attachments/assets/03dad6cb-a362-4484-a559-33a96fbae1cb)

![Коды ошибок](https://github.com/user-attachments/assets/30f02cd3-8b83-4f16-b792-e7c094210a2c)

Задача 3.2

@startuml
actor client
participant RegistrationService


client ->> RegistrationService: POST/registration
RegistrationService -> RegistrationService: Валидация данных
alt Если данные валидны
    RegistrationService --> client: 201 Ok
    note right: Пользователь удачно создан
else Данные не валидны
    RegistrationService --> client: 400
    note right: Неверные данные(Пароль должен минимум состоять из 8 символов)
else Такой пользователь существует
    RegistrationService --> client: 409
    note right: Пользователь с такими данными существует(email,nikname)
else Ошибка сервера
    RegistrationService --> client: 500
    note right: Сервис недоступен(сервер перегружен)
end
@enduml

![Без имени](https://github.com/user-attachments/assets/bcc968e4-f253-4fb2-8d0e-8589af07405e)
