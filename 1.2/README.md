# Домашнее задание к занятию 1.2 	JSON. Codable. Модели данных

## Правила выполнения домашней работы:
* За основу домашнего задания мы берем версию VK-проекта `Navigation` в рабочей ветке на Github. 
От локальной версии удаленной базовой ветки создайте новую ветку для ДЗ: `git checkout -b <название новой ветки>`. 
После окончания работы над ДЗ необходимо запушить ветку в origin.
* В поле для сдачи работы прикрепите ссылку на новый пулл реквест
* Любые вопросы по решению задач задавайте в чате учебной группы.


## Задание 1:

[URL 1](https://jsonplaceholder.typicode.com/todos/ {любой номер на ваше усмотрение})

- Создайте модель данных на базе JSON
- Запустите `URLSessionDataTask` 
- С помощью `JSONSerialization` инициализируйте объект в `do try catch` блоке. Используйте метод `jsonObject(with data: Data, options opt: JSONSerialization.ReadingOptions = [])`.

- В дополнительно созданной `UILabel` на `InfoViewController` отобразите значение поля `title`

## Задание 2:

[URL 2](https://swapi.dev/api/planets/1)

- Создайте модель данных планеты на базе JSON, соответствующую протоколу `Decodable` 
- Запустите `URLSessionDataTask` 
- С помощью `JSONDecoder` инициализируйте объект с типом модели. Используйте метод `decode<T: Decodable>(_ type: T.Type, from: Data)`.
- В дополнительно созданной `UILabel` на `InfoViewController` отобразите период обращения планеты Татуин вокруг своей звезды (orbital_period)
- Подсказка: в этой задаче пригодится `enum CodingKeys` 

## Задание 3* (с большой звездочкой):

[URL тот же](https://swapi.dev/api/planets/1)

- Создайте модель данных планеты на базе JSON, соответствующую протоколу `Decodable` 
- Запустите `URLSessionDataTask` 
- С помощью `JSONDecoder` инициализируйте вашу модель данных
- В дополнительно созданной `UITableView` на `InfoViewController` отобразите имена всех жителей планеты Татуин
- Для этого вам потребуется отключить SSL с помощью ключа в `Info.plist`: 
Dictionary: App Transport Security Settings
ключ: Allow Arbitrary Loads, значение: YES
- после чего создайте модель данных для JSON по адресу жителя планеты с 1 полем - `name` 
- запустите для каждого URL жителя Татуина `URLSessionDataTask`
- инициализируйте модели данных жителей и сохраните их, к примеру, в `Array` 
- `.reloadData()`
