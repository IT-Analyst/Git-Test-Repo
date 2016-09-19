#  Git Test Repository


Mit diesem Git-Repository soll der Umgang mit git gelernt werden. Es können beliebig Dateien hinzugefügt und verändert werden.

* Klonen des Repo

  `git clone https://github.com/IT-Analyst/Git-Test-Repo.git`

  ![git-clone](https://cloud.githubusercontent.com/assets/9308836/18434839/f58644ee-78ef-11e6-9d60-5bf90a315d69.jpg)

* Eine neue Datei erzeugen

  Erstellen Sie mit einem Editor eine neue Datei. Zum Beispiel `vorname_nachname.txt`

* Status anzeigen

  `git status`

  ![git-status](https://cloud.githubusercontent.com/assets/9308836/18434848/fbbb780c-78ef-11e6-82d0-1b95d02b0a6c.jpg)

* Datei zu Git hinzufügen:

  `git add vorname_nachname.txt`

  Die Datei ist jetzt für den nächsten Commit vorgemerkt.

* Commit erzeugen

  Der Befehl `git commit -v` öffnet einen Editor (default vim). Hier wird die Commit-Nachricht verfasst. Mit '-v' werden noch alle Änderungen an den Dateien im Editor angezeigt.

  ![git-commit](https://cloud.githubusercontent.com/assets/9308836/18434841/f6e42bee-78ef-11e6-8d2b-dd463ebaf4ab.jpg)

* Git History anzeigen

  `git log`

  ![git-log](https://cloud.githubusercontent.com/assets/9308836/18434842/f8b26a30-78ef-11e6-86ef-344621f41534.jpg)

* Änderungen dem Server bekannt machen

  Mit `git push origin master` werden die lokalen Änderungen zum Server geschickt. 'master' bezeichnet hierbei den Entwicklungszweig.

    ![git-push](https://cloud.githubusercontent.com/assets/9308836/18434846/fa48b200-78ef-11e6-9bb8-d35bb93223fa.jpg)


* Änderungen vom Server holen

  Mit `git fetch` werden Änderungen vom Server abgefragt ohne die lokale Arbeitskopie zu verändern. Durch den Befehl `git pull origin master` werden die Änderungen vom Server abgefragt und mit dem lokalen Arbeitsverzeichnis verschmolzen.

  Ausfüren von `git log` (oneline) -> `git fetch` -> `git log` (oneline)

 ![git-fetch](https://cloud.githubusercontent.com/assets/9308836/18435240/4e01c51a-78f2-11e6-89d9-7673c1b82c49.jpg)

 ![screenshot 1473682072](https://cloud.githubusercontent.com/assets/9308836/18435252/652f61ac-78f2-11e6-83e0-5e7d55ae4b3f.jpg)

 Ausführen von `git log` (oneline) -> `git pull` -> `git log` (oneline)

 ![screenshot 1473682252](https://cloud.githubusercontent.com/assets/9308836/18435347/d55d7842-78f2-11e6-8e62-34c5a34c4c1d.jpg)

* Erzeugen eines neuen Zweiges

  `git branch <name>` erstellt einen neuen lokalen Zweig.

  Mit `git branch --list` können alle Zweige angezeigt werden. Der aktuell aktive Branch ist mit einem Stern markiert.

  ![screenshot 1473754851](https://cloud.githubusercontent.com/assets/9308836/18466407/e6d70aa8-799b-11e6-9050-f7814fc1566b.jpg)

  Durch Ausführen von `git checkout develop` können wir den Branch wecheln.

* Zusammenführen von zwei Zweigen

  Wenn wir uns im master-branch befinden und `git merge develop` aufrufen werden die Änderungen aus dem develop-branch in den Hauptzweig eingefügt. Hier wurde jetzt absichtlich ein Konflikt herbeigeführt, der nicht automatisch durch Git aufgelöst werden kann.

  Mit `git mergetool` wird das eingestellte Werzeug geöffnet. Hier jetzt P4Merge. Wenn die Datei im Mergetool gespeichert wird und das Werkzeug geschlossen wird, werden die bearbeiteten Dateien für den nächsten Commit vorgemerkt (Ist in der Gitconfig trustExitCode = false eingestellt wird noch einen Datei name.orig angelegt).

  ![screenshot 1473769008](https://cloud.githubusercontent.com/assets/9308836/18473437/4219643a-79bd-11e6-8374-538604bc02a5.jpg)

  Das Mergetool P4Merge zeigt 4 Bereiche an: Zweig 1, den gemeinsamen Ursprung, Zweig 2 und das Ergebnis.

  ![screenshot 1473768864](https://cloud.githubusercontent.com/assets/9308836/18473434/3ef57c44-79bd-11e6-9bcb-1a8c2865d1ec.jpg)

  Mit `git commit -v` kann nun der Merge-Commit erzeugt werden.

  ![screenshot 1473769045](https://cloud.githubusercontent.com/assets/9308836/18473656/6b71ea9a-79be-11e6-9805-13814f8e1d9a.jpg)

  Merge-Commit in der Git-History (HEAD zeigt auf Master):

  ![screenshot 1473769092](https://cloud.githubusercontent.com/assets/9308836/18473657/6d293e6a-79be-11e6-841a-b79a0e1aee23.jpg)

  Danach wurde mit `git checkout develop` wieder in den Develop-Zweig gewechselt und ein Fast-Forward Merge zum   Master-Zweig durchgeführt. HEAD, develop und master sind auf dem selben Stand. Der Server (origin/master) steht noch weiter hinten.

  ![screenshot 1473769151](https://cloud.githubusercontent.com/assets/9308836/18473659/6e92a642-79be-11e6-8766-18fa2dde89ca.jpg)
