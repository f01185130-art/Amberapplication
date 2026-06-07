// ================= VOCAB (NO REPEAT) =================
const vocab = [
["das Krankenhaus","hospital"],
["die Station","ward"],
["der Patient","patient"],
["die Pflege","care"],
["das Medikament","medication"],
["der Schmerz","pain"],
["Fieber","fever"],
["Husten","cough"],
["Atemnot","shortness of breath"],
["die Tablette","tablet"],
["die Spritze","injection"],
["die Infusion","infusion"],
["waschen","to wash"],
["mobilisieren","to mobilize"],
["Blutdruck","blood pressure"],
["Puls","pulse"],
["Temperatur","temperature"],
["Notfall","emergency"],
["bewusstlos","unconscious"],
["die Wunde","wound"],
["der Verband","bandage"],
["desinfizieren","disinfect"],
["die Haut","skin"],
["der Katheter","catheter"],
["Demenz","dementia"],
["Rollstuhl","wheelchair"],
["Pflegeheim","nursing home"],
["Dokumentation","documentation"],
["Team","team"],
["Pflegeplan","care plan"]
];

let vocabQueue = [];
let current;

// shuffle function
function shuffle(array) {
  for (let i = array.length - 1; i > 0; i--) {
    let j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]];
  }
}

// start vocab
function startVocab() {
  hideAll();
  document.getElementById("vocab").classList.remove("hidden");

  vocabQueue = [...vocab]; // copy all words
  shuffle(vocabQueue);     // shuffle once

  nextWord();
}

// next word (NO REPEAT)
function nextWord() {
  if (vocabQueue.length === 0) {
    // reset after all used
    vocabQueue = [...vocab];
    shuffle(vocabQueue);
