# Автоимпорт торговых инструментов TradingView

С помощью этой инструкции можно добавить список торговых инстументов в ваш Watchlist.

**Шаг 1**

Настройка загрузки инструментов.

- Нажмите + на панели Watchlist
- В появившемся окне выберите параметры инструментов

  ![Step1](https://github.com/vladpantyukhin/clicker-for-tradingview/blob/main/screenshots/step1.jpg)

**Шаг 2**

Загрузка инструментов.

- Откройте панель разработчика нажав F12 (Google Chrome)
  или правый клик мыши, далее "Посмотреть код страницы или элемента"
- Выберите вкладку Console

  ![Step2](https://github.com/vladpantyukhin/clicker-for-tradingview/blob/main/screenshots/step2.jpg)

- Скопируйте код ниже и вставьте в Console, нажмите Enter

```sh
let timer;
let isPaused = false;
$(window).on("wheel", function () {
  isPaused = true;
  clearTimeout(timer);
  timer = window.setTimeout(function () {
    isPaused = false;
  }, 1000);
});
window.setInterval(function () {
  if (!isPaused) {
    $("div.scrollContainer-vWG52QBW").scrollTop(
      $("div.scrollContainer-vWG52QBW")[0].scrollHeight
    );
  }
}, 500);
```

Скрипт будет работать до тех пор, пока не закончатся выбранные инструменты. Сайт можно свернуть и делать свои дела.

**Шаг 3**

Добавление инстументов.

Важно! Если ваше рабочее устройство слабое, измените в коде

`delay += 200 на delay += 600`

Скопируйте код ниже и вставьте в Console, нажмите Enter

```sh
(() => {
  let delay = 0;
  const stock = document.querySelectorAll("span.button-W4RYPlVi");
  stock.forEach((stock) => {
    setTimeout(() => {
      stock.click();
    }, delay);
    delay += 200;
  });
})();
```

Скрипт будет работать до тех пор, пока не добавит все инструменты.

Индикатором завершения можно считать появление Х на последнем инструменте:

![Step3](https://github.com/vladpantyukhin/clicker-for-tradingview/blob/main/screenshots/step3.jpg)

Поблагодарить автора монетой **[КЛАЦ](https://pay.cloudtips.ru/p/6bacb6ea)**
