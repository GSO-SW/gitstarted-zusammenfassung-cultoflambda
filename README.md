# Richtiges Arbeiten mit Git und GitHub

## Inhalt
  - [Was sind Git und GitHub und wofür werden die Systeme verwendet?](#was-sind-git-und-github-und-wofür-werden-die-systeme-verwendet)
    - [Versionskontrollsysteme - von Paul von Napolski](#versionskontrollsysteme---von-paul-von-napolski)
      - [Git - von Paul von Napolski](#git---von-paul-von-napolski)
    - [GitHub - Von Felix Andreas Assert](#github---von-felix-andreas-assert)
  - [Wie funktioniert Git? - von Patrick Scheuer](#wie-funktioniert-git---von-patrick-scheuer)
  - [Wie funktioniert Git? (Alternative Beschreibung) - von Paul von Napolski](#wie-funktioniert-git-alternative-beschreibung---von-paul-von-napolski)
    - [Commits - von Paul von Napolski](#commits---von-paul-von-napolski)
    - [Branches und HEAD](#branches-und-head)
    - [Merge und Rebase](#merge-und-rebase)
    - [Commits als Wiederherstellungspunkte](#commits-als-wiederherstellungspunkte)
  - [Was sind Remote-Repositoris und wie funktionieren sie? - von Paul von Napolski](#was-sind-remote-repositoris-und-wie-funktionieren-sie---von-paul-von-napolski)
    - [Remote Branches - von Paul von Napolski](#remote-branches---von-paul-von-napolski)
    - [Origin](#origin)
    - [GitHub als Remote Repository - Von Felix Andreas Assert](#github-als-remote-repository---von-felix-andreas-assert)
  - [Best-Practices - von Weiting Zhou](#best-practices---von-weiting-zhou)
    - [Wann sollte man commiten? - von Weiting Zhou](#wann-sollte-man-commiten---von-weiting-zhou)
    - [Wann und wofür sollten neue Branches erstellt werden? - von Weiting Zhou](#wann-und-wofür-sollten-neue-branches-erstellt-werden---von-weiting-zhou)
    - [Wann sollte gepusht und gemergt werden? - von Weiting Zhou](#wann-sollte-gepusht-und-gemergt-werden---von-weiting-zhou)
    - [Wie arbeitet man mit dem main/master branch? - von Weiting Zhou](#wie-arbeitet-man-mit-dem-mainmaster-branch---von-weiting-zhou)
  - [Git Befehle - von Bardia Azmoun](#git-befehle---von-bardia-azmoun)
    - [Lokales Repository](#lokales-repository)
      - [git init](#git-init)
      - [git add](#git-add)
      - [git commit](#git-commit)
      - [git status](#git-status)
    - [Remote Repository](#remote-repository)
      - [git fetch](#git-fetch)
      - [git push](#git-push)
      - [git pull](#git-pull)
      - [git clone](#git-clone)
      - [git remote](#git-remote)


## Was sind Git und GitHub und wofür werden die Systeme verwendet?

### Versionskontrollsysteme - von Paul von Napolski
> Versionskontrollsysteme sind hauptsächlich dazu da, Dateien zu *versionieren* - dass bedeutet, dass für jede Änderung, die vorgenommen wird, eine neue Version gespeichert wird, die diese Änderungen enthält. Das hat den Vorteil, dass fehlerhafte Änderungen jederzeit zurückgesetzt werden können. Ein weiterer Vorteil von Versionskontrollsystemem ist, dass die Zusammenarbeit mit Teammitgliedern deutlich vereinfacht.

> 28.02.2024

#### Git - von Paul von Napolski
> Das aktuell beliebteste Versionskontrollsystem ist **Git**. Git ist mittlerweile fast schon zum Standart-Versionskontrollsystem für Entwickler geworden; die meisten modernen Entwicklungsumgebungen wie VisualStudio oder IntelliJ unterstüzen die Versionierung mit Git. Entwickelt wurde Git [2005](https://de.wikipedia.org/wiki/Git) von Linus Torvalds, als Ersatz für die kostenpflichtige BitKeeper Software. Git gehört zu den *dezentralen Versionskontrollsystemen*.

> 04.03.2024

### GitHub - Von Felix Andreas Assert
> GitHub ist ein Online-service Anbieter, der Server für Versionskontrollsystem anbietet. GitHub wird benutz als ein Tool um das Bearbeiten von Programmen in Teams einfacher zu gestalten und Programmieren ein sogenantes "Repository" als allgemeinen Speicherort für ihre Projekte zu geben. 

> Änderungen vom 4. März, 2024

## Wie funktioniert Git? - von Patrick Scheuer
> Wenn man mit Git arbeitet, kommt man an denn folgenden drei Begriffen nicht vorbei: Das Working Directory, die Staging Area und das Repository.
Das Working Directory dient als eine Art Aufnahme der Dateien und Ordner, welchen man Git erlaubt zu tracken und dessen Versionen zu kontrollieren. Dort sind also die
Daten untergebracht, mit welchen gearbeitet werden sollen.
Die Staging Area kann als ein temporärer Platz für ausgewählte Dateien gesehen werden, dessen Änderungen man im nächsten Schritt comitten möchte. Es ist also ein
Zwischenschritt vor dem Commit.
Das Repository kann daher als das Endergebnis betrachtet werden, wo alle Commits und Historien der Projekte hinterlegt werden. Das Repository wird mit einer
versteckten .git-Datei gekennzeichnet.

> 04.03.2024

## Wie funktioniert Git? (Alternative Beschreibung) - von Paul von Napolski
> Um Git zu benutzen, muss zuerst ein sogenanntes *Repository* mit dem Befehl ```git init [Name]```angelegt werden. Dieser Befehl *merkiert* einen Ordner sozusagen als Git-Repository, durch das erstellen eines Ordners *.git/*. Dieser Ordner enthält alle für Git relevanten Dateien, wie z.B. *refs/* (siehe [Remote Branches](#remote-branches---von-paul-von-napolski)). In jedem Git Repository gibt es drei Bereiche - den *Working Tree*, die *Staging Area* und das *Repository*.
> 
> Der **Working Tree** ist der Bereich, in dem gearbeitet wird. Er enthält alle Dateien in ihrem aktuellen Zustand. Änderungen im Working Tree können *gestaged* werden, um sie dann zu *commiten*. Dadurch werden sie dem Repository hinzugefügt.
> 
> Die **Staging Area** enthält alle *gestageten* Änderungen, dass Änderungen, die markiert wurden, um sie später zu commiten.
> 
> Das **Repository** enthält alle bereits committeten Änderungen. Diese werden jeweils als eigenständige [*Commits*](#commits) gespeichert, die jeweils nur ihre entsprechenden Änderungen enthalten.

> 06.03.2024

### Commits - von Paul von Napolski
> Commits sind sozusagen gespeicherte *Zustände* oder *Versionen* des Repositorys. Sie enthalten alle gespeicherten Änderungen, basierend auf ihrem jeweiligen *Vorgänger-Commit*. Das heißt, wenn z.B. die Datei README<span>.md</span> geändert wird, und diese Änderung dann gespeichert - *committet* - wird, dann enthält dieser Commit alle Änderungen an der Datei README<span>.md</span> seit dem letzten Commit. Zusätzlich verweist jeder Commit auf seine jeweiligen Vorgänger-Commits. Meistens hat ein Commit genau einen Vorgänger, [*Merge-Commits*](#merging) beispielsweise können jedoch auch mehrere Vorgänger haben. Des weiteren dient jeder Commit auch als [Wiederherstellungspunkt](#commits-als-wiederherstellungspunkte). Das heißt, dass Branches und HEAD jederzeit auf den Stand eines bestimmten Commits zurückgesetzt werden können.


### Commits (Alternative Beschreibung) - von Patrick Scheuer
> Commits können als Snapshots oder Checkpoints deines Projektes angesehen werden. Es ist grob gesagt eine Version in deinem Repository, also eine Kopie über die zum Zeitpunkt aufgenommene Dateien im Projekt. Man kann es auch als Fortschritte sehen, welche in einem Projekt erzielt und aufgezeichnet wurden. Auf diese kann man auch immer zugreifen, indem man mit "git checkout" zu dem jeweilien Commit auscheckt.

> 11.03.2024


### Branches und HEAD - von Patrick Scheuer

> Branches und Head lässt sich erstmal einfacher erklären, wenn wir uns Git wie eine Zeitmachine vorstellen. Master ist gewöhnlich die "Haupt-Timeline" und somit der Standard-Branch. Wenn wir nun allerdings etwas verändern möchten, was für diese Timeline (zumindest erstmal) nicht vorgesehen ist, erstellen wir einen neuen Branch. Es ist in diesem Fall ein neuer Entwicklungszweig, beispielweise für ein Feature, Experimente oder sonstige Änderungen, die unseren Standard-Branch nicht betreffen dürfen. Diese verschiedenen Zweige kann man auch zusammenführen, aber dazu mehr bei "Merge und Rebase". Doch was ist nun der HEAD? Der HEAD dient ganz einfach als Zeiger, welcher uns sagt, auf welchem Branch wir uns befinden. Es ist also der Ort, zu welchem wir "auschecken" und auf welchem wir uns aktuell befinden. Ein Beispiel: Du befindest dich im Branch master - der HEAD ist auf master. Wenn du nun auf den Branch "Test" auscheckst, ist ebenfalls der HEAD auf "Test". Man kann auch auf vorherige Commits auschecken, wodurch der HEAD sich ebenfalls auf diesem Commit befindet. Allerdings ist der HEAD in diesem Fall auf keinem Branch, sondern nur dem einzelnen Commit. Man nennt dies auch "detached HEAD".

> 11.03.2024

### Merge und Rebase - von Patrick Scheuer

> Wie bereits bei "Branches und HEAD" erwähnt, kann man zwei Branches auch zusammenführen. Dies ist nützlich, wenn man beispielweise ein Feature, welches sich auf einem anderen Branch befindet, zu dem Master-Branch hinzufügen möchte. Hierbei gibt es mehrere Methoden/Befehle, um dies zu erreichen, aber Merge und Rebase sind die Gängisten. Zunächst schauen wir uns Merging an: Mit dem Befehl "git merge <branch>" wird ein sogenannter "Merge-Commit" in dem Branch erstellt, von welchem du mergen möchtest. Dieser vereint den Verlauf beider Branches und somit wird die Historie nicht umgeschrieben oder verändert. Dies kann allerdings, besonders bei Teamarbeit, schnell unübersichtlich werden, da für jedes Mergen ein neuer Commit erstellt wird. Rebase erledigt dies anders. Mit dem Befehl "git rebase <branch>" werden ebenso beide Branches zusammengefasst, allerdings wird hierbei die Historie des Branches, von welchem ge-rebased wird, an die Spitze des anderen Branches verschoben. Beispielweise befinden sich somit alle Commits bzw. Kopien der Commits des Test-Branches vorne im Master-Branch. Dies sorgt dafür, dass die Historie umgeschrieben wird und es einen linearen Verlauf gibt. Dies hat allerdings ohne einen extra Commit wie beim Merging den Nachteil, dass Änderungen nicht mehr nachvollziehbar werden können. Daher sollte man sich gut überlegen, welchen der Methoden man benutzt.

> 11.03.2024

### Commits als Wiederherstellungspunkte - von Patrick Scheuer
> Commits dienen nicht nur als Snapshots deines bisherigen Fortschrittes im Projekt, sondern können auch genutzt werden, um dein Projekt auf einen früheren Zeitraum wiederherzustellen. Stellen wir uns mal vor, du hast die letzten 3 Commits "verkackt" und möchtest auf den Zustand eines anderes Commits zurückkehren. Zunächst lässt du dir den kompletten Verlauf aller Commits mit dem Befehl "git log" anzeigen. Hier suchst du nach dem Commit, zu welchenm du zurückkehren möchtest du kopierst den Hashwert. Darauf kannst du das Projekt zu diesem Commit reseten, indem du "git reset <hashwert>" in die Konsole eingibst. Dabei gibt es noch eine Sache zu beachten. der "git reset" Command hat drei verschiedene Parameter: soft, mixed und hard. Der Defaultwert ist mixed, was bedeutet, dass die letzten Commits nicht entgültig gelöscht werden, sondern die Änderungen weiterhin in den Dateien und der Staging Area bestehend bleiben. Mit "git reset --soft" bleibt ebenfalls alles unverändert und man müsste nur neu commiten, was praktisch ist, wenn man nur die Nachricht des Commites ändern möchte. In unserem Bespiel möchten wir mit "git reset --hard" gehen, was alle Änderungen entgültig löscht. Es ist, wie es im Namen steckt, ein Hardreset. Mit dieser Methode befindet sich das Projekt auf den Zustand, zu welchem man zurücksetzen möchte.

> 11.03.2024

## Was sind Remote-Repositoris und wie funktionieren sie? - von Paul von Napolski
> Remote Repositories sind andere Versionen des eigenen Repositories, die sich an einem anderen Ort befinden. Das kannn einfach ein anderer Ordner auf demselben Gerät sein, meistens wird man Remote Repositories jedoch auf anderen Geräten, häufig auch einem dedizierten Server, antreffen.

> 04.03.2024

### Remote Branches - von Paul von Napolski
> Ein Remote Branch ist im Grunde erstmal nichts weiteres, als ein Branch in einem Remote Repository. Wenn das lokale Repository mit einem Remote Repository verbunden ist, speichert Git *Referenzen*, in diesem Fall Links, in dem Ordner *'refs/'*. Um den Remote Branch jetzt meit einem lokalen Branch zu verbinden, wird der Befehl: 
>> ```git --set-upstream [RemoteRepoName] [RemoteBranchName]``` 
> Wenn ein Remote Branch auf diese Weise mit einem lokalen Branch verbunden ist, wird als *Upstream Branch* bezeichnet.

> 04.03.2024

### Origin - von Patrick Scheuer
> Die Origin beschreibt den Namen für ein remote Repository, welches ein dazugehöriges lokales Repository hat, aus welchem geklont wurde. Ebenso haben die Branches eigene Origins im remote Repository, welche auf das Lokale zurückgreifen. Beispielweise ist o/master der remote Branch vom lokalen Branch "master". Das "o" steht dbei für "origin".

> 11.03.2024

### GitHub als Remote Repository - Von Felix Andreas Assert

> Die GitHub-Server sind innerhalb des Internets addressierbar, was Menschen - zum größtenteil Entwicklern - die Möglichkeit bietet Lokale Repositories hochzuladen und als Remote Repository zu benutzen.

> Änderungen vom 4. März, 2024

## Best-Practices - von Weiting Zhou
> Grundregeln wie man mit einer Repository arbeiten soll um einen möglichs Übersichtlichen und stabile main/master branch zu haben.

> 28.02.24

### Wann sollte man commiten? - von Weiting Zhou
> Man sollte am besten nach jeder Teilaufgabe, die man Aufgestellt hat, einmal nach der Fertigstellung Committen um die Änderung zu speichern und ggf. Rückgängig zu machen.

> 28.02.24

### Wann und wofür sollten neue Branches erstellt werden? - von Weiting Zhou
> Man sollte einen neuen Branch erstellen, wenn z.B. eine weitere Person am Projekt arbeitet oder man den Projekt in verschiedenen Teilaufgaben aufteilt.

> 28.02.24

### Wann sollte gepusht und gemergt werden? - von Weiting Zhou
> Man sollte Grundsätzlich nach jeden Commit einmal pushen um die Änderung extern zu haben und man sollte nach jeder Fertiggestellter Teilaufgabe, einmal seine Änderungen mit den main/master mergen.

> 28.02.2024

### Wie arbeitet man mit dem main/master branch? - von Weiting Zhou
> Im main/master branch sollte man grundsätzlich nur Fertige Teilaufgaben hinzufügen, damit der main/master sauber und stabil läuft

> 28.02.2024

## Git Befehle - von Bardia Azmoun

### Lokales Repository

#### git init
> Initialisiert ein neues Git-Repository.

> 04.03.2024

#### git add
> Verschiebt Änderungen aus dem Arbeitsverzeichnis in die Staging-Area, bevor man sie in den offiziellen Verlauf committet.

> 28.02.2024

#### git commit
> 

#### git status
> Gibt den Status des Arbeitsverzeichnisses und der Staging-Area zurück.

> 04.03.2024

### Remote Repository

#### git fetch
> Ein Branch von einem anderen Repository wird zusammen mit allen zugehörigen Commits und Dateien heruntergeladen. Dabei wird jedoch nichts in dein lokales Repository integriert. Auf diese Weise hast du die Möglichkeit, Änderungen vor dem Merge in dein Projekt noch zu überprüfen.

> 04.03.2024

#### git push
> Mit diesem Befehl kann man einen lokalen Branch in ein anderes Repository verschieben.

> 04.03.2024

#### git pull
> Pulls sind die automatisierte Version von git fetch. Dabei wird ein Branch von einem Remote-Repository heruntergeladen und dann direkt in den aktuellen Branch gemergt.

> 04.03.2024

#### git clone
> Erstellt eine Kopie eines bestehenden Git-Repositorys.

> 04.03.2024

#### git remote
> 

