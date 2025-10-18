// Experimentelles Gesalten: Abgabe von der Aufgabe (Alina Böhm, CVD 1)

// Soundimput Visualisieren - Idee: Dino der "spricht", wenn man ins Mikrofon redet

let mic; // Damit wird das Mic gespeichert
let mouthOpen = 0; // Das ist die Mundbewegung

function setup() { // Das bedeutet, dass es einmal am Anfang läuft
  createCanvas(400, 400); // Erzeugt Fenster von 400x400 Pixeln
  mic = new p5.AudioIn(); // Erstellt Mic-Obj.
  mic.start(); // Startet das Mic (Zugriff erlauben drücken!)
}

function draw() { // Das bedeuted, dass es immer wieder läuft
  background(190,248,207) // Hintergrund Farbe (hellgrün)

  let vol = mic.getLevel(); //Lautstärke vom Mic
  // -> Gibt einen Wert zwischen 0 (leise) und 1 (laut) zurück
  
  // Lautstärke (0-0.3) umrechnen in Mundhöhe (0-30 Pixel)
  mouthOpen = map(vol, 0, 0.3, 0, 30); // je lauter, desto weiter öffnet sich der Mund
  // -> "vol" für Volumen der Box
  // -> map  um die Lautstärke (0-0.3) in eine Bewegung (0-30-Pixel) umzuwandeln

  // Boden
  fill(105,122,109); // Farbe (grau mit hellgrün)
  rect(0, 330, width, 70) // Rechteck (x,y = Breite, Höhe, Rundung) -> Breite
 noStroke() 
  
  // Schwanz
  fill(100, 200, 100);
  triangle(126, 240, 60, 220, 131, 270) // Dreieck (x1,y1, x2,y2, x3,y3)
  // -> jeder Punkt (insgesamt drei) mit jeweils zwei Koordinaten
  
  // Beine
  rect(155, 285, 20, 50, 5); // Rechteck (x,y = Breite, Höhe, Rundung; x,y = Länge, Weite)
  rect(225, 285, 20, 50, 5); // Rechteck (x,y = Breite, Höhe, Rundung; x,y = Länge, Weite)
  
  // Zacken (also die Stacheln am Rücken)
  fill(154,46,46) // Farbe (rot)
  triangle(140, 219, 150, 170, 175, 203) // wieder Dreieck (x1,y1, x2,y2, x3,y3)
  triangle (192, 200, 210, 160, 230, 204) // Dreieck
  
  // Körper vom Dino
  fill(100, 200, 100); // Farbe (grün)
  ellipse(200, 250, 150, 100); // Ellipse (x,y ; x,y = Breite, Höhe; Länge, Weite)

  // Kopf
  fill(100, 200, 100); // Farbe (grün)
  ellipse(280, 200, 100, 80); // wieder Ellipse (x,y ; x,y = Breite, Höhe; Länge, Weite)

  // Auge
  fill(255); // Farbe (weiß)
  ellipse(282, 190, 20, 20); // Ellipse 
  fill(0); // Farbe (schwarz) -> Für die Pupille
  ellipse(285, 190, 10, 10); // Ellipse

  // Mund
  fill(45,124,71) // Farbe (dunkelgrün)
  rect(270, 215, 60, mouthOpen +5, 5); // Rechteck (x,y = Breite, Höhe, Rundung)

  // Sprechblase mit dem Wort "rawr"
  if (mouthOpen > 5) { // -> Wenn der Dino laut genug "spricht" sozusagen
    fill(255); // Farbe (weiß) -> für die Sprechblase
    triangle(300,155, 320, 110, 340, 130) // Dreieck
    ellipse(340, 120, 80, 50); // Ellipse

    
    fill(0); // Farbe (schwarz) -> für die Schrift
    textSize(20); // Größe des Textes
    textAlign(CENTER, CENTER); // Text soll in der Mitte der Ellipse (Sprechblase) sein
    text("rawr", 340, 120); // Text (mit x,y Wert)
  }
}

// Ende
