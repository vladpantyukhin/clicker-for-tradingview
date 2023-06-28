# Автоимпорт торговых инструментов TradingView

С помощью этой инструкции можно добавить список торговых инстументов в Watchlist. Данный способ не подходит для огромных рынков по типу США. Берите рынки поменьше. Например, добавление обыкновенных акций России заняло не более 15 минут.

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
window.addEventListener("wheel", function () {
  isPaused = true;
  clearTimeout(timer);
  timer = window.setTimeout(function () {
    isPaused = false;
  }, 1000);
});
window.setInterval(function () {
  if (!isPaused) {
    const scrollContainer = document.evaluate(
      '//*[@id="overlap-manager-root"]/div/div/div[2]/div/div[5]/div',
      document,
      null,
      XPathResult.FIRST_ORDERED_NODE_TYPE,
      null
    ).singleNodeValue;
    if (scrollContainer) {
      scrollContainer.scrollTop = scrollContainer.scrollHeight;
    }
  }
}, 500);
```

Ожидаем, пока не перестанет крутиться индикатор загрузки. Переходим к шагу 3.

**Шаг 3**

Добавление инстументов.

Скопируйте код ниже и вставьте в Console, нажмите Enter

```sh
(() => {
  let delay = 0;
  const stock = document.querySelectorAll("span.apply-common-tooltip");
  stock.forEach((stock) => {
    setTimeout(() => {
      stock.click();
    }, delay);
    delay += 1000;
  });
})();
```

Скрипт будет работать до тех пор, пока не добавит все инструменты.
Индикатором завершения можно считать появление Х на последнем инструменте:

![Step3](https://github.com/vladpantyukhin/clicker-for-tradingview/blob/main/screenshots/step3.jpg)

**Поблагодарить автора монетой [КЛАЦ](https://pay.cloudtips.ru/p/6bacb6ea)**
