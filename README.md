# JS-LightBox-RWD

![image](https://img.shields.io/badge/JavaScript-exercise-brightgreen.svg)
![image](https://img.shields.io/badge/SASS-exercise-ff69b4.svg)
![image](https://img.shields.io/badge/RWD-exercise-blue.svg)

![images](https://github.com/jedchang/JS-LightBox/blob/master/preview.jpg)

## 定義資料

- `let imgPath = 'images'` 圖片路徑。
- `let linkPath = 'images/large'` 點擊後連結圖片路徑。
- `let currentIndex = 1` 當前索引。
- `data-*` 紀錄圖片位置。

## 圖片處理

判斷點擊對象為圖片，利用點選後，動態生成 DOM 並替換原有連結改變圖片。
使用 `data-num`，改變當前圖片索引。

```javascript
function modalHandler(e) {
  e.preventDefault();

  if (e.target.nodeName == 'IMG') {
    overlay.style.display = 'block';
    modalBox.style.display = 'flex';
    console.log('IMG');

    let num = Number(e.target.dataset.num);
    currentIndex = num;
    currentNum.textContent = num;

    let largePic = `<img src="${linkPath}/pic-${currentIndex}.jpg" alt="" class="large-pic">`;
    picAll.innerHTML = largePic;
  }
}
```

## 頁面切換

- 下一頁按鈕，當前索引累加。假設當前索引大於所有圖片數量，，表示最後一張，則當前索引設定為 1 ，執行改變圖片函式。
- 上一頁按鈕，當前索引累減。假設當前索引小於 1 ，表示第一張，則當前索引設定為所有圖片數量，執行改變圖片函式。

```javascript
function nextHandler(e) {
  e.preventDefault();
  currentIndex++;
  currentNum.textContent = currentIndex;
  if (currentIndex > li.length) {
    currentIndex = 1;
    currentNum.textContent = currentIndex;
  }
  changeImg();
}

function prevHandler(e) {
  e.preventDefault();
  currentIndex--;
  currentNum.textContent = currentIndex;
  if (currentIndex < 1) {
    currentIndex = li.length;
    currentNum.textContent = currentIndex;
  }
  changeImg();
}
```
