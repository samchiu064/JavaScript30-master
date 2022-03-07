## Day 03 - CSS Variables
### 目標
  - 透過JS改變CSS變數
  - 透過change&mousemove事件動態改變input style

### 技術要點
  - :root(html)底下設定變數
  - 設定變數方式 --name: value
  - document.documentElement.setProperty('property name', value) 可用來獲得:root節點並設定css屬性
### 實作要領
  - 先設定 css 變數
  - 註冊 change 及 mousemove 事件
  - 利用 document.documentElement.setProperty 取得跟節點並設定css屬性

### 觀念釐清
  - 需注意如果寫了三行 document.documentElement.style.setProperty 則每個事件會同時發生
  - 改寫為一行 document.documentElement.style.setProperty 就能夠根據 this 的不同而只調整對應屬性
### 疑問
