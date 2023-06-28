# Auto import of trading instruments TradingView

Using this instruction, you can add a list of trading instruments to the Watchlist. This method is not suitable for huge markets like the USA. Take smaller markets. For example, the addition of ordinary shares of Russia took no more than 15 minutes.

**Step 1**

Configuring tool loading.

- Click + on the Watchlist panel
- In the window that appears, select the tool options

  ![Step1](https://github.com/vladpantyukhin/clicker-for-tradingview/blob/main/screenshots/step1.jpg)

**Step 2**

Loading tools.

- Open the Developer panel by pressing F12 (Google Chrome)
  or right-click, then "View the code of the page or element"
- Select the Console tab

  ![Step2](https://github.com/vladpantyukhin/clicker-for-tradingview/blob/main/screenshots/step2.jpg)

- Copy the code below and paste it into the Console, press Enter

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

We wait until the loading indicator stops spinning. Go to step 3.

**Step 3**

Adding tools.

Copy the code below and paste it into the Console, press Enter

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

The script will run until it adds all the tools.
The indicator of completion can be considered the appearance of X on the last instrument:

![Step3](https://github.com/vladpantyukhin/clicker-for-tradingview/blob/main/screenshots/step3.jpg)

**Thank the author with a coin [CLACK](https://pay.cloudtips.ru/p/6bacb6ea)**
