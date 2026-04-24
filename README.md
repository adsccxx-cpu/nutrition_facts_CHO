# nutrition_facts_CHO

<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>兒童碳水計算器</title>

<style>
body {
  font-family: -apple-system, BlinkMacSystemFont;
  background: #f7f9fc;
  text-align: center;
  padding: 20px;
}

h1 {
  font-size: 26px;
}

.card {
  background: white;
  border-radius: 16px;
  padding: 16px;
  margin: 12px auto;
  max-width: 400px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}

input {
  width: 80%;
  padding: 10px;
  margin: 6px;
  font-size: 16px;
  border-radius: 10px;
  border: 1px solid #ccc;
}

button {
  padding: 12px 16px;
  margin: 6px;
  border: none;
  border-radius: 12px;
  font-size: 16px;
  cursor: pointer;
}

.portion-btn {
  width: 45%;
}

.result {
  font-size: 20px;
  margin-top: 10px;
}

.small {
  font-size: 14px;
  color: gray;
}
</style>
</head>

<body>

<h1>🍪 吃了多少？</h1>

<div class="card">
  <h3>家長設定</h3>

  <label>👉 模式：</label><br>
  <select id="mode" onchange="toggleMode()">
    <option value="package">整包輸入（推薦）</option>
    <option value="serving">每份輸入</option>
  </select>

  <div id="packageMode">
    <input id="carbPackage" type="number" placeholder="每包碳水 (g)">
    <input id="kcalPackage" type="number" placeholder="每包熱量 (kcal)">
  </div>

  <div id="servingMode" style="display:none;">
    <input id="carbServing" type="number" placeholder="每份碳水 (g)">
    <input id="kcalServing" type="number" placeholder="每份熱量 (kcal)">
    <input id="servings" type="number" placeholder="每包幾份">
  </div>
</div>

<div class="card">
  <h3>你吃了多少？</h3>

  <button class="portion-btn" onclick="calculate(0.25)">🟡 一點點 （1/4） </button>
  <button class="portion-btn" onclick="calculate(0.5)">🟢 一半 （1/2） </button>
  <button class="portion-btn" onclick="calculate(0.75)">🔵 大部分（3/4）</button>
  <button class="portion-btn" onclick="calculate(1)">🟣 一包</button>
  <button class="portion-btn" onclick="calculate(1.5)">🔴 多吃/1.5包（瓶）</button>
  <button class="portion-btn" onclick="calculate(2)">🔥 兩包（瓶）</button>
</div>

<div class="card">
  <h3>結果</h3>
  <div class="result" id="carbResult">碳水：0 g</div>
  <div class="result" id="kcalResult">熱量：0 kcal</div>
  <div class="result" id="exchangeResult">碳水份數：0</div>
  <div class="small" id="feedback"></div>
</div>

<script>
function toggleMode(){
  let mode = document.getElementById("mode").value;
  document.getElementById("packageMode").style.display =
    mode === "package" ? "block" : "none";
  document.getElementById("servingMode").style.display =
    mode === "serving" ? "block" : "none";
}

function calculate(portion){

  let mode = document.getElementById("mode").value;

  let carb = 0;
  let kcal = 0;

  if(mode === "package"){
    carb = parseFloat(document.getElementById("carbPackage").value);
    kcal = parseFloat(document.getElementById("kcalPackage").value);
  } else {
    let carbServing = parseFloat(document.getElementById("carbServing").value);
    let kcalServing = parseFloat(document.getElementById("kcalServing").value);
    let servings = parseFloat(document.getElementById("servings").value);

    carb = carbServing * servings;
    kcal = kcalServing * servings;
  }

  if(isNaN(carb) || isNaN(kcal)){
    alert("請先輸入數值");
    return;
  }

  let actualCarb = carb * portion;
  let actualKcal = kcal * portion;

  let exchange = actualCarb / 15;

  document.getElementById("carbResult").innerText =
    "碳水：" + actualCarb.toFixed(1) + " g";

  document.getElementById("kcalResult").innerText =
    "熱量：" + actualKcal.toFixed(0) + " kcal";

  document.getElementById("exchangeResult").innerText =
    "碳水份數：" + exchange.toFixed(1);

  let feedback = "";
  if(exchange < 1) feedback = "👍 吃得不多";
  else if(exchange < 3) feedback = "👌 還可以";
  else feedback = "⚠ 有點多喔";

  document.getElementById("feedback").innerText = feedback;
}
</script>

</body>
</html>
