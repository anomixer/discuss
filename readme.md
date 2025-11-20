[演示與特性](#演示與特性) | [下載安裝及用法](#下載安裝及用法) | [服務及支援](#服務及支援)

discuss: 省事一鍵輕量可聯合社交化平臺(可cf部署)🚀🎉
=====


鑑於現在的主機論很難玩又融入奇特化
釋出這個新的創新選擇小玩具

> 全稱為discuss，省事一鍵輕量可聯合社交化平臺 ..  

專案地址：[https://github.com/minlearn/discuss](https://github.com/minlearn/discuss)

演示與特性✨
-----


![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/instapps/discuss.png)



下載安裝及用法📄
-----

共3步

### 第一步. Fork本倉庫到你的GitHub帳號

登你的github，然後點選 [https://github.com/minlearn/discuss/fork](https://github.com/minlearn/discuss/fork) 把倉庫fork到你的github帳號

### 第二步. 在你fork到的倉庫裡面加幾個部署相關的密碼變數

進入你fork到的倉庫的 [Settings -> Secrets -> Actions](../../settings/secrets/actions), 建立幾個部署相關的密碼變數，共3個（最後2個r2相關的不需要），如何獲取這些變數及如何複製為變數(請展開檢視細節)：  

![](https://user-images.githubusercontent.com/1719237/205524410-268abf92-af61-467a-8883-78b8d4de3c56.png)

<details>
<summary><b>如何獲得CLOUDFLARE_ACCOUNT_ID變數</b></summary>
登入cf面板會自動跳到:https://dash.cloudflare.com/[你的帳號id]  ，比如這樣：https://dash.cloudflare.com/fff88980eeeeedcc3ffffd4f555f4999，  後面的 * fff88980eeeeedcc3ffffd4f555f4999 * 就是帳號id  
將其複製到倉庫的[Settings -> Secrets -> Actions](../../settings/secrets/actions) 處即可，注意複製到不要有多餘字元，會顯示為星號，
<IMG src="https://user-images.githubusercontent.com/1719237/208216752-56f00f51-29cb-43ea-b720-75244719898d.png"/>
</details>

<details>
<summary><b>如何獲得CLOUDFLARE_API_TOKEN變數</b></summary>
登入cf，定位到: https://dash.cloudflare.com/profile/api-tokens  建立一個custom token:  
<IMG src="https://user-images.githubusercontent.com/1719237/205525627-14da54ae-1733-4db5-b65d-94f5ec48f360.png"/>
修改token的許可權，放行Cloudflare Pages 和 D1:
<IMG src="https://user-images.githubusercontent.com/1719237/205525675-4c8a6bce-21a8-45e3-bf0c-28981f123da3.png"/>
像複製帳號id一樣複製為倉庫的對應名字變數
</details>


<details>
<summary><b>給要部署到cf的整套應用取一個名字字首CLOUDFLARE_PROJECT_NAME</b></summary>
隨便都可以，就是不要帶._等特殊符號，比如你取名為discuss，或discussmyxxxdomain都可以
像複製帳號id一樣複製為倉庫的對應名字變數
</details>


### 第三步. 在你fork到的倉庫裡面執行名為updatebuilddiscuss的部署

前往 [Actions -> Deploy to Cloudflare Pages](../../actions/workflows/deploy.yml) 執行deploy  
![](https://user-images.githubusercontent.com/1719237/205526856-05ea0ff4-703a-4d08-bc7f-4ae2dfc07cfe.png)


### 最後，檢查結果

等部署完畢, 綠點表示成功. 你可以在 [Cloudflare dashboard](https://dash.cloudflare.com/sign-up/pages) 處看到已生成形式為 CLOUDFLARE_PROJECT_NAME變數.pages.dev 的pages應用，點選即可訪問


### 更新/修改設定：

常規操作在論壇介面上即可操作。其它的如修改全域性設定，將使用者設為仲裁員和增加註冊碼的工作，請直接在d1資料庫中操作。

global:

找到這條資料（只有一條），下面字樣預設on改成off可開啟邀請及關閉公開瀏覽貼子，反之同理，不要破壞json結構
{"sitetitle":"Discuss","dismissmessage":"xxxxxx","public":"on"}

regcodes:  

| body            | isredeemed | redeemedto |
| :------:        | :-:        | :-: |
| 你要發放的邀請碼   |  0         | 留空，邀請碼被使用時會自動變成1 |

users:  

| ...            | roletags |
| :------:       | :-:        |
| ...            |  admin為超管,mod為仲裁,留空為普通成員         |


### 部署到本地或vps  

開啟 [https://github.com/minlearn/inst/tree/master/_build/apps/discuss](https://github.com/minlearn/inst/tree/master/_build/apps/discuss) ，在裝有debian的vps上執行指令碼discuss_install.sh即可。  

> Wrangler v3 預設使用了Miniflare v3,而Miniflare v3使用了workerd, workerd不僅是支援wrangler本地除錯的worker模擬環境，而且是產品級的nodejs runtime，所以可供本地直接部署worker/pages用，搭配帶快取的cdn，可以直接做站。  

服務及支援👀
-----

略





