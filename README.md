# ALAB-SA7
العــبها صــح
let team1Score = 0;
let team2Score = 0;
let currentTeam = 1;
let x2Used = false;

function updateScores() {
  document.getElementById("score1").innerText = team1Score;
  document.getElementById("score2").innerText = team2Score;
}

function selectQuestion(button, points) {
  button.disabled = true;
  let actualPoints = x2Used ? points * 2 : points;

  const isCorrect = confirm("هل الإجابة صحيحة؟");
  if (isCorrect) {
    if (currentTeam === 1) {
      team1Score += actualPoints;
    } else {
      team2Score += actualPoints;
    }
  }

  x2Used = false;
  updateScores();
  switchTeam();
}

function switchTeam() {
  currentTeam = currentTeam === 1 ? 2 : 1;
  alert(`دور الفريق ${currentTeam}`);
}

function useX2(button) {
  if (x2Used) return;
  x2Used = true;
  button.disabled = true;
  showAlert("تم تفعيل مضاعفة النقاط!");
}

function useCallFriend(button) {
  button.disabled = true;
  showAlert("تم استخدام اتصال بصديق!");
}

function showAlert(text) {
  const alertBox = document.createElement("div");
  alertBox.innerText = text;
  alertBox.style.position = "fixed";
  alertBox.style.top = "40%";
  alertBox.style.left = "50%";
  alertBox.style.transform = "translate(-50%, -50%)";
  alertBox.style.background = "#222";
  alertBox.style.color = "#fff";
  alertBox.style.padding = "20px";
  alertBox.style.borderRadius = "12px";
  alertBox.style.fontSize = "20px";
  alertBox.style.zIndex = 1000;
  document.body.appendChild(alertBox);

  setTimeout(() => {
    alertBox.remove();
  }, 2000);
}
