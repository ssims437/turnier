# Turnier

**Wie aus lauter Eigennutz Zusammenarbeit wird.** Das Gefangenendilemma einmal gespielt ist
eindeutig und trostlos. Zweihundertmal hintereinander gespielt wird es das Gegenteil. Zehn
Strategien, jeder gegen jeden, jedes Duell Zug für Zug — und die Frage, was passiert, wenn man
sich vertut.

→ **[Blatt öffnen](https://ssims437.github.io/turnier/)**

- **Jeder gegen jeden** als Wärmebild — Punkteschnitt je Runde, alle 100 Begegnungen
- **Ein Duell Zug für Zug** — zwei Strategien wählen und die ersten 80 Runden als Farbstreifen
  sehen; unter Rauschen wird die Vergeltungsschleife sichtbar
- **Rangliste** und **Evolution** über bis zu 400 Generationen (Replikatordynamik)
- **Rauschen am Regler** — was ein Prozent Versehen anrichtet
- **Prüflauf** — sieben Zeilen, darunter die Einladungsschwelle gegen ihre Herleitung

## Die zehn Strategien

| | Verhalten |
|---|---|
| **Immer nett** | kooperiert immer |
| **Immer fies** | verrät immer — im Einzelspiel unschlagbar |
| **Wie du mir** | kooperiert zuerst, dann spiegelt sie den letzten Zug |
| **Nachtragend** | kooperiert bis zum ersten Verrat, danach nie wieder |
| **Großzügig** | wie du mir, verzeiht aber in drei von zehn Fällen grundlos |
| **Zwei Vergehen** | schlägt erst nach zwei Verraten in Folge zurück |
| **Pawlow** | bleibt beim Zug, wenn er sich gelohnt hat, sonst wechselt sie |
| **Zufall** | wirft jedes Mal eine Münze |
| **Prüfer** | testet früh mit einem Verrat und beutet aus, wer nicht reagiert |
| **Misstrauisch** | wie du mir, fängt aber mit einem Verrat an |

## Was der Prüflauf zeigt

| Behauptung | Ergebnis |
|---|---|
| es ist wirklich ein Dilemma | T > R > P > S ✓ · 2R > T+S ✓ · Verraten dominiert gegen **jede** Antwort |
| jeder Punkt ist zweimal gezählt | 100 Duelle über 12 000 Runden, aus dem Zugprotokoll neu addiert · 0 Abweichungen |
| **„Wie du mir" gewinnt kein einziges Duell** | **30 Duelle, 0 gewonnen**, größter Vorsprung 0 — und im Turnier trotzdem **Platz 2** |
| **ein Prozent Versehen zerstört Vertrauen** | bei 2 % Rauschen fällt „Wie du mir" mit sich selbst auf **53,7 %** Kooperation, „Großzügig" hält 93,9 % |
| die Dynamik erhält, was sie erhalten muss | Summe bleibt 1 (3,3·10⁻¹⁶) · 0 negative Anteile · alle 10 reinen Zustände sind Fixpunkte |
| **wie viele Kooperierende es mindestens braucht** | gemessen **0,252 %**, hergeleitet 0,252 % — genau **1/(2n−3)** · Abstand 4,2·10⁻¹⁷ |
| dasselbe Turnier kommt zweimal gleich heraus | 0 abweichende Felder auch mit Rauschen · 64 gespiegelte Duelle, 0 Abweichungen |

## Die Einladungsschwelle

Wie groß muss eine Gruppe von Kooperierenden mindestens sein, um in einer Welt aus lauter
Verrätern zu wachsen statt zu verschwinden? Man kann es simulieren, und man kann es herleiten.
Mit `a = nR`, `b = S+(n−1)P`, `c = T+(n−1)P`, `d = nP` ist die Schwelle `(d−b)/(a−b−c+d)` — bei den
üblichen Auszahlungen 5/3/1/0 genau

```
        1
x* = ────────       bei n = 200 Runden:  0,252 %
      2n − 3
```

Der Prüflauf sucht diese Schwelle durch Bisektion in der Simulation und vergleicht: Abstand
**4,2·10⁻¹⁷**. Die Aussage dahinter ist die eigentliche Pointe des ganzen Blattes — es braucht
**erstaunlich wenige**, damit Zusammenarbeit Fuß fasst, solange sie sich untereinander begegnen.

## Was mich das gekostet hat

**Der Sieger war nicht der, den ich erwartet hatte.** Bei 200 Runden ohne Rauschen gewinnt in
diesem Feld nicht „Wie du mir", sondern **„Großzügig"** — knapp. Der Reflex ist, die
Bedingungen so lange zu drehen, bis die Legende stimmt. Stattdessen sagt es das Blatt jetzt
selbst: *Ein Turnier ist kein Beweis, es ist eine Messung unter bestimmten Bedingungen.* Wer
gewinnt, hängt am Teilnehmerfeld — bei Axelrod war es ein anderes. Was **unabhängig vom Feld**
gilt, steht in der dritten Prüfzeile: „Wie du mir" kann kein Duell gewinnen und landet trotzdem
oben.

**`hsl(210 52% var(--hell))` ist im Canvas kein Fehler, sondern ein Nichts.** Canvas kennt keine
CSS-Variablen. Eine ungültige `fillStyle` wird nicht etwa gemeldet, sondern **stillschweigend
ignoriert** — der vorherige Wert bleibt stehen. Da der vorherige Wert die Hintergrundfarbe war,
habe ich das Evolutionsdiagramm sauber in sich selbst gemalt: ein perfekt leeres Rechteck, kein
Fehler in der Konsole, kein roter Prüflauf. Das Blatt prüft Zahlen, keine Pixel — gefunden habe
ich es erst beim Hinsehen.

**Ein Zufallsstrom für zwei Spieler macht die Sitzordnung wichtig.** Die Prüfzeile „seitenverkehrt
kommt dasselbe heraus" schlug in 3 von 100 Paarungen fehl. Ursache: Beide Strategien zogen aus
**demselben** Strom, und wer zuerst zieht, hängt davon ab, wer links sitzt. Zwei Korrekturen
folgten: Jede Seite hat jetzt ihren eigenen Strom (und das Rauschen einen dritten) — und die
Prüfung nimmt die würfelnden Strategien ausdrücklich **aus**, statt sie stillschweigend
mitlaufen zu lassen. Wer würfelt, spielt seitenverkehrt zu Recht anders.

**Was das Blatt nicht kann:** keine lernenden Gegner, keine Strategien mit Gedächtnis über mehr
als die letzten Züge, keine Reputation über Dritte (das ist indirekte Reziprozität und ein eigenes
Thema), keine räumliche Nachbarschaft (die ändert das Ergebnis erheblich — Kooperation überlebt
in Clustern viel leichter), keine Evolution mit Mutation, kein unbekanntes Spielende. Die
Replikatordynamik beschreibt außerdem eine **unendlich große** Population; in kleinen kann eine
Strategie durch Zufall aussterben, obwohl sie überlegen ist.

## Technik

Eine einzelne HTML-Datei. Kein Build, keine Bibliothek, nichts verlässt den Browser.
Rundenturnier, Replikatordynamik, xorshift-Zufall mit Saat, Canvas 2D, hell und dunkel.

## Die ganze Sammlung

Alle Blätter nach Feld geordnet, jedes mit eigenem Repo:
**[ssims437.github.io](https://ssims437.github.io/)**

## Lizenz

MIT
