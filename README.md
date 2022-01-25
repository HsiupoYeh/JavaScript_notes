# JavaScript_notes
JavaScript簡稱JS。

## 函數特色:
  + 宣告函數(使用陳述式):
    + 大部分程式語言用的方法，用「function」關鍵字去宣告這個函數叫什麼、要做什麼事情。
    ```javascript
    // 陳述式宣告一個square的函數(宣告寫在呼叫之前)。
    // 這不會回傳東西，但會在全域出現這個函數可以被使用。
    // 這個宣告不會運行，位置在哪都一樣，當Script被完整載入後就會被宣告到全域中。被稱作「提升」。
    function square(number) {
      let result= number * number;
      return result;
    }
    // 呼叫方式
    let my_answer=square(2);
    console.log(my_answer);
    ```
     ```javascript
     // 呼叫方式
    let my_answer=square(2);
    console.log(my_answer);
    // 陳述式宣告一個square的函數(宣告寫在呼叫之後)。
    // 這不會回傳東西，但會在全域出現這個函數可以被使用。
    // 這個宣告不會運行，位置在哪都一樣，當Script被完整載入後就會被宣告到全域中。被稱作「提升」。
    function square(number) {
      let result= number * number;
      return result;
    }
    
    ```
  + 函數表達式:
    + JS的奇怪建立函數的方法，偏偏比較常用，看起來跟宣告函數超像。 
    ```javascript
    // 表達式宣告一個square的函數。
    // 會回傳物件(使這個函數成為一個物件)。
    // 這個宣告不會運行，宣告部分要寫在呼叫之前。也就是不會被「提升」。
    var my_square = function square(number) {
      return number * number;
    }
    // 呼叫方式
    let my_answer=my_square(2);
    console.log(my_answer);
    ```
    ```javascript
    // 表達式宣告一個square的函數。
    // 會回傳物件(使這個函數成為一個物件)。
    // 這個宣告不會運行，宣告部分要寫在呼叫之前。也就是不會被「提升」。
    // function後面不寫名字叫做匿名函數，通常給名字是讓內部呼叫用的，否則寫了也是白寫。
    var my_square = function (number) {
      return number * number;
    }
    // 呼叫方式
    let my_answer=my_square(2);
    console.log(my_answer);
    ```
    ```javascript
    // 用括號包住代表直接當物件，內部就是表達式宣告。這是有名字的情況。
    // 直接呼叫該函數的方式如下:
    let my_answer=(function square(number) {
      return number * number;
    })(2);
    console.log(my_answer);
    ```
    ```javascript
    // 用括號包住代表直接當物件，內部就是表達式宣告。這是匿名的情況，效果跟有名字一樣，所以很多時候都用匿名函數就足夠了。
    // 直接呼叫該函數的方式如下:
    let my_answer=(function (number) {
      return number * number;
    })(2);
    console.log(my_answer);
    ```
    
  + 匿名函數:
    + JS允許沒有名字的函數。
    + 即使給函數名字但還是用表達式來宣告的話，名字是函數內部使用的，對外部呼叫來說沒屁用。
  
  + 箭頭函數:
    + ES6的新招式。蠻多不太容易記得的規定，但讓程式碼很短。只能多看範例多想原理。
    + 箭頭函數不會被提升，所以也屬於表達式。
    ```javascript
    // 表達式宣告一個square的函數。
    // 會回傳物件(使這個函數成為一個物件)。
    // 這個宣告不會運行，宣告部分要寫在呼叫之前。也就是不會被「提升」。
    // function後面不寫名字叫做匿名函數，通常給名字是讓內部呼叫用的，否則寫了也是白寫。
    var my_square = function (number) {
      return number * number;
    }
    // 呼叫方式
    let my_answer=my_square(2);
    console.log(my_answer);
    ```
    ```javascript
    // 表達式宣告一個square的箭頭函數。
    // 會回傳物件(使這個函數成為一個物件)。
    // 這個宣告不會運行，宣告部分要寫在呼叫之前。也就是不會被「提升」。
    var my_square = (number) => {
      return number * number;
    };

    // 呼叫方式
    let my_answer=my_square(2);
    console.log(my_answer); 
    ```
    

## 運行特色:  
  + Single Thread (單線程)  
  + Synchronous (同步)
    > Javascript 一次只執行一件事，程式會逐行執行 。  
    > 所以普通的程式碼都是同步(阻塞式)的，實現非同步(非阻塞式)的程式碼是依賴運行環境提供的特殊功能。

## 運行環境:
  + 瀏覽器
  + Node.js

## 實際上的狀況
  + 配合運行環境，JS可以撰寫出同步與非同步的程式碼。
  + 非同步的程式碼風格:
    + 舊式的 callback 風格
    + 新式的 promise 風格。本質上，它代表瀏覽器述說著：「我承諾我會盡快給予你一個答覆」，因此名稱就叫做「 promise 」。
