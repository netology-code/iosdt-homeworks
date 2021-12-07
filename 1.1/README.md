# Домашнее задание к занятию 1.1 	URLSession. URLSessionDataTask

## Правила выполнения домашней работы:
* За основу домашнего задания мы берем итоговую версию VK-проекта `Navigation` в рабочей ветке на Github. 
От локальной версии удаленной базовой ветки создайте новую ветку для ДЗ: `git checkout -b <название новой ветки>`. После окончания работы над ДЗ необходимо запушить ветку в origin.
* В поле для сдачи работы прикрепите ссылку на ваш проект в Git.
* Любые вопросы по решению задач задавайте в чате учебной группы.


## Задание:

1. Создайте сетевой сервис, типа `struct NetworkManager` или `struct NetworkService`. В `NetworkService` пока будет только 1 метод, он будет запускать `URLSessionDataTask` для определенного URL.
2. Дополнительно создайте `enum AppConfiguration`, в нем будут 3 case с ассоциированными значениями типа URL или String, на ваше усмотрение.
3.  При загрузке приложения в `AppDelegate` рандомно инициализируйте свойство `appConfiguration: AppConfiguration` в методе `didFinish...`.
4.  Для инициализации кейсов `appConfiguration` используйте любые 3 URL из открытого API: `https://swapi.dev/api/`. 

Примеры String для URL: 
* "https://swapi.dev/api/people/8"
* "https://swapi.dev/api/starships/3"
* "https://swapi.dev/api/planets/5"

- после инициализации свойства `appConfiguration` его значение передается в (лучше `static func...`) метод сетевого сервиса (см. пункт первый).
- метод вынимает из appConfiguration ассоциированное значение String или сразу URL и отправляет запрос (типа `URLSessionDataTask`) к API.

5. С помощью команды `print` выведите результат:

A. data - в доступном для понимания виде, то есть `String` в стандартной кодировке

B. свойство `.allHeaderFields` и `.statusCode` у `response`

C. попробуйте выключить интернет (WiFi у ноутбука) и запустить приложение - распечатайте `error.localizedDescription` или `error.debugDescription`
Код ошибки, который пришел при выключенном интернете, укажите в комментарии, пожалуйста.
