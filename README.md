<!DOCTYPE html>
<html lang="fa">
<head>
  <meta charset="UTF-8">
  <title>🌙 تغییر حالت شب/روز</title>
  <style>
    body {
      margin: 0;
      font-family: sans-serif;
      direction: rtl;
      transition: background 0.4s, color 0.4s;
    }

    .ontainer {
      text-align: center;
      margin-top: 100px;
    }

    .toggle-btn {
      width: 80px;
      height: 40px;
      border-radius: 40px;
      background: #ccc;
      position: relative;
      cursor: pointer;
      margin: 20px auto;
      transition: background 0.3s;
    }

    .circle {
      width: 36px;
      height: 36px;
      background: #fff;
      border-radius: 50%;
      position: absolute;
      top: 2px;
      left: 2px;
      transition: transform 0.3s;
    }

    body.dark {
      background: #121212;
      color: #fff;
    }

    body.dark .toggle-btn {
      background: #333;
    }

    body.dark .circle {
      transform: translateX(40px);
      background: #ffe600;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>🌙 حالت شب / ☀️ حالت روز</h1>
    <p>برای تغییر تم، روی دکمه پایین کلیک کنید:</p>

    <div class="toggle-btn" onclick="toggleMode()">
      <div class="circle"></div>
    </div>

    <p id="statusText">حالت فعلی: روز</p>
  </div>

  <script>
    // خواندن حالت ذخیره‌شده
    if (localStorage.getItem("mode") === "dark") {
      document.body.classList.add("dark");
      document.getElementById("statusText").textContent = "حالت فعلی: شب";
    }

    function toggleMode() {
      document.body.classList.toggle("dark");

      const isDark = document.body.classList.contains("dark");

      // ذخیره‌سازی حالت
      localStorage.setItem("mode", isDark ? "dark" : "light");

      document.getElementById("statusText").textContent =
        isDark ? "حالت فعلی: شب" : "حالت فعلی: روز";
    }
  </script>

</body>
</html>
