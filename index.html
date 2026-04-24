<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>碳水計算器</title>

<style>
body {
  font-family: -apple-system, BlinkMacSystemFont;
  background: #f4f6fb;
  text-align: center;
  padding: 20px;
}

h1 {
  font-size: 24px;
}

.card {
  background: white;
  border-radius: 16px;
  padding: 18px;
  margin: 12px auto;
  max-width: 420px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.08);
}

input {
  width: 85%;
  padding: 12px;
  margin: 8px;
  font-size: 16px;
  border-radius: 10px;
  border: 1px solid #ccc;
}

button {
  padding: 12px;
  margin: 6px;
  border: none;
  border-radius: 12px;
  font-size: 15px;
  cursor: pointer;
  width: 45%;
  background: #e8edff;
}

button:hover {
  background: #d6ddff;
}

.result {
  font-size: 20px;
  margin-top: 10px;
  font-weight: bold;
}

.small {
  font-size: 14px;
  color: gray;
}
</style>
</head>

<body>

<h1>🍪 吃了多少碳水？</h1>

<div class="card">
  <h3>① 看營養標示</h3>

  <input id="carbServing" type="number" placeholder="每份碳水 (公克)">
  <input id="servings" type="number" placeholder="本包裝幾份">

  <div class="small">👉 只看「碳水化合物」，不用加糖</div>
</div>

<div class="card">
  <h3>② 你吃了多少？</h3>

  <button onclick="calculate(0.25)">1/4</button>
  <button onclick="calculate(0.5)">1/2</button>
  <button onclick="calculate(0.75)">3/4</button>
  <button onclick="calculate(1)">1包</button>
  <button onclick="calculate(1.5)">1.5包</button>
  <button onclick="calculate(2)">2包</button>
</div>

<div class="card">
  <h3>③ 結果</h3>

  <div class="result" id="carbResult">碳水：0 g</div>
  <div class="result" id="exchangeResult">主食份數：0 份</div>
  <div class="small" id="feedback"></div>
</div>

<script>
function calculate(portion){

  let carbServing = parseFloat(document.getElementById("carbServing").value);
  let servings = parseFloat(document.getElementById("servings").value);

  if(isNaN(carbServing) || isNaN(servings)){
    alert("請先輸入數值");
    return;
  }

  let totalCarb = carbServing * servings;
  let actualCarb = totalCarb * portion;
  let exchange = actualCarb / 15;

  document.getElementById("carbResult").innerText =
    "碳水：" + actualCarb.toFixed(0) + " g";

  document.getElementById("exchangeResult").innerText =
    "主食份數：" + exchange.toFixed(1);

  let feedback = "";
  if(exchange < 1) feedback = "👍 1份內 OK";
  else if(exchange < 3) feedback = "👌 建議增加活動量";
  else feedback = "⚠ 碳水偏多";

  document.getElementById("feedback").innerText = feedback;
}
</script>

</body>
</html>