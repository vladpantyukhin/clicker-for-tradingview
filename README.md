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
