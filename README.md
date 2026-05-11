<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Task Bot Dashboard</title>
    <!-- AdsGram ရဲ့ ကြော်ငြာကုဒ်ကို ဤနေရာတွင် ကြိုတင်ချိတ်ဆက်ထားခြင်း ဖြစ်သည် -->
    <script src="adsgram.ai"></script>
    
    <style>
        /* အမည်းရောင် ဒီဇိုင်း ဖြစ်အောင် ပြင်ဆင်ခြင်း */
        body { background-color: #111; color: white; font-family: sans-serif; text-align: center; padding: 20px; }
        .box { border: 1px solid #333; padding: 20px; border-radius: 10px; margin-bottom: 20px; background: #1a1a1a; }
        .btn { background-color: #ffffff; color: black; border: none; padding: 15px 30px; font-weight: bold; border-radius: 5px; cursor: pointer; font-size: 16px; }
    </style>
</head>
<body>
<script src="adsgram.ai"></script>
    <h2>Task12 Rewards Bot</h2>

    <div class="box">
        <p>DAILY REMAINING</p>
        <h1 id="remaining">150</h1>
    </div>

    <div class="box">
        <p>TASK: Open a task bot to watch ads.</p>
        <!-- ကြော်ငြာကြည့်မည့် ခလုတ် -->
        <button class="btn" onclick="watchAd()">TASK 1</button>
    </div>

    <script>
        // လက်တွေ့ AdsGram နှင့် ချိတ်ဆက်မည့် ကုဒ်အပိုင်းအစ
        // (လောလောဆယ် "YOUR_BLOCK_ID" နေရာတွင် AdsGram ကုဒ် အစစ်ထည့်ရမည်)
        const AdController = window.Adsgram ? window.Adsgram.init({ blockId: "YOUR_BLOCK_ID" }) : null;

        function watchAd() {
            if (!AdController) {
                alert("AdsGram နှင့် ချိတ်ဆက်နေဆဲ ဖြစ်သည်။ ဖုန်း Screen ပေါ်တွင် စမ်းသပ်ချက်အဖြစ် ခလုတ်နှိပ်ခြင်း အောင်မြင်ပါသည်။");
                // စမ်းသပ်မှုအဖြစ် Limits ကို ၁ လျှော့ပြခြင်း
                let current = parseInt(document.getElementById('remaining').innerText);
                document.getElementById('remaining').innerText = current - 1;
                return;
            }

            AdController.show().then((result) => {
                alert("ကြော်ငြာကြည့်ရှုမှု အောင်မြင်သည်။");
                // ဤနေရာတွင် ပိုက်ဆံတိုးသည့် စနစ် ဆက်ရေးရမည်
            }).catch((err) => {
                alert("ကြော်ငြာကို ပိတ်လိုက်သဖြင့် မအောင်မြင်ပါ။");
            });
        }
    </script>

</body>
</html>
