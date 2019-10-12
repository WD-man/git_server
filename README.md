# Node js сервер для shri_arcanum

Скачайте и установите зависимости

При разработке использовлась

Node.js версии __12.6.0__

## В данный момент актуальная ветка __typescript__
Проблемы с домашкой были связаны с использованием тестового репозитория  
внутри работчего. При исполнении git команд для получения данных,  
несмотря на передачу прямого пути, бралась верхняя директория гита.  
Из за этого все падало, так как данные были невалидны.

__info__  
В качестве папки для хранения репозиториев берется папка на уровень выше текущей.  
В репозитории фронта есть инструкции для добавления и удаления тестового репозитория.

#### Запуск Production версии

`npm run start`

#### Запуск Development версии

`npm run dev`

__Чтобы при запуске передать директорию хранения репозиториев передайте путь через аргумент:__

`node src/server.js --dir='$path'`

__Где $path это абсолютный путь к нужной директории__


По умолчанию запускается на порту __8076__

Можно поменять, передав параметр при запуске
`PORT=$port npm run start` или в dev режиме  
`PORT=$port npm run dev`

Где $port номер порта

Роуты:

__/__ - Получение списка всех установленных git репозиториев

**POST**  __/:repositoryId__ - установка нового репозитория

**DELETE**  __/:repositoryId__ - адаление существующего репозитория

__/:repositoryId/commits/:commitHash__ - получение списка коммитов

__/:repositoryId/commits/:commitHash/diff__ = получение diff коммита

__/:repositoryId/tree/:commitHash?/:pathFromUrl*?__ - получение содержимого директории (по умолчанию корневой)

__/:repositoryId/blob/:commitHash/:pathToFile*__ - получение содержимого файла


### Тесты

**Блоки**

- Сервер
- Хэндлеры роутов

Изначально функция получения содержимого файла была непригодна для тестирования  
из за смешения логики роутинга и получения файла. Для тестов был проведен рефакторинг.


Юнит тесты написаны для нескольких хээндлеров роутов. 
В данный момент больше не успел.
