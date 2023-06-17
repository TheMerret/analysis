# Network

## Профиль загрузки ресурсов

Можно найти [здесь](https://disk.yandex.ru/d/Ns1thwluGP3jnw)

## Неоптимальные места

### Дублирование ресурсов

- bootstrap.bundle.min.js, bootstrap.min.css, bootstrap.min.js
  ![bootstrap.bundle.min.js, bootstrap.min.css, bootstrap.min.js](image.png)

- code.js
  ![code.js](image-1.png)

- data:image/png;base...
  ![Alt text](image-2.png)

- fontawesome-webfont.woff2?v=4.7.0
  ![Alt text](image-3.png)

- jquery-3.5.1.js
  ![Alt text](image-4.png)

- openapi.js
  ![Alt text](image-5.png)

- ph_gd...php
  ![Alt text](image-6.png)

- photoFileName (хотя другие кэшированы)
  ![Alt text](image-7.png)

- popper.min.js
  ![Alt text](image-8.png)

- proximanova-bold-webfont, proximanova-regular-webfont.woff2, proximanova-semibold-webfont
  ![Alt text](image-9.png)

- system_gd-logo
  ![Alt text](image-10.png)

### Лишний размер ресурса

- 9039-finansovyy-kontrol. Используется лишь на 50% судя по Coverage. Много закомментированного кода, ненужного форматирования (доп байты). Можно вынести неиспользуемый код в отдельные js/css файлы и загружать по необходимости.
  ![Alt text](image-11.png)
  ![Alt text](image-12.png)

- context.js. Используется лишь 54% из 316 kB (91 kB gzip), что достаточно большой размер.
  ![Alt text](image-13.png)

- partner core bundles. Сторонний код, используется ли 3% из 647 kB. Предполагая, что стоит отказаться от данного ресурса из за крайне маленькой эффективности.
  ![Alt text](image-14.png).

- common_frontend.css. 86% не используется при большом размере, нужно вынести первично неиспользуемые стили в отдельные файлы.
  ![Alt text](image-15.png)

- Аналогично вышеописанному для ресурсов ниже.
  ![Alt text](image-16.png)

- Шрифт FontAwesome. Единственное место, где используется этот шрифт, представлено на скриншотах ниже. Сам шрифт весит 77 kB при загрузке. То есть бесполезная трата трафика.
  ![Alt text](image-17.png)
  ![Alt text](image-18.png)
  ![Alt text](image-19.png)

- Шрифт ProximaNova. Используется в единственной кнопке регистрации/логина. Шрифт весит около 30 kB.
  ![Alt text](image-21.png)
  ![Alt text](image-22.png)
  ![Alt text](image-23.png)

### Медленно загружающиеся ресурсы

Ресурсы загружающиеся дольше, чем сама страница (9039-finansovyy-kontrol), признаны медленными.
![Alt text](image-20.png)
![Alt text](image-24.png)
![Alt text](image-25.png)

### Ресурсы, блокирующие загрузку

- Файлы стилей в header, загружающиеся через link.
  ![Alt text](image-26.png)
  ![Alt text](image-27.png)

- Скрипты, загружающиеся в header через тег script, имеют большой приоритет и мешают браузеру рендерить контент. Можно их перенести в конец body. Ниже представлены примеры скриптов и их обращения во внешние ресурсы.
  ![Alt text](image-28.png)
  ![Alt text](image-29.png)

- Виджеты от сторонних поставщиков, заставляющие пользователя ждать рендеринг
  ![Alt text](image-30.png)

- Lighthouse не заподозрил никаких потенциальных ресурсов, мешающих рендерингу. Хотя можно было вынести view.js в конец body.
  ![Alt text](image-31.png)
  ![Alt text](image-32.png)

### Что-то ещё

- CORS Error
  ![Alt text](image-33.png)

- Лениво загружать embed'ы
  ![Alt text](image-34.png)

- Кэшировать сторонние ресурсы. Например, виджеты от вк.
  ![Alt text](image-35.png)
  ![Alt text](image-36.png)

- Кнопки как изображения вместо использования css.
  ![Alt text](image-37.png)

- Огромные payload. Например для вк.
  ![Alt text](image-38.png)

# Slow

## Профиль загрузки ресурсов

Можно найти [здесь](https://disk.yandex.ru/d/c1jSb9kzbnyz-A)

## Неоптимальные места

Показало те же результаты, что и при обычном тестировании. См. [выше](#неоптимальные-места)
