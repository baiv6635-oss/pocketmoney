<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PocketMoney Earning App</title>
    <!-- Telegram WebApp SDK -->
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f2f5;
            color: #333;
            padding: 15px;
        }
        /* ১. হেডার ও প্রোফাইল */
        .header-card {
            background: linear-gradient(135deg, #0088cc, #005588);
            color: #fff;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            margin-bottom: 15px;
        }
        .logo {
            width: 65px;
            height: 65px;
            border-radius: 50%;
            border: 3px solid #fff;
            margin-bottom: 8px;
        }
        .balance-box {
            background: rgba(255, 255, 255, 0.2);
            padding: 10px;
            border-radius: 10px;
            margin-top: 10px;
            font-size: 18px;
            font-weight: bold;
        }

        /* কার্ড স্টাইল */
        .card {
            background: #fff;
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
        }
        .card h3 {
            font-size: 16px;
            margin-bottom: 12px;
            color: #0088cc;
            border-bottom: 2px solid #f0f2f5;
            padding-bottom: 6px;
        }

        /* বাটন ও ইনপুট */
        .btn {
            background-color: #0088cc;
            color: #fff;
            border: none;
            padding: 10px 15px;
            border-radius: 8px;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            margin-top: 6px;
            transition: 0.2s;
        }
        .btn:active { opacity: 0.85; }
        .btn-success { background-color: #27ae60; }
        .btn-premium { background-color: #f39c12; }
        
        .task-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            background: #f9f9f9;
            padding: 10px;
            border-radius: 8px;
        }
        .task-item span { font-size: 13px; font-weight: 500; }
        .task-btn { width: auto; padding: 6px 12px; font-size: 12px; }

        input {
            width: 100%;
            padding: 10px;
            margin-top: 8px;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 14px;
        }
        .ref-box {
            display: flex;
            gap: 8px;
            margin-top: 8px;
        }
    </style>
</head>
<body>

    <!-- ১. লোগো, নাম ও ব্যালেন্স -->
    <div class="header-card">
        <img src="https://via.placeholder.com/65" id="user-photo" class="logo" alt="Logo">
        <h2 id="user-name">Loading...</h2>
        <div class="balance-box">
            ব্যালেন্স: <span id="user-balance">0</span> টাকা | রেফার: <span id="ref-count">0</span> জন
        </div>
    </div>

    <!-- ২. এডস দেখা -->
    <div class="card">
        <h3>📢 বিজ্ঞাপন ও কুইক টাস্ক</h3>
        <button class="btn btn-success" onclick="watchAd()">বিজ্ঞাপন দেখুন (+৫ টাকা)</button>
    </div>

    <!-- ৪, ৫, ৬. সোশ্যাল মিডিয়া টাস্ক -->
    <div class="card">
        <h3>🎯 ইনকাম টাস্কসমূহ</h3>
        
        <!-- ৪. টেলিগ্রাম টাস্ক -->
        <div class="task-item">
            <span>টেলিগ্রাম চ্যানেলে জয়েন করুন</span>
            <button class="btn task-btn" onclick="doTask('https://t.me/your_channel', 10)">Start</button>
        </div>

        <!-- ৫. ইউটিউব টাস্ক -->
        <div class="task-item">
            <span>ইউটিউব সাবস্ক্রাইব ও লাইক</span>
            <button class="btn task-btn" onclick="doTask('https://youtube.com', 15)">Start</button>
        </div>

        <!-- ৬. ফেসবুক টাস্ক -->
        <div class="task-item">
            <span>ফেসবুক পেজ ফলো ও লাইক</span>
            <button class="btn task-btn" onclick="doTask('https://facebook.com', 10)">Start</button>
        </div>
    </div>

    <!-- ৩. রেফারেল সেকশন -->
    <div class="card">
        <h3>👥 রেফার করে আয় করুন</h3>
        <p style="font-size: 12px; color: #666;">প্রতি রেফারে ১০ টাকা বোনাস পাবেন!</p>
        <div class="ref-box">
            <input type="text" id="ref-link" readonly value="Loading link...">
            <button class="btn task-btn" onclick="copyRefLink()">Copy</button>
        </div>
    </div>

    <!-- ৭. প্রিমিয়াম সাবস্ক্রিপশন (বিকাশ/নগদ) -->
    <div class="card">
        <h3>⭐ প্রিমিয়াম সাবস্ক্রিপশন (১০০ টাকা)</h3>
        <p style="font-size: 12px; color: #555;">
            বিকাশ/নগদ পার্সোনাল (Send Money): <b>017XXXXXXXX</b><br>
            ১০০ টাকা সেন্ড মানি করে নিচে TrxID লিখে সাবমিট করুন:
        </p>
        <input type="text" id="trx-id" placeholder="TrxID (যেমন: 9J83KX10)">
        <button class="btn btn-premium" onclick="submitPremium()">প্রিমিয়াম রিকোয়েস্ট পাঠান</button>
    </div>

    <!-- ৮. টাকা তোলা (Withdraw) -->
    <div class="card">
        <h3>💸 টাকা তুলুন (Withdraw)</h3>
        <p style="font-size: 11px; color: #d35400;">
            ⚠️ শর্ত: সর্বনিম্ন ১০০০ টাকা হতে হবে এবং ২০ জন রেফার থাকতে হবে।
        </p>
        <input type="number" id="withdraw-amount" placeholder="টাকার পরিমাণ (সর্বনিম্ন ১০০০)">
        <input type="text" id="withdraw-number" placeholder="বিকাশ/নগদ নম্বর">
        <button class="btn btn-success" onclick="processWithdraw()">Withdraw করুন</button>
    </div>

    <script>
        const tg = window.Telegram.WebApp;
        tg.expand();

        // ডাটাবেজ সাময়িকভাবে লোকাল স্টোরেজে সেভ রাখার লজিক
        let balance = localStorage.getItem('app_balance') ? parseFloat(localStorage.getItem('app_balance')) : 0;
        let refCount = localStorage.getItem('app_ref_count') ? parseInt(localStorage.getItem('app_ref_count')) : 0;
        let userId = "123456";

        // ইউজার ইনফো লোড
        if (tg.initDataUnsafe && tg.initDataUnsafe.user) {
            const user = tg.initDataUnsafe.user;
            userId = user.id;
            document.getElementById('user-name').innerText = user.first_name + (user.last_name ? " " + user.last_name : "");
            if(user.photo_url) document.getElementById('user-photo').src = user.photo_url;
        } else {
            document.getElementById('user-name').innerText = "Test User";
        }

        // রেফার লিংক সেট করা
        const botUsername = "pocketmoney00bot"; // আপনার বটের ইউজারনেম
        document.getElementById('ref-link').value = `https://t.me/${botUsername}?start=${userId}`;

        function updateUI() {
            document.getElementById('user-balance').innerText = balance;
            document.getElementById('ref-count').innerText = refCount;
            localStorage.setItem('app_balance', balance);
            localStorage.setItem('app_ref_count', refCount);
        }
        updateUI();

        // টাস্ক সম্পূর্ণ করা
        function doTask(url, reward) {
            tg.openLink(url);
            setTimeout(() => {
                balance += reward;
                updateUI();
                tg.showAlert(`টাস্ক সম্পন্ন হয়েছে! +${reward} টাকা যোগ হয়েছে।`);
            }, 3000);
        }

        // এডস দেখা
        function watchAd() {
            tg.showAlert("বিজ্ঞাপন দেখা হচ্ছে...");
            setTimeout(() => {
                balance += 5;
                updateUI();
                tg.showAlert("বিজ্ঞাপন দেখার জন্য +৫ টাকা যোগ করা হয়েছে!");
            }, 2000);
        }

        // রেফার লিংক কপি
        function copyRefLink() {
            const copyText = document.getElementById("ref-link");
            copyText.select();
            navigator.clipboard.writeText(copyText.value);
            tg.showAlert("রেফার লিংক কপি করা হয়েছে!");
        }

        // প্রিমিয়াম রিকোয়েস্ট
        function submitPremium() {
            const trx = document.getElementById('trx-id').value;
            if(!trx) {
                tg.showAlert("অনুগ্রহ করে TrxID লিখুন!");
                return;
            }
            tg.showAlert("আপনার প্রিমিয়াম রিকোয়েস্ট গ্রহন করা হয়েছে। ভেরিফাই হতে কিছুক্ষণ সময় লাগবে।");
            document.getElementById('trx-id').value = "";
        }

        // ৮. টাকা তোলার প্রসেস
        function processWithdraw() {
            const amount = parseFloat(document.getElementById('withdraw-amount').value);
            const number = document.getElementById('withdraw-number').value;

            if(!amount || !number) {
                tg.showAlert("সবগুলো ঘর সঠিকভাবে পূরণ করুন!");
                return;
            }

            // শর্ত চেক
            if (balance < 1000) {
                tg.showAlert("উইথড্র করতে সর্বনিম্ন ১০০০ টাকা ব্যালেন্স লাগবে।");
            } else if (refCount < 20) {
                tg.showAlert(`উইথড্র করার জন্য ২০ টি রেফার প্রয়োজন! (আপনার আছে: ${refCount} টি)`);
            } else if (amount > balance) {
                tg.showAlert("আপনার পর্যাপ্ত ব্যালেন্স নেই।");
            } else {
                balance -= amount;
                updateUI();
                tg.showAlert(`সফল হয়েছে! ${amount} টাকা ${number} নম্বরে প্রসেসিং এ আছে।`);
            }
        }
    </script>
</body>
</html>
