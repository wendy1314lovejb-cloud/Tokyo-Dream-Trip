# -app
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>2026 東京夢幻之旅 💜</title>
    <style>
        :root {
            --primary-color: #9370DB; /* 夢幻紫 */
            --secondary-color: #8A2BE2; /* 深紫 */
            --bg-color: #F8F4FF; /* 極淺紫白底 */
            --card-bg: #FFFFFF;
            --text-main: #333333;
            --text-light: #666666;
            --tag-food: #FFE4E1;
            --tag-food-text: #D2691E;
            --tag-buy: #E6E6FA;
            --tag-buy-text: #4B0082;
        }

        body {
            margin: 0;
            font-family: "PingFang TC", "Helvetica Neue", Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            padding-bottom: 80px; /* 給底部導覽列留空間 */
        }

        .header {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 20px 15px;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(138, 43, 226, 0.2);
            border-bottom-left-radius: 15px;
            border-bottom-right-radius: 15px;
        }

        .header h1 { margin: 0; font-size: 1.2rem; font-weight: 600; letter-spacing: 1px; }

        .container { padding: 15px; max-width: 600px; margin: 0 auto; }

        .tab-content { display: none; animation: fadeIn 0.3s ease; }
        .tab-content.active { display: block; }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        .card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 18px;
            margin-bottom: 15px;
            box-shadow: 0 4px 12px rgba(147, 112, 219, 0.08);
            border-left: 6px solid var(--primary-color);
        }

        .card-title {
            font-size: 1.1rem;
            font-weight: bold;
            color: var(--secondary-color);
            margin-top: 0;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .weather {
            font-size: 0.85rem;
            color: var(--text-light);
            background: #F0F0F0;
            padding: 6px 10px;
            border-radius: 8px;
            margin-bottom: 12px;
            display: inline-block;
        }

        ul { padding-left: 20px; margin: 10px 0; color: var(--text-light); line-height: 1.6; }
        li { margin-bottom: 8px; }
        strong { color: var(--text-main); }

        .tag {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 12px;
            font-size: 0.75rem;
            font-weight: bold;
            margin-right: 5px;
            margin-top: 5px;
        }
        .tag.food { background-color: var(--tag-food); color: var(--tag-food-text); }
        .tag.buy { background-color: var(--tag-buy); color: var(--tag-buy-text); }
        .tag.story { background-color: #FFF0F5; color: #C71585; }

        .nav-btn-link {
            background-color: var(--primary-color);
            color: white;
            text-decoration: none;
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            display: inline-flex;
            align-items: center;
            margin-top: 8px;
            box-shadow: 0 2px 5px rgba(147, 112, 219, 0.3);
        }

        /* 底部導覽列 */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            display: flex;
            justify-content: space-around;
            padding: 10px 0 calc(10px + env(safe-area-inset-bottom));
            box-shadow: 0 -2px 15px rgba(0,0,0,0.05);
            z-index: 1000;
            border-top: 1px solid #eee;
        }

        .nav-item {
            background: none;
            border: none;
            font-size: 0.75rem;
            color: #A9A9A9;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            align-items: center;
            flex: 1;
        }

        .nav-item.active { color: var(--secondary-color); font-weight: bold; }
        .nav-icon { font-size: 1.6rem; margin-bottom: 4px; }

        /* 工具箱表格與樣式 */
        table { width: 100%; border-collapse: collapse; margin-top: 10px; font-size: 0.9rem; }
        th, td { border: 1px solid #eee; padding: 10px; text-align: left; }
        th { background-color: var(--bg-color); color: var(--secondary-color); }
        
        .converter-box { background: white; padding: 15px; border-radius: 12px; border: 2px solid var(--primary-color); text-align: center; }
        .converter-input { padding: 10px; font-size: 1.1rem; width: 60%; border: 1px solid #ccc; border-radius: 8px; margin: 10px 0; text-align: center; }
    </style>
</head>
<body>

    <div class="header">
        <h1>💜 2026 東京夢幻之旅 💜</h1>
    </div>

    <div class="container">
        <!-- 分頁 1: 行程 -->
        <div id="tab-itinerary" class="tab-content active">
            
            <div class="card">
                <h3 class="card-title">Day 1: 啟程與都會浪漫 <span>10/26 周一</span></h3>
                <div class="weather">⛅ 氣溫約 15°C - 21°C，建議帶紫色輕薄小外套</div>
                <ul>
                    <li><strong>🚆 交通：</strong>12:10 抵達成田機場 ➔ Skyliner至船橋 ➔ 總武線至西船橋 ➔ 東西線至南行德</li>
                    <li><strong>📍 景點：中目黑</strong>
                        <br><a href="https://maps.google.com/?q=星巴克臻選東京烘焙工坊" target="_blank" class="nav-btn-link">🚗 導航：星巴克山手通店</a>
                        <br><span class="tag story">💡 全球僅六間的旗艦店！四層樓紅銅櫻花樹</span>
                        <br><span class="tag food">😋 必點：一樓精緻麵包(Princi)與特調</span>
                    </li>
                    <li><strong>📍 景點：小義大利 La vita</strong>
                        <br><a href="https://maps.google.com/?q=中目黑+La+vita" target="_blank" class="nav-btn-link">🚗 導航：La vita</a>
                    </li>
                    <li><strong>🛒 逛街：上野阿美橫町</strong>
                        <br><a href="https://maps.google.com/?q=上野阿美橫町" target="_blank" class="nav-btn-link">🚗 導航：阿美橫町</a>
                        <br><span class="tag buy">🛍️ 必買：OS Drug / 零食大王二木菓子</span>
                    </li>
                </ul>
            </div>

            <div class="card">
                <h3 class="card-title">Day 2: 傳統風情與極致和牛 <span>10/27 周二</span></h3>
                <div class="weather">🌤️ 晴時多雲，14°C - 20°C。穿和服的好天氣！</div>
                <ul>
                    <li><strong>👘 體驗：江户和装工房 雅</strong>
                        <br><span class="tag buy">🔖 預約代號：(請填寫)</span>
                    </li>
                    <li><strong>📍 景點：淺草寺、雷門、仲見世通</strong>
                        <br><a href="https://maps.google.com/?q=雷門" target="_blank" class="nav-btn-link">🚗 導航：雷門</a>
                        <br><span class="tag food">😋 必吃：淺草九重炸饅頭、花月堂菠蘿麵包</span>
                    </li>
                    <li><strong>🍵 甜點：Suzukien 淺草本店</strong>
                        <br><span class="tag food">😋 必吃：世界最濃 No.7 頂級抹茶冰淇淋</span>
                    </li>
                    <li><strong>📍 景點：今戶神社 & 晴空塔</strong>
                        <br><span class="tag story">💡 今戶神社是招財貓發源地，祈求好姻緣！</span>
                    </li>
                    <li><strong>🥩 晚餐：燒肉黑田 (澀谷)</strong>
                        <br><a href="https://maps.google.com/?q=燒肉黑田+澀谷" target="_blank" class="nav-btn-link">🚗 導航：燒肉黑田</a>
                        <br><span class="tag story">💡 享受深夜和牛饗宴</span>
                        <br><span class="tag food">😋 必點：厚切牛舌與和牛特選部位</span>
                    </li>
                </ul>
            </div>

            <div class="card">
                <h3 class="card-title">Day 3: 迪士尼海洋 <span>10/28 周三</span></h3>
                <div class="weather">☀️ 晴朗，15°C - 22°C。海風較大需防風。</div>
                <ul>
                    <li><strong>🚆 交通秘訣：</strong>南行德(東西線) ➔ 葛西站/浦安站 ➔ 轉巴士直達舞濱</li>
                    <li><strong>🎢 樂園：Tokyo Disney Sea</strong>
                        <br><a href="https://maps.google.com/?q=東京迪士尼海洋" target="_blank" class="nav-btn-link">🚗 導航：迪士尼海洋</a>
                        <br><span class="tag story">💡 全新「夢幻泉鄉」冰雪奇緣與魔髮奇緣！</span>
                        <br><span class="tag buy">📱 必做：入園即抽 Standby Pass 或買 DPA</span>
                        <br><span class="tag food">😋 必吃：三眼怪麻糬、火雞腿</span>
                    </li>
                </ul>
            </div>

            <div class="card">
                <h3 class="card-title">Day 4: 迪士尼樂園 <span>10/29 周四</span></h3>
                <div class="weather">☀️ 晴朗，16°C - 23°C。公主夢幻日！</div>
                <ul>
                    <li><strong>🏰 樂園：Tokyo Disney Land</strong>
                        <br><a href="https://maps.google.com/?q=東京迪士尼樂園" target="_blank" class="nav-btn-link">🚗 導航：迪士尼樂園</a>
                        <br><span class="tag story">💡 提早卡位美女與野獸「城堡奇緣」</span>
                        <br><span class="tag buy">🛍️ 必買：公主系列髮飾、米奇爆米花桶</span>
                    </li>
                </ul>
            </div>

            <div class="card">
                <h3 class="card-title">Day 5: 高空絕景與時尚散策 <span>10/30 周五</span></h3>
                <div class="weather">⛅ 多雲時晴，14°C - 21°C。</div>
                <ul>
                    <li><strong>📍 上午：東京都廳觀景臺 ➔ 明治神宮</strong></li>
                    <li><strong>🥩 午餐：敘敘苑 (東京歌劇城 53F)</strong>
                        <br><a href="https://maps.google.com/?q=敘敘苑+東京歌劇城" target="_blank" class="nav-btn-link">🚗 導航：敘敘苑</a>
                        <br><span class="tag food">😋 必點：高CP值商業午餐 (牛切落燒肉)</span>
                    </li>
                    <li><strong>🛍️ 下午：原宿竹下通 ➔ 伊勢丹新宿店</strong>
                        <br><span class="tag buy">🛍️ 必買：伊勢丹地下街最高級甜點</span>
                    </li>
                    <li><strong>🌃 晚上：澀谷 SKY ➔ 歌舞伎町散策</strong>
                        <br><a href="https://maps.google.com/?q=澀谷+SKY" target="_blank" class="nav-btn-link">🚗 導航：澀谷 SKY</a>
                        <br><span class="tag buy">🔖 澀谷SKY預約代號：(請提前出示QR)</span>
                    </li>
                </ul>
            </div>

            <div class="card">
                <h3 class="card-title">Day 6: 滿載而歸 <span>10/31 周六</span></h3>
                <div class="weather">☁️ 多雲，13°C - 19°C。</div>
                <ul>
                    <li><strong>⏰ 08:15</strong> 離開飯店</li>
                    <li><strong>⏰ 09:25</strong> 前抵達成田機場並報到</li>
                    <li><strong>✈️ 11:25</strong> 起飛 (IT281) ➔ 15:05 抵達高雄</li>
                </ul>
            </div>
        </div>

        <!-- 分頁 2: 工具 -->
        <div id="tab-tools" class="tab-content">
            <div class="card">
                <h3 class="card-title">✈️ 航班資訊</h3>
                <table>
                    <tr><th>去程 (10/26)</th><td>IT280<br>KHH 08:00 ➔ NRT 12:10</td></tr>
                    <tr><th>回程 (10/31)</th><td>IT281<br>NRT 11:25 ➔ KHH 15:05</td></tr>
                    <tr><td colspan="2"><span class="tag buy">🔖 虎航訂位代號：</span></td></tr>
                </table>
            </div>

            <div class="card">
                <h3 class="card-title">🏨 住宿資訊</h3>
                <ul>
                    <li><strong>飯店：</strong>D Regalo (南行德站)</li>
                    <li><strong>期間：</strong>10/26 - 10/31 (共5晚)</li>
                    <li><span class="tag buy">🔖 入住憑證號碼：</span></li>
                </ul>
                <a href="https://maps.google.com/?q=D+Regalo+南行德" target="_blank" class="nav-btn-link" style="width: 100%; text-align: center; justify-content: center; box-sizing: border-box;">🚗 一鍵導航回飯店</a>
            </div>

            <div class="card">
                <h3 class="card-title">📞 緊急聯絡電話</h3>
                <ul>
                    <li><strong>日本報警：</strong><a href="tel:110">110</a></li>
                    <li><strong>救護車/火警：</strong><a href="tel:119">119</a></li>
                    <li><strong>急難救助免付費：</strong><a href="tel:00180008850885">001-800-0885-0885</a></li>
                    <li><strong>駐日代表處(緊急)：</strong><a href="tel:+818010097179">+81-80-1009-7179</a></li>
                </ul>
            </div>
        </div>

        <!-- 分頁 3: 預算 -->
        <div id="tab-budget" class="tab-content">
            <div class="card converter-box">
                <h3 class="card-title" style="justify-content: center;">💱 匯率小算盤</h3>
                <p style="font-size: 0.85rem; color: var(--text-light);">輸入日幣，自動換算台幣 (預設匯率 0.215)</p>
                <div>¥ <input type="number" id="jpyInput" class="converter-input" placeholder="輸入日幣金額" oninput="calcCurrency()"></div>
                <div style="font-size: 1.2rem; font-weight: bold; color: var(--secondary-color); margin-top: 10px;">
                    約等於 NT$ <span id="twdOutput">0</span>
                </div>
            </div>

            <div class="card">
                <h3 class="card-title">📝 記帳清單</h3>
                <p style="font-size: 0.85rem; color: var(--text-light);">可截圖或在此記錄您的花費</p>
                <ul style="list-style: none; padding-left: 0;">
                    <li style="border-bottom: 1px dashed #ccc; padding-bottom: 5px;">💸 交通票券：¥ _________</li>
                    <li style="border-bottom: 1px dashed #ccc; padding-bottom: 5px;">💸 餐飲美食：¥ _________</li>
                    <li style="border-bottom: 1px dashed #ccc; padding-bottom: 5px;">💸 和服體驗：¥ _________</li>
                    <li style="border-bottom: 1px dashed #ccc; padding-bottom: 5px;">💸 樂園花費：¥ _________</li>
                    <li style="border-bottom: 1px dashed #ccc; padding-bottom: 5px;">💸 伴手/藥妝：¥ _________</li>
                    <li style="padding-bottom: 5px; font-weight: bold; color: var(--secondary-color);">🔥 總結算：¥ _________</li>
                </ul>
            </div>
        </div>

    </div>

    <!-- 底部導覽列 -->
    <div class="bottom-nav">
        <button class="nav-item active" onclick="switchTab('tab-itinerary', this)">
            <span class="nav-icon">📅</span>
            <span>行程</span>
        </button>
        <button class="nav-item" onclick="switchTab('tab-tools', this)">
            <span class="nav-icon">🛠️</span>
            <span>工具</span>
        </button>
        <button class="nav-item" onclick="switchTab('tab-budget', this)">
            <span class="nav-icon">💰</span>
            <span>預算</span>
        </button>
    </div>

    <script>
        function switchTab(tabId, btnElement) {
            // 隱藏所有內容
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            // 移除所有按鈕的 active 狀態
            document.querySelectorAll('.nav-item').forEach(btn => {
                btn.classList.remove('active');
            });
            
            // 顯示選擇的內容並高亮按鈕
            document.getElementById(tabId).classList.add('active');
            btnElement.classList.add('active');
            
            // 切換時回到頂部
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function calcCurrency() {
            const jpy = document.getElementById('jpyInput').value;
            const rate = 0.215; // 可在此修改匯率
            const twd = Math.round(jpy * rate);
            document.getElementById('twdOutput').innerText = twd.toLocaleString();
        }
    </script>
</body>
</html>
