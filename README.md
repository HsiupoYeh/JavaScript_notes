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
    + 大部分狀況下會是取代匿名函數的簡潔寫法，規則是: 物件名稱 = (輸入參數) => {函數工作程式碼}。
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
    ```javascript
    // 用new可以把promise建構出來，自帶3個常用的方法
    const my_Promise = new Promise();

    my_Promise.then();    // Promise 回傳正確
    my_Promise.catch();   // Promise 回傳失敗
    my_Promise.finally(); // 非同步執行完畢（無論是否正確完成）
    ```
    ```javascript
    // 正確建構的時候要提供「executor函數」作為輸入參數。「executor函數」可想像著裡面是另外一個執行緒在做事。
    // 「executor函數」必須是雙參數，第一個參數習慣性叫resolve，第二個叫reject。當然也可以改，但通常都不改。
    // 另一個執行緒的工作就是大括號裡的程式碼，也是逐行運行只是在另一個執行緒，會運行直到resolve或reject被呼叫。
    // resolve與reject就像是一個return，會停止後續的程式碼工作。
    // resolve的輸入會變成then方法的輸入，reject的輸入會變成catch方法的輸入。
    // 按照建議函數不需要名字，用匿名函數就好了，參數固定要兩個。箭頭函數誕生後更建議寫成箭頭函數。
    // 匿名函數方式
    const my_Promise = new Promise( function(resolve,reject){ ... });
    // 箭頭函數方式
    const my_Promise = new Promise( (resolve,reject) = > { ... });
    ```
    ```javascript
    // 神奇的鏈結方法(then):
    const my_Promise = new Promise(function(resolve, reject) {
      // 成功(資料 value 向下一個鏈結then傳遞)
      resolve('success');
      // 失敗(錯誤 reason 向下一個鏈結catch傳遞)
      reject('error');
    });
    
    // then方法與catch方法裡面要放一個匿名函數，箭頭函數誕生後建議用箭頭函數撰寫。
    // then方法只取出promise成功運行到resolve函數時，傳進resolve的東西，然後塞進匿名函數的變數中
    // catch方法只取出promise成功運行到resolve函數時，傳進reject的東西，然後塞進匿名函數的變數中
    my_Promise.then( (resolve_result) => {
        console.log(resolve_result);
    })
    .catch( (reject_result) => {
        console.log(reject_result);
    });    
    ```
    ```javascript
    // 神奇的鏈結方法(catch):
    const my_Promise = new Promise(function(resolve, reject) {
      // 失敗(錯誤 reason 向下一個鏈結catch傳遞)
      reject('error');
      // 成功(資料 value 向下一個鏈結then傳遞)
      resolve('success');      
    });
    
    // then方法與catch方法裡面要放一個匿名函數，箭頭函數誕生後建議用箭頭函數撰寫。
    // then方法只取出promise成功運行到resolve函數時，傳進resolve的東西，然後塞進匿名函數的變數中
    // catch方法只取出promise成功運行到resolve函數時，傳進reject的東西，然後塞進匿名函數的變數中
    my_Promise.then( (resolve_result) => {
        console.log(resolve_result);
    })
    .catch( (reject_result) => {
        console.log(reject_result);
    });    
    ```
    > 可以想像reject、resolve兩個參數就像是特別的return命令，分別用來傳東西給then與catch的匿名函數。

## 非同步函數(async function)
  + 宣告函數(使用陳述式):
      ```javascript
      // 陳述式宣告一個add_one的非同步函數(宣告寫在呼叫之前)。
      // 這不會回傳東西，但會在全域出現這個函數可以被使用。
      // 這個宣告不會運行，位置在哪都一樣，當Script被完整載入後就會被宣告到全域中。被稱作「提升」。
      async function add_one(x) {
          x=x+1;
          return x;
      }
      // 呼叫方式，呼叫非同步函數後會回傳一個Promise。
      let add_one_promise=add_one(5);
      console.log(add_one_promise);
      ```
      ```javascript
      // 呼叫方式，呼叫非同步函數後會回傳一個Promise。
      let add_one_promise=add_one(5);
      console.log(add_one_promise);
      // 陳述式宣告一個add_one的非同步函數(宣告寫在呼叫之後)。
      // 這不會回傳東西，但會在全域出現這個函數可以被使用。
      // 這個宣告不會運行，位置在哪都一樣，當Script被完整載入後就會被宣告到全域中。被稱作「提升」。
      async function add_one(x) {
          x=x+1;
          return x;
      }
      ```
  + 函數表達式:
      + JS的奇怪建立函數的方法，偏偏比較常用，看起來跟宣告函數超像。 
      ```javascript
      // 表達式宣告一個add_one的非同步函數。
      // 會回傳物件(使這個函數成為一個物件)。
      // 這個宣告不會運行，宣告部分要寫在呼叫之前。也就是不會被「提升」。
      var my_add_one = async function add_one(x) {
          x=x+1;
          return x;
      }
      // 呼叫方式，呼叫非同步函數後會回傳一個Promise。
      let add_one_promise=my_add_one(5);
      console.log(add_one_promise);
      ```
      ```javascript
      // 表達式宣告一個匿名非同步函數。
      // 會回傳物件(使這個函數成為一個物件)。
      // 這個宣告不會運行，宣告部分要寫在呼叫之前。也就是不會被「提升」。
      // function後面不寫名字叫做匿名函數，通常給名字是讓內部呼叫用的，否則寫了也是白寫。
      var my_add_one = async function(x) {
          x=x+1;
          return x;
      }
      // 呼叫方式，呼叫非同步函數後會回傳一個Promise。
      let add_one_promise=my_add_one(5);
      console.log(add_one_promise);
      ```
+ 箭頭函數:
    ```javascript
    // 表達式宣告一個箭頭函數。
    // 會回傳物件(使這個函數成為一個物件)。
    // 這個宣告不會運行，宣告部分要寫在呼叫之前。也就是不會被「提升」。
    var my_add_one = async (x) => {
        x=x+1;
        return x;
    }

    // 呼叫方式
    let add_one_promise=my_add_one(5);
    console.log(add_one_promise);
    ```
