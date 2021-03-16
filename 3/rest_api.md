# Домашнее задание к занятию 1.3 	REST API. HTTPs

## Правила выполнения домашней работы:
* За основу домашнего задания мы берем версию VK-проекта `Navigation` в рабочей ветке на Github. 
От локальной версии удаленной базовой ветки создайте новую ветку для ДЗ: `git checkout -b <название новой ветки>`. 
После окончания работы над ДЗ необходимо запушить ветку в origin.
* В поле для сдачи работы прикрепите ссылку на новый пулл реквест
* Любые вопросы по решению задач задавайте в чате Slack.

## Предварительная подготовка:
Взять за основу проект Navigation с LoginViewController. 
Подойдут ДЗ к лекции 3 (Паттерны и архитектура), 4 (MVVM + координаторы) и далее. 
Основное предварительное условие: готовый `LoginViewController`

## Задача: 

1. свой проект Firebase создать  [Firebase](https://firebase.google.com/docs/ios/setup?authuser=0)
2. Bundle.id -> прописать в консоли Firebase 
3. Firebase .plist -> скачать из консоли и добавить в файлы приложения 
4. установить Firebase/Core, Firebase/Auth через [CocoaPods](https://cocoapods.org)
5. подключить Firebase/Auth к LoginViewController 
https://firebase.google.com/docs/auth/ios/start?authuser=0

### Сценарии "Регистрация" и "Вход" 

1. Перед тем, как писать код, проработать сценарии: 
   a) юзер вводит email / пароль, которых еще в БД нет - зарегистрировать нового юзера
   b) юзер пытается войти без регистрации, с пустыми полями ввода (может быть кнопке `Login` сделать ***disable?***) - напомнить о том, что надо ввести email и пароль
   c) юзер нажимает кнопку "Login" с частично/неверно заполненными полями ввода - выдать ошибку или зарегистрировать нового юзера
   d) юзер вводит email / пароль, которые уже существуют в базе - успешный логин
2. Сопоставьте сценарии с методами Firebase API: надо ли расписывать все сценарии или просто обработать ошибку в методе 
3. раньше у нас был синглтон Checker, теперь вариантов 2: 
LoginInspector передается в роли ViewModel (или как extension от ViewModel) к LoginViewController. Тогда взаимодействие у него будет с LoginViewController через замыкания.
LoginInspector взаимодействует с LoginViewController через протокол делегата LoginViewControllerDelegate. 
В любом случае, в своем(их) методе(ах) проверки логина и пароля LoginInspector будет вызывать методы Firebase/Auth

### Что пригодится: 

`FirebaseAuth.Auth.auth().currentUser` - проверка на `nil`
`FirebaseAuth.Auth.auth().createUser(withEmail:, password:, completion:)`
`FirebaseAuth.Auth.auth().signIn(withEmail:, password:, completion:)`
`FirebaseAuth.Auth.auth().signOut() throws`
