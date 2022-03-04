## Day 01 - JavaScript Drum Kit
### 目標
  - 當按下 A,S,D,F,G,H,J,K,L 任一鍵之後
    - 播放相應的 audio 檔案
    - 畫面上的按鍵 (div) 添加觸發的動畫 (採用加上/移除class的方式)
### 技術要點
  - keydown event
    - property: keyCode 可用來判斷按下哪顆按鍵
  - transitionend event
    - 需注意 css 是否設定為 transition all
  - data-* attribute 的選取
    - js 中可使用 .key[data-key=35] 來選取
  - Array.from
    - 可將 querySelectAll 取回的nodelist轉為陣列
    - 用法為 Array.from(document.querySelectorAll('.key'))
  - audio tag
    - property: currentTime (若要從頭播放則需設定為0，不會自動重播)
    - method: play() (播放 audio 的方法)
### 實作要領
  - 事件綁定後，可指派一變數作為每次觸發事件的對象
  - 透過比對觸發事件對象(e)與 DOM elements 相同的 key 值，可以將 audio, div 等 DOM 元素關聯在一起

### 觀念釐清
  - DOM level tree: **Window (瀏覽器視窗本身)** > Document > HTML ...
  - ![DOM Level](https://www.w3schools.com/js/pic_htmltree.gif)
  - 事件綁定可視為 **作用域.addEventListener("事件名稱", 透過此事件要做到的事)**
  - 綁定事件至 window 表示這個事件的作用域是在整個 window (browser) 底下
  - e 和 this 的區別，e => event Object; this => DOM object

### 疑問
  - Window, Document 及 HTML 有何不同?
    - Window 為 BOM 中最上層的物件(或稱Level 0 DOM)，代表著瀏覽器本身
    - Document 為 Window 底下的其中一個節點 (node)，代表著頁面本身
      - 可透過 document instance of Node 證明
    - HTML 為 DOM 中的 root element
  - keydown 事件該綁在 window or document?
    - 需要考慮的面相為 DOM event flow
    - 在 capture phase 綁在 Window 的事件會先執行，Bubbling phase 則相反
    ![DOM Event flow](https://i.stack.imgur.com/uKnhJ.png)
  - 為什麼 transitionEvent 會 fire 兩次?  :
    - 因為 transitionend event 是雙向 fired 的
    - 從初始狀態到 transition 完成 (1次)
    - 從 transitione 狀態回到初始狀態結束 (1次)