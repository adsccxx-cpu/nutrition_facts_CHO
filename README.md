
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>碳水計算器</title>

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

<h1>🍪 吃了多少碳水？</h1>

<div class="card">
  <h3>請閲讀食物包裝上的「營養標示」方框</h3>

  <label>👉 只需輸入營養標示方框中「碳水化合物」公克數，不需加上「糖」公克數</label><br>

  <div id="servingMode" style="display:none;">
    <input id="carbServing" type="number" placeholder="每份碳水化合物 (公克)">
    <input id="servings" type="number" placeholder="本包裝含幾份">
  </div>
</div>

<div class="card">
  <h3>你吃了多少？</h3>

  <button class="portion-btn" onclick="calculate(0.25)">🟡 一點點 （1/4） </button>
  <button class="portion-btn" onclick="calculate(0.5)">🟢 一半 （1/2） </button>
  <button class="portion-btn" onclick="calculate(0.75)">🔵 大部分（3/4）</button>
  <button class="portion-btn" onclick="calculate(1)">🟣 整個吃完</button>
  <button class="portion-btn" onclick="calculate(1.5)">🔴 吃了1.5包（1又1/2）</button>
  <button class="portion-btn" onclick="calculate(2)">🔥 吃了2包 </button>
    <button class="portion-btn" onclick="calculate(3)">🔥 吃了3包 </button>
      <button class="portion-btn" onclick="calculate(4)">🔥 吃了4包 </button>
</div>

<div class="card">
  <h3>結果</h3>
  <div class="result" id="carbResult">總共吃了碳水化合物：0 公克</div>
  <div class="result" id="exchangeResult">換算成主食份數：0 份</div>
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
    "碳水化合物：" + actualCarb.toFixed(1) + " 公克";

  document.getElementById("exchangeResult").innerText =
    "碳水份數：" + exchange.toFixed(1);

  let feedback = "";
  if(exchange < 1) feedback = "👍 一份主食，剛剛好";
  else if(exchange < 3) feedback = "👌 2～3份主食，可以增加半小時運動消耗";
  else feedback = "⚠ 超過3份主食（八分滿飯），當作點心的話有點多喔";

  document.getElementById("feedback").innerText = feedback;
}
</script>

</body>
</html>
