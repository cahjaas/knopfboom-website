// script.js
let counter = 0;

function increaseCounter() {
  counter++;
  document.getElementById("counter").textContent = counter;

  if (counter === 1000) {
    explodeButton();
  }
}

function explodeButton() {
  const button = document.getElementById("redButton");
  const explosion = document.getElementById("explosionEffect");
  const message = document.getElementById("message");
  const explosionSound = document.getElementById("explosionSound");
  const resetButton = document.getElementById("resetButton");

  // Explosionseffekt anzeigen und starten
  explosion.style.display = "block";
  explosion.style.animation = "explode 1s ease-out forwards";

  // Knopf wird unsichtbar
  button.style.transition = "transform 0.5s ease";
  button.style.transform = "scale(0)";  // Knopf verschwindet

  // Explosion Sound abspielen
  explosionSound.play();

  // Nachricht anzeigen
  message.textContent = "BOOM! Du hast 1000 erreicht!";
  message.style.color = "red";

  // Den Reset-Button anzeigen
  resetButton.style.display = "block";

  // Entfernen des Knopfs nach der Explosion
  setTimeout(() => {
    button.style.display = "none";
  }, 1000); // Nach der Explosion wird der Knopf entfernt
}

// Reset-Funktion
function resetGame() {
  // Den Zähler zurücksetzen
  counter = 0;
  document.getElementById("counter").textContent = counter;

  // Den Knopf wieder sichtbar machen
  const button = document.getElementById("redButton");
  button.style.display = "inline-block";
  button.style.transform = "scale(1)";

  // Die Explosion und die Nachricht zurücksetzen
  const explosion = document.getElementById("explosionEffect");
  explosion.style.display = "none";

  const message = document.getElementById("message");
  message.textContent = "";

  // Den Reset-Button wieder unsichtbar machen
  const resetButton = document.getElementById("resetButton");
  resetButton.style.display = "none";
}
