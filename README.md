# InstagramParserBot // Бот-парсер подписчиков для инстаграма
Проект был разработан по локальному запросу, однако установить и работать с ним самостоятельно тоже имеется возможность 💼

Возможности
===========
Боту требуется указать специальную команду */f* или */followers* с указанием двух аргументов: никнейма и ключевого слова (например, косметолог, если задача искать косметологов)
![уу](https://user-images.githubusercontent.com/52885982/186795153-e8c752cf-86a9-4a8f-8fdf-546c0ae6fd12.jpg)

В процессе отсеиваются аккаунты, номера которых уже имеются в базе (про предварительную настройку см. ниже)    
![e](https://user-images.githubusercontent.com/52885982/186795281-16bb418d-8055-498d-a7f5-02f104df82ef.jpg)

🔷 *Открыть аккаунт через инстаграм* - перейти по ссылке к оригинальному аккаунту

🔷 *1-5* - внести корректировки в никнейм, полное имя, номера или город

🔷 *Вернуться к предыдущему/Перейти к следующему* - пролистывание списка вперед или назад соотвественно

🔷 *Удалить аккаунт из списка* - удалить аккаунт, если не подошел по каким-либо критериям

🔷 *Вывести краткий список аккаунтов* - изменяет текущее сообщение с кратким списком всего списка, в списке указаны номера аккаунтов, благодаря которым можно мгновенно перейти к ним, не используя кнопки вперед-назад

🔷 *Создать документ* - получить выходные данные в виде Word-документа (.docx)

### Пример выходных данных    
![word](https://user-images.githubusercontent.com/52885982/186796119-cff29162-d771-470e-b289-d895540fd36b.jpg)


Предварительная настройка
===========
Бот использует json-файл для реализации всех ключевых нужд: телеграм-токен, данные от инстаграм аккаунта, данные для прокси, база номеров телефонов, ключевые слова    
> Для работы с API Инстаграма требуется входить через аккаунт, это может быть так и собственный, так и отдельно подготовленный. Второе более желательный вариант, так как в случае подозрительных действий Инстаграм может наложить блокировку    

> Номера телефонов указываются в файле **database.xlsx$user_data**!!  Первым столбцом идет юзернейм, затем номер     

Остальная настройка производится в файле **appsettings.json**    

```json
{
    "BotSettings": {
        "Token": "insert-your-token-here",  // телеграм токен, достается через BotFather
        "UserName": "",                     // логин от инстаграм аккаунта
        "UserPassword": "",                 // пароль от инстаграм аккаунта
        "ProxyHost": "",                    // адрес от прокси (http)
        "ProxyPort": "",                    // порт от прокси
        "ProxyUserName": "",                // логин для доступа к прокси, если имеется
        "ProxyUserPassword": "",            // пароль для доступа к прокси, если имеется
        "KeyWords": [                       // ключевые слова как дополнительные критерии для поиска требуемых подписчиков
            "enter", "some", "words", "here"
        ]
    }
```
> Если прокси не используется, данные требуется оставить пустыми    

Небольшие бонусы
===========
#### ✅ Перевод городов
В проекте находится Excel-файл с большей частью городов РФ на русском и английском языке, при желании, базу можно и пополнить    

#### ✅ Автоматическое пополнение базы номеров
Совершается после вызова отправки Word-документа, тем самым не позволяя попасть на одни и те же аккаунты    