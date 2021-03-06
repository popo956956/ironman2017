# React篇 - 路由器(router) 與 本篇小結

![intro](https://raw.githubusercontent.com/eyesofkids/ironman2017/master/day24_react_router/asset/intro.png)

今天的主題是路由器(router)，以及關於React篇的一些總結資訊。今天並沒有把路由器整合到原先的TodoApp之中，所以沒有範例。

> 註: 本文章同步放置於[Github庫的這裡](https://github.com/eyesofkids/ironman2017/tree/master/day24_react_router/)，所有的程式碼也在裡面。

## 路由器(router)是什麼

談到路由器(router)，你應該先了解什麼是路由(routes)，對於網站來說，它其實就是瀏覽器上的網址路徑，對於程式來說，它稱為路由(routes)，這裡指的程式當然是像在伺服器端的PHP程式，或是在瀏覽器端(客戶端)的JS程式。

React是一個開發單頁式應用(SPA)的函式庫，按照設計，所有的應用都只會在單一個網頁下執行，也就是網址並不會變動，不論你作大大小小的事情，都在這個網頁之中，也就是說它沒有考慮不同網址的情況，這種方式的設計很合理，但在某些情況下，少了一些彈性或功能。

> 將會少了什麼彈性或功能？

我們先了解，如果React要切換應用中不同的場景(Screen)頁面該如何作，對React來說，它的設計是在觸發事件後然後重新渲染，你大可用一個工具列或選單放上連結或按鈕，在不同的事件被觸發後，就重新渲染，載入對應的元件即可，這樣就可以切換不同的場景(Screen)，在另一個事件觸發時，例如儲存完資料，或使用者點按了另一個工具列/選單的連結，再切換到另一個場景(Screen)，運作的概念類似於在我們的TodoApp中雙點按其中一個項目，然後項目變為可編輯的文字框一樣。如果要為了管理得很好，你也可以把每個要切換的場景與連結，放在state中來管理，以此作為切換場景的依據。

單頁式應用(SPA)的設計，在簡單的應用中很容易作，也可以運作得很好的，但這個方式會有一些問題，問題是來自於當應用裡面的元件開始複雜時，這個方式會顯得不易組織與管理，當然還有可能有其他的需求出現:

- 巢狀的元件結構: 當出現巢狀的元件結構時，例如你切換到某個場景後，裡面還有其他的場景要切換，類似網站的子選單結構，這種情況不易管理
- 網址直接連結: 例如要使用網址來切換場景，像`/`根網址路徑是連到主應用，`/additem`是連到新增一筆項目，在單頁式應用(SPA)的設計下是作不到的
- 網址上的參數: 網址上可以指定參數，用參數來指明是要作什麼，例如`/edititem:id`，代表要編輯某一筆id值的項目
- 瀏覽器的歷史記錄: 最簡單像是的"返回上一個場景"這樣的功能

路由器(router)套件可以幫你作的，就是上面說的這幾點，它都可以幫你解決這些問題。

在React中發展最早，也是最多人使用的，就是[react-router](https://github.com/ReactTraining/react-router)，它是由[React Training](https://reacttraining.com/)這個專門提供React教育訓練的組織所開發，而不是由React官方所發佈的。

當然，你可能會認為像這麼重要的功能，為何是由社群主導而非官方？實際上React官方本來在開發上的角色並不是像你所想的那麼包山包海，React在Facebook投入的人力並沒有很多，大部份都是作核心的開發與決策性的工作，社群或其他公司團隊的參與程度反而比例是很高的。另一個明顯的例子是像之後我們要介紹的Redux，它也不是React官方所制作的函式庫。在React Native中會更明顯，官網上的文件常常建議你去用社群上的另一個元件，而不要用官方現在提供的，可能是舊了或功能沒這社群元件的好用。這也算是React相關專案的特性之一吧。

[react-router](https://github.com/ReactTraining/react-router)是一個包含很多功能的套件，它裡面的內容很多，因為它要解決的事情很多，也要回應社群上的各種需求，所以現在的react-router已經愈來愈複雜且內容很多，不太像我之前一開始學它的時候那麼容易學習與使用。

那為何不把react-router加到現在的TodoApp之中？主要有兩個原因，第一個原因是它正在作新版本v4.0，還在alpha中，我個人雖然比較傾向用v4.0，但可能用了有很多問題，或是之後會裡面的功能會改，所以現在如果要用大概還是只能先用v3.0。目前[新的官網上的文件](https://react-router.now.sh/)都是使用v4.0的。你可以看裡面的範例如何使用，當然，react-router的內容與功能很多，它仍然有一些基礎可以先學習，其它的各種情況下的應用可以需要的時候再參考。

第二個原因是，路由器(router)也是一個應用程式領域的主題，它涉及到整個應用程式該如何運作，內部資料要如何傳遞，也就是說它與之後的Redux會需要搭配運用，而且是必定要互相搭配，不然這兩個會互相衝突卡到。Redux官方也有一篇專門解說React Router如何與Redux整合的[文章](http://redux.js.org/docs/advanced/UsageWithReactRouter.html)。目前還有另一個解決方式，就是用專門為redux所開發的套件[react-router-redux](https://github.com/reactjs/react-router-redux)，它可以扮演React Router如何與Redux同步整合的工作。但也就是說，你也得先學會用Redux後，再用這個套件。而我想如果你用了Redux，不用這個同步整合套件也滿可惜的，時光旅行(之後會說到)是Redux中很棒的功能。

題外話是與React Native有關，react-router是在網頁上才需要的功能，它並不能在React Native裡使用，因為在手機App裡並不是用"路由(routes)"的概念在切換場景的，而是用"導覽(Navigation)"的概念，不太一樣的設計。當然，社群上也有人想用React Router的作法，包了一套[react-router-native](https://github.com/jmurzy/react-router-native)，不過不太受歡迎，目前比較受歡迎的是[react-native-router-flux](https://github.com/aksonov/react-native-router-flux)，但是它這個套件的名稱也取作router(路由器)，用了類似路由器的作法，而且需要Redux/Flux搭配使用。當然，目前內建的Navigator元件，與未來將會正式的NavigationExperimental元件，可能是另一種比較常看到的用法。

最後，對於路由器的部份，如果你的應用功能很少也不複雜(像我們的TodoApp)，並不需要沒什麼太特別的路由功能，你也不需要像上面說的這些使用情況，你不一定要使用像react-router的套件，在這篇[You might not need React Router](https://medium.freecodecamp.com/you-might-not-need-react-router-38673620f3d#.u21cisvjk)，有提供一些另外的想法。

---

## 本篇小結

在經過了漫長的React篇之後，下一章將是新的開始 - Redux篇。原本按照我原本的想法，每一篇都要幫它們取個好名字:

- React - DOM界的彼方
- Flux - 一方通行
- Redux - 穿越時空的狀態

這些名稱都是改編自輕小說或動畫而來，以下是轉自維基百科中的說明與比喻。

### React - DOM界的彼方

改編自"《[境界的彼方](https://zh.wikipedia.org/wiki/%E5%A2%83%E7%95%8C%E7%9A%84%E5%BD%BC%E6%96%B9)》（日語：境界の彼方），是日本作家鳥居なごむ創作的輕小說作品"。

#### 境界的彼方（境界の彼方（きょうかいのかなた））

傳說會帶來巨大災禍的妖夢，沒有實體，看起來就像鏡子般倒映著所有景物。據說各種疾病、戰爭等皆是由它引起，推測擁有「讓持有者具現出極其思念之人的肉體」的能力，也能讓持有者擁有不死之身的能力，目前潛伏在秋人的體內。實際上為妖夢世界和人類世界的大門

> 用"DOM界的彼方"，主要比喻React就像是真實網頁上的DOM元素與JS應用程式的一個大門，也是看起來像是鏡子般倒映所有的DOM元素一樣。

### Flux - 一方通行

採用"《[魔法禁書目錄](https://zh.wikipedia.org/wiki/%E9%AD%94%E6%B3%95%E7%A6%81%E6%9B%B8%E7%9B%AE%E9%8C%84)》的一個角色，[一方通行](https://zh.wikipedia.org/wiki/%E4%B8%80%E6%96%B9%E9%80%9A%E8%A1%8C)（日語：アクセラレータ，英語：Accelerator）是《魔法禁書目錄》的第二主角，科學側男主角之一，也是其外傳《科學一方通行》及《偶像一方通行》的主角"

一方通行的能力是「向量操作」（Vector Control），只要是接觸到自己的皮膚的，不管是動能、熱能、電能等任何所有能量，其方向都能受到一方通行的操控。他可以在自己的計算能力範圍內改變一切已知的能量的方向。

> 用"一方通行"，主要比喻Flux架構的資源流是只有單一個方向。

### Redux - 穿越時空的狀態

改編自"《[穿越時空的少女](https://zh.wikipedia.org/wiki/%E7%A9%BF%E8%B6%8A%E6%99%82%E7%A9%BA%E7%9A%84%E5%B0%91%E5%A5%B3)》（原題：時をかける少女）是日本小說家筒井康隆於1965年創作的青少年取向短篇科幻小說，曾多次被改編成電視劇、電影與動畫電影。"

> 用"Redux - 穿越時空的狀態"，主要比喻Redux中具有時光旅行的除錯功能。

---

其實我不太想用像"30天精通React"(因為30天也不會精通，我自己都沒精通了...)、"快快樂樂學React"或"輕輕鬆鬆學React"(學這麼艱難的技術怎麼輕鬆，又怎麼會快樂得起來...)，或是什麼"王者歸來xxx"、"瘋狂React講義"(好怪的名字，但聽說都很熱賣...)。上面用這些名稱只是純粹個人喜好而已，當然它們都有比喻一些東西，與這個技術它的核心概念有關。

React篇到這裡就是最後了一章了，雖然我能寫的內容很有限，但也差不多就是足以達到入門的階段，對我來說，這些學習的過程大概花了一年多，當然這些文章中的知識只是我學到的一部份而已。我想最後面因為並沒有人在23篇文章問過任何問題，所以我只好自問自答一些在討論區中常見的問題，這些解答就作為你學習React的一些經驗參考，以下答案純屬個人想法。

---

### 為什麼要學React而不學Vue.js、Angular2？React比較好的原因是什麼？

這個問題很常見，對我來說，我其實是想寫手機上的App，所以才學React的，手機上的App要用React Native寫，但它的語法基礎是React。

Vue.js、Angular2我並沒有花太多時間深入研究，所以我沒辦法比較得準確，但我知道每套受歡迎的框架或函式庫，自然有它較為合適的應用情況，React不可能在每種應用情況都是合適的，它的目的也不是如此。以生態圈整體來看，React是最多人支持的，所以它的可取得資源也是最多的，學習資源、週邊套件什麼的，都是最多的，其他的兩套可能就沒那麼多，但也不少。

未來的發展會如何？沒人知道，但至少在2017年，這個局勢並不會差太多。React與React Native並不是一下子蹦出來的專案，它其實背後已經有很多發展很久的專案支持，或是用了其他專案的設計概念延伸出來的東西，像最近阿里巴巴為Vue.js打造的[weex](https://github.com/alibaba/weex)，可以用Vue.js語法來開發手機App，裡面用的架構與React Native差不了多少，一樣是用FB的[css-layout](https://github.com/facebook/yoga)專案(現在改名為Yoga)作底層。當然美其名為專為Vue.js打造，其實也並非創新，說老實話會變成"跟風"或"仿效"，當然開放原始碼抄來抄去的風氣本來就是這樣。阿里巴巴作開放原始碼的之前故事很多就不多說，網路上可以找到。

回到最本質的情況，開放原始碼上社群的力量畢竟還是最重要的，不論是協助開發的，還是宣傳的、教育的都是。大公司再怎麼有錢有人，沒有創新、沒有真的契合到真正的需求，作再炫的專案也沒人想要用。像Google Chrome瀏覽器，從零開始作起，到今天不到十年變成市佔率最高的瀏覽器(2008年發佈)，V8引擎成為最重要的JS引擎，原本的執行長一直反對了好多年，誰知道這一走來在裡面開發的這些工程師的辛苦。

我會認為React與React Native今天會出名不會是一個遇然性的結果，Facebook在很多基礎的技術扎根很久了，你可以看最近它在[2016年的回顧](https://code.facebook.com/posts/1058188987642144/facebook-open-source-2016-year-in-review/)中，其實有很多專案。它也願意投資贊助其它的相關開放原始碼專案，babel工具就是一個例子。從另一個角度看起來，FB是真的用這些技術在自己的服務上，今天我們所看到的Facebook網站，上面就用了React技術，手機上的Facebook App與其他的相關App就用了React Native技術，可見它是真的重視與應用這些技術，不是開玩笑的拿石頭來砸自己的腳，而不是拿來作學術研究而已。那麼你用這個角度來檢視其他的技術，他們又是怎麼樣的一個發展的情況呢？

### 要學React Native要先學React嗎？

當然，語法概念設計都一樣，不學React直接學或用React Native，痛苦指數保証直線上升。

學React最好還是先有ES6基礎，而且一定要學到Redux等Flux的架構，這是一段很漫長的過程，如果有人說你可以幾天就學會或精通，那是騙人的，大部份的課程或教學都是超級入門的，或是用走馬看花式的什麼都介紹一點，太深入的內容就跳過。

React Native還有它自己的其他基礎知識，例如排版用的Flexbox、或是取代Ajax的Fetch API等等。

### 要學React的學習路徑應該是怎麼樣的？

首先，你要先學好ES6與JavaScript，再來是你要開始會建置開發環境與使用這些開發工具。

如果你已經有學過jQuery，暫時先忘了它吧，jQuery與React的開發概念完全不同。

常常聽到有人抱怨說: "呃，這功能我用jQuery，寫十分鐘就作出來了，React要這麼麻煩..."。概念不同，自然撰寫的方式都不同，心理上如果不能調適，我還是建議你用jQuery就好，如果你不能先放下心中的成見，永遠也學不了新的想法或概念。

技術進步得太快，唯一的好方式就是保持基礎，以不變應萬變，React上每天有太多的新知識要學習，但沒人學得完，也不可能學得完。

> 那什麼是基礎？

對JavaScript函式庫的基礎來說，就是ES6與JavaScript，基礎夠紥實，學什麼React、Vue.js或Angular都會比較容易。

對React來說，基礎就是基本的設計概念，JSX語法、props與state、生命週期方法這些基本的語法與特性。

你應該要多花時間學習基礎，而且要多思考一下，不是一開始就把網路上的範例拿來抄一抄，或是什麼套件不管三七二十一就直接套來套去這樣用。

React官方網站上的文件，都是很重要的一些參考的指引。我指的是[這個官方網站](https://facebook.github.io/react/)，不是簡體的翻譯網站，你如果英文不夠好，就多花點時間勤查字典，不要去看翻譯簡體的官方文章，雖然只有差一些時間，但翻得不會太好，加上文章的的版本也舊了，簡中的資料參考的價值會很低，而且有可能裡面有些方法或技術，早就被棄用或調整了。

不要花太多時間研究一些細節或內部，我常常有看到一些人在學習時，貼出研究React或Redux的原始碼的一些分析文章，我會認為研究這些東西一點意義都沒有，這是參與這些套件的開發者去研究的東西。因為這些程式碼也不是幾個寫的，是幾百人甚至上千人在提交的，除了從程式碼根本很難看出來設計的全貌之外。而且變動得很快，你今天研究完了，下個月就變了。你該花時間的是例如官方的設計概念的文件、範例，或是最近一些討論得很熱烈的議題(Issue)。當然，如果你的技術水平到一個程度，這就是另外一件事情了。

所有的函式庫或框架，都有其設計的核心理念，或是所依循的標準規定。React或Redux的原始碼只是實現了這些設計與標準的結果而已，當然有一開始的設計概念，也有在後面跟著產生的API文件，這兩個才是我們所需要學習與理解的。

## 結論

本篇是一個心得發表的章節，並沒有展示路由器的程式碼該怎麼作，理由在上面的內容中已經有說明了，之後我們再來看怎麼整合Redux與路由，它們都是與應用程式領域有關的特性。最後，回答了一些討論區中常見的問題，最近還是有很多朋友在問這些問題，當然你也可以參考我的部落格中之前回答的一些文章。

今天是"平安夜"，對歐美人士來說，就像我們過年的除夕一樣，也祝福所有的朋友們，幸福健康平安！
