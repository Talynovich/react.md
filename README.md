## Запуск React-проекта на Джино.Хостинге

Для запуска React-приложения вам понадобится подключённая услуга **Поддержка веб-приложений**.  
После её подключения в разделе <j-path>Управление / Настройки веб-сервера</j-path> контрольной панели выберите для нужного вам домена необходимую версию Node.js.
Подключитесь к хостинг-контейнеру через SSH или используйте web-консоль для выполнения команд - оба способа равнозначны. Чтобы открыть web-консоль пройдите в панель управления на хостинге в раздел <j-path>Управление / Консоль</j-path>.
Перейдите в каталог домена на хостинге. Для этого используйте команду

```sh
cd domains/example.ru
```

Где `example.ru` замените на название вашего домена. После выполнения этого шага появится следующее сообщение:

```sh
direnv: loading ~/domains/example.ru/.envrc
direnv: export +CPATH +LD_LIBRARY_PATH +LIBRARY_PATH +PKG_CONFIG_PATH ~MANPATH ~PATH
```

Это сообщение свидетельствует о создании окружения с выбранной для домена версией Node.js.

Для создания проекта введите команду `npx create-react-app myapp`, где "myapp" может быть заменено на название вашего проекта. После завершения создания проекта вы увидите следующее сообщение:

```sh
We suggest that you begin by typing:

  cd myapp
  npm start

Happy hacking!
```

Создание проекта завершено успешно!

В папке с названием вашего домена будут расположены три каталога и один файл:

**myapp** - каталог проекта, созданный ранее. 

**tmp** - каталог для временных файлов.

Файл **.envrc** является системным и необходим для указания пути до интерпретатора в консоли хостинга.

Далее перейдите в каталог **myapp** используя команду `cd myapp`.
Запустите сборку проекта с помощью команды `npm run build`. После успешного завершения сборки вы увидите сообщение:

```sh
Compiled successfully.

File sizes after gzip:

  46.62 kB  build/static/js/main.c5794881.js
  1.78 kB   build/static/js/453.64512fd7.chunk.js
  515 B     build/static/css/main.f855e6bc.css

The project was built assuming it is hosted at /.
You can control this with the homepage field in your package.json.

The build folder is ready to be deployed.
You may serve it with a static server:

  npm install -g serve
  serve -s build

Find out more about deployment here:

  https://cra.link/deployment
```

В папке проекта **myapp** будет создан каталог **build**, в котором содержатся результаты сборки проекта.

Теперь нам нужно скопировать файлы из каталога **build** в наш каталог **public_html** в корневом каталоге домена. Для этого введите команду

```sh
cp -r ~/domains/example.ru/myapp/build/* ~/domains/example.ru/public_html/
```

Где `example.ru` замените на название вашего домена. После чего проверьте работу проекта по URL http://example.ru/
