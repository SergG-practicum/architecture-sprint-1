Задание 1.

Для разбиения проекта на микрофронтенды я решил использовать Webpack Module Federation. В проекте используется только React и нет необходимости давать возможность подключать другие фреймворки. Плюс он лучше описан в уроке и, как мне показалось, более простой в настройке.

Я выделил 4 микрофронтенда: common, auth, profile, places.

common -- общие элементы страницы
```
/src
  /blocks
    /footer
      footer.css            // Стили для футера
    /header
      header.css            // Стили для хедера
  /components
    Footer.js               // Компонент футер
    Header.js               // Компонент хедер
    ProtectedRoute.js       // Компонент редиректа на логин
  App.jsx                   // Логика модуля
  index.css                 // Подключение стилей из blocks
  index.html
  index.js                  // Точка входа микрофронтенда
compilation.config.js
package.json                // Зависимости и скрипты микрофронтенда
webpack.config.js
```

auth -- логин и регистрация
```
/src
  /blocks
    /auth-form
      auth-form.css         // Стили для элементов формы
    /popup
      popup.css             // Стили для всплывающего окна
  /components
    InfoTooltip.js          // Компонент с инфой о результате входа/регистрации
    Login.js                // Компонент входа пользователя
    Register.js             // Компонент регистрации пользователя
  /utils
    auth.js                 // API входа/регистрации
  App.jsx                   // Логика модуля
  index.css                 // Подключение стилей из blocks
  index.html
  index.js                  // Точка входа микрофронтенда
compilation.config.js
package.json                // Зависимости и скрипты микрофронтенда
webpack.config.js
```

profile -- работа с профилем пользователя
```
/src
  /blocks
    /popup
      popup.css             // Стили для всплывающего окна
    /profile
      profile.css           // Стили отображения профиля пользователя
  /components
    EditAvatarPopup.js      // Компонент смены аватарки
    EditProfilePopup.js     // Компонент редактирования профиля пользователя
    MainProfile.js          // Компонент отображения профиля пользователя
    PopupWithForm.js        // Компонент всплывающего окна с формой
  /utils
    api.js                  // API редактирования профиля пользователя
  App.jsx                   // Логика модуля
  index.css                 // Подключение стилей из blocks
  index.html
  index.js                  // Точка входа микрофронтенда
compilation.config.js
package.json                // Зависимости и скрипты микрофронтенда
webpack.config.js
```

places -- работа с фотками, лайки
```
/src
  /blocks
    /card
      card.css              // Стили компонента с фоткой
    /places
      places.css            // Стили компонента со списком фоток
    /popup
      popup.css             // Стили для всплывающего окна
  /components
    AddPlacePopup.js        // Компонент с добавлением фотки
    Card.js                 // Компонент с фоткой
    ImagePopup.js           // Компонент для всплывающего окна с фоткой
    MainCards.js            // Компонент со списком фоток
    PopupWithForm.js        // Компонент всплывающего окна с формой
  /utils
    api.js                  // API для работы с фотками и лайками
  App.jsx                   // Логика модуля
  index.css                 // Подключение стилей из blocks
  index.html
  index.js                  // Точка входа микрофронтенда
compilation.config.js
package.json                // Зависимости и скрипты микрофронтенда
webpack.config.js
```

host -- основное приложение
```
/src
  /blocks
    /content
      content.css           // Общие стили контента
    /page
      page.css              // Общие стили страницы
  /vendor                   // Нормализация стилей, шрифты
  App.jsx                   // Логика модуля
  index.css                 // Подключение стилей из blocks
  index.html
  index.js                  // Точка входа в основное приложение
compilation.config.js
package.json                // Зависимости и скрипты микрофронтенда
webpack.config.js
```

Исходный компонент Main.js я разделил на два, отдельно список фоток и отдельно отображение пользователя, они пошли в разные микрофронтенды. Компонент PopupWithForm.js продублировал в микрофронтендах profile и places, чтобы сохранить принцип вертикальной нарезки.

Для запуска приложения нужно сначала запустить микрофронтенды, а затем основное приложение host.


Задание 2.

Первоначальная схема:

https://github.com/SergG-practicum/architecture-draw-io/blob/main/arch_SergG_sprint1_task2.drawio

Схема с исправлением замечаний по ревью:

https://github.com/SergG-practicum/architecture-draw-io/blob/main/arch_SergG_sprint1_task2_fix_after_review.drawio
