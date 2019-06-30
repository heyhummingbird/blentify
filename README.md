# Blentify
## 題目名稱
(Group 19) Blentify

## 一句話描述這個服務在做什麼
這是一個結合spotify的漸層色遊戲網站。可以一邊收聽 Spotify上的歌曲，一邊以專輯封面作為色票基底玩色彩遊戲。

## 安裝/使用方式
1. Clone the repository
2. `npm install` to install the packages
3. Create a MongoDB.
4. Go to Spotify Developer to apply for client id and client secret, and add `http://localhost:3001/auth/spotify/callback` into callback url whitelist.
5. Store the above information in `backend/.env` using the following format.
`SP_ID` is the client ID for Spotify, and `SP_SECRET` is the client secret for Spotify.
```
(backend/.env)

DB_HOST={DB_HOST}
DB_USER={DB_USER}
DB_PASSWD={DB_PASSWD}
DB_NAME=test?retryWrites=true&w=majority
SP_ID={SP_ID}
SP_SECRET={SP_SECRET}
  ```
Substitute `{***SP_ID***}` in `frontend/App.js` with your own spotify client ID.

6. `npm start` in both `frontend/` and `backend/`
7. Open `localhost:3000` to start!

## 系統說明
1. 可以用 Spotify 帳戶登入，登入後可搜尋音樂，並點選音樂進入遊戲畫面
3. 可以一邊播放音樂一邊進行色彩遊戲
    - 色彩遊戲的色票有部份來自正在聆聽的音樂的專輯封面
    - 隨機產生地圖形狀，玩家須將上方提供的色彩以漸層的方式填入下方的地圖中
    - 支援上一步、下一步操作
    - 可按 `answer` 公佈答案
5. 提供不同的遊戲難度模式
    - random
    - 1
    - 2
    - 3
6. 可以選擇以訪客模式（不登入 Spotify）直接玩遊戲，色票直接隨機產生

## 使用與參考之框架/模組/原始碼
- frontend
    - react
    - axios
- backend
    - express
    - mongoose
    - spotify-web-api-node

## 使用之第三方套件、框架、程式碼
- frontend
    - color-thief
    - modal (https://github.com/jpntex/Modal.js)

## Supported browser
- Google Chrome
- Safari

## 組員分工
- 陳宥嘉（此 project 延伸自其 midterm project）
    - 色彩遊戲、DB 連接
- 楊舒瑄
    - 串接 Spotify API、整體 UI layout、css


## 專題製作心得
這是第一次去串 API，一開始有點撞牆，但後來發現 spotify API 蠻好用的，有提供一些意想不到的功能（像是 recommendation 可以下很多參數，雖然這次 project 沒有用到）。為了結合我們兩個想做的東西，最初在討論題目的時候想了很久，最後才勉強在色彩遊戲和音樂中間找到了一個接口（原本也有考慮過用音樂的調性來作為視覺顏色的基礎，但發現同樣調性的歌給人的感覺也會差很多，覺得調性並不適合拿來決定顏色，最後才決定直接用專輯封面決定顏色）。

雖然在期中時已經大概做完只有線條的遊戲，但這次從1D升級到2D還是花了很長一段時間構想及實作，算是有把期中目標遊戲能夠擴充地圖跟難度的部分都做到了，至於切換色票這個構想，讓我必須去額外補充一些canvas相關知識，雖然最後好像並沒有實作進去，但也算是有所收穫。