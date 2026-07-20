<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PocketMoney - Earn Money</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #0f172a;
            color: #ffffff;
            margin: 0;
            padding: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .container {
            width: 100%;
            max-width: 400px;
        }
        .profile-box {
            display: flex;
            align-items: center;
            background: #1e293b;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 15px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }
        .profile-box img {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            margin-right: 15px;
        }
        .profile-info h3 {
            margin: 0;
            font-size: 16px;
        }
        .profile-info p {
            margin: 5px 0 0;
            font-size: 14px;
            color: #38bdf8;
        }
        .balance-card {
            background: linear-gradient(135deg, #3b82f6, #1d4ed8);
            padding: 20px;
            border-radius: 16px;
            text-align: center;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            margin-bottom: 20px;
        }
        .balance-card h2 {
            margin: 0;
            font-size: 15px;
            color: #e2e8f0;
        }
        .balance-card h1 {
            margin: 10px 0 0;
            font-size: 30px;
        }
        .section-title {
            font-size: 16px;
            margin: 15px 0 10px;
            color: #cbd5e1;
            font-weight: bold;
        }
        .btn {
            background-color: #22c55e;
            color: white;
            border: none;
            width: 100%;
            padding: 14px;
            border-radius: 12px;
            font-size: 15px;
            font-weight: bold;
            cursor: pointer;
            margin-bottom: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            text-align: left;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .btn-tg { background-color: #229ED9; }
        .btn-yt { background-color: #FF0000; }
        .btn-fb { background-color: #1877F2; }
        .btn-ref { background-color: #6366f1; }
        .btn-sub { background-color: #ec4899; }
        .btn-wd { background-color: #eab308; color: #000; justify-content: center; }
    </style>
</head>
<body>

    <div class="container">
        <!-- ১. লোগো এবং ইউজারের নাম ও ব্যালেন্স বক্স -->
        <div class="profile-box">
            <img src="https://i.ibb.co/1Z0p000/logo.png" alt="Logo" id="user-avatar">
            <div class="profile-info">
                <h3 id="username">User Name</h3>
                <p>ID: <span id="user-id">12345678</span></p>
            </div>
        </div>

        <div class="balance-card">
            <h2>আপনার বর্তমান ব্যালেন্স</h2>
            <h1>৳ <span id="balance">০.০০</span></h1>
        </div>

        <!-- ২. টাস্ক পূরণ বা বিজ্ঞাপন দেখার বাটন -->
        <button class="btn" onclick="alert('বিজ্ঞাপন লোড হচ্ছে...')">🎬 দৈনিক বিজ্ঞাপন দেখুন <span>➡️</span></button>

        <!-- ৩. রেফার করার লিংক কপি করার অপশন -->
        <button class="btn btn-ref" onclick="alert('আপনার রেফারেল লিংক কপি করা হয়েছে!')">👥 বন্ধুদের রেফার করুন <span>➡️</span></button>

        <div class="section-title">সোশ্যাল টাস্ক ও ইনকাম</div>

        <!-- ৪. টেলিগ্রাম চ্যানেল টাস্ক -->
        <button class="btn btn-tg" onclick="alert('টেলিগ্রাম চ্যানেলে জয়েন করুন!')">📢 টেলিগ্রাম চ্যানেল জয়েন টাস্ক <span>➡️</span></button>

        <!-- ৫. ইউটিউব চ্যানেল টাস্ক -->
        <button class="btn btn-yt" onclick="alert('ইউটিউব সাবস্ক্রাইব, লাইক ও শেয়ার করুন!')">▶️ ইউটিউব সাবস্ক্রাইব ও লাইক <span>➡️</span></button>

        <!-- ৬. ফেসবুক পেজ টাস্ক -->
        <button class="btn btn-fb" onclick="alert('ফেসবুক পেজ ফলো, লাইক ও শেয়ার করুন!')">👍 ফেসবুক পেজ ফলো ও লাইক <span>➡️</span></button>

        <div class="section-title">পেমেন্ট ও সাবস্ক্রিপশন</div>

        <!-- ৭. বিকাশ এবং নগদ এ ১০০ টাকা সেন্ট মানি করে প্রিমিয়াম সাবস্ক্রিপশন -->
        <button class="btn btn-sub" onclick="alert('বিকাশ/নগদ নাম্বারে ১০০ টাকা Send Money করে ট্রানজেকশন আইডি দিন।')">💎 প্রিমিয়াম সাবস্ক্রিপশন (বিকাশ/নগদ ১০০৳) <span>➡️</span></button>

        <!-- ৮. টাকা তোলার (Withdraw) বাটন সাথে শর্ত -->
        <button class="btn btn-wd" onclick="alert('সতর্কতা: টাকা তুলতে হলে সর্বনিম্ন ৳১০০০ টাকা এবং কমপক্ষে ১৫টি রেফার থাকতে হবে!')">💳 টাকা তুলুন (Withdraw) <span>🔒</span></button>
    </div>

</body>
</html>


