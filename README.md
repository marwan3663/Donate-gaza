<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ادعم غزة</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Cairo', sans-serif;
      background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://upload.wikimedia.org/wikipedia/commons/6/63/Gaza_strip_2021.jpg') no-repeat center center fixed;
      background-size: cover;
      color: white;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 500px;
      margin: 50px auto;
      background: rgba(0, 0, 0, 0.7);
      padding: 30px;
      border-radius: 15px;
      text-align: center;
    }
    h1 {
      font-size: 32px;
      margin-bottom: 20px;
    }
    label {
      display: block;
      margin-top: 15px;
      font-size: 18px;
    }
    input, select {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border-radius: 5px;
      border: none;
      font-size: 16px;
    }
    button {
      margin-top: 20px;
      padding: 12px 20px;
      font-size: 18px;
      background-color: #28a745;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      width: 100%;
    }
    .thank-you {
      display: none;
      font-size: 20px;
      margin-top: 30px;
      background-color: #198754;
      padding: 20px;
      border-radius: 10px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>ادعم غزة</h1>

    <label for="amount">اختر المبلغ (5 - 500 جنيه):</label>
    <input type="number" id="amount" min="5" max="500" value="50">

    <label for="method">اختر طريقة الدفع:</label>
    <select id="method">
      <option value="vodafone">فودافون كاش</option>
      <option value="instapay">InstaPay</option>
      <option value="sms">رسالة نصية</option>
    </select>

    <button onclick="donate()">تبرع الآن</button>

    <div class="thank-you" id="thankYou">شكرًا لك! تم تسجيل تبرعك، بارك الله فيك على دعمك لأهل غزة.</div>
  </div>

  <script>
    function donate() {
      const amount = document.getElementById('amount').value;
      const method = document.getElementById('method').value;
      const number = "01069277557";
      if (amount < 5 || amount > 500) {
        alert("الرجاء إدخال مبلغ بين 5 و 500 جنيه");
        return;
      }

      if (method === "vodafone") {
        alert(`قم بتحويل ${amount} جنيه إلى رقم فودافون كاش: ${number}`);
      } else if (method === "instapay") {
        window.location.href = `instapay://send?recipient=${number}&amount=${amount}`;
      } else if (method === "sms") {
        window.location.href = `sms:${number}?body=تبرع لغزة بقيمة ${amount} جنيه`;
      }

      document.getElementById('thankYou').style.display = 'block';
    }
  </script>
</body>
</html>
