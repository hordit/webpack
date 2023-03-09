# webpack

--> npm init -y  устанавливаем пакет package.json ;

--> npm install webpack webpack-cli --save-dev  устанавливаем интерфейс командной строки для терминала webpack-cli, они доступны не глобально, а из наших npm скриптов ;

-->  |- /src               - создаем папку src c ->
        |- /index.js       - корневым index.js   
     |- index.html         - создаем главный index.html ;
     |- package.json
     |- package-lock.json
     
--> автоматически потом после создания конфигураций будет создан бандлер |- /dist
           |- /index.html ;

--> создаем отдельный фаил с конфигурациями(в виде обьекта мы будем записывать настройки) для всех файлов webpack.config.js , потом мы их экспортируем в виде :

const path = require('path'); - это импорт встроеного модуля node.js(встроеная библеотека с путями в файловой системе)

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',     - имя файла бандла
    path: path.resolve(__dirname, 'dist'), - абсолютный путь к вашей папке на системе в имя которую нужно выкинуть
  },
} ;

--> создаем NPM Scripts в packege.json
       "scripts": {
        "build": "webpack"
       } - вместо него можно сделать так :
       "scripts": {
          "dev": "webpack --mode=development",
          "prod": "webpack --mode=production"
        },

--> npm run build - билдит написаный код в модулях(hash - уникальный индифекатор сборки) ;

--> "mode": 'production' - этот минифицирует код, в конфигурациях не нужно для разработки(потому что 'development' не минифицирует);

--> устанавливаем DevServer это как лайфсервер, это сервер который раздает ваши файлики , вашу статику(index.html, index.js и т.д.) под капотом, и перезагружает страницу каждый раз, когда вы делаете како-ето изменение в исходном файле;

npm install --save-dev webpack webpack-dev-server

замени :

"scripts": {
    "dev": "webpack-dev-server --mode=development",
    "prod": "webpack --mode=production"
  },

--> 
