# Richtiges Arbeiten mit Git und GitHub

## Inhalt
- [Richtiges Arbeiten mit Git und GitHub](#richtiges-arbeiten-mit-git-und-github)
  - [Inhalt](#inhalt)
  - [Was sind Git und GitHub und wofür werden die Systeme verwendet?](#was-sind-git-und-github-und-wofür-werden-die-systeme-verwendet)
    - [Versionskontrollsysteme](#versionskontrollsysteme)
      - [Git](#git)
    - [GitHub](#github)
  - [Wie funktioniert Git?](#wie-funktioniert-git)
  - [Wie funktioniert Git? (Alternative Beschreibung)](#wie-funktioniert-git-alternative-beschreibung)
    - [Commits](#commits)
    - [Commits (Alternative Beschreibung)](#commits-alternative-beschreibung)
    - [Branches und HEAD](#branches-und-head)
    - [Merge und Rebase](#merge-und-rebase)
    - [Commits als Wiederherstellungspunkte](#commits-als-wiederherstellungspunkte)
  - [Was sind Remote-Repositoris und wie funktionieren sie?](#was-sind-remote-repositoris-und-wie-funktionieren-sie)
    - [Remote Branches](#remote-branches)
    - [Origin - von Patrick Scheuer](#origin---von-patrick-scheuer)
    - [GitHub als Remote Repository](#github-als-remote-repository)
  - [Best-Practices](#best-practices)
    - [Wann sollte man commiten?](#wann-sollte-man-commiten)
    - [Wann und wofür sollten neue Branches erstellt werden?](#wann-und-wofür-sollten-neue-branches-erstellt-werden)
    - [Wann sollte gepusht und gemergt werden?](#wann-sollte-gepusht-und-gemergt-werden)
    - [Wie arbeitet man mit dem main/master branch?](#wie-arbeitet-man-mit-dem-mainmaster-branch)
  - [Git Befehle](#git-befehle)
    - [Lokales Repository](#lokales-repository)
      - [git init](#git-init)
      - [git add](#git-add)
      - [git commit -m "..."](#git-commit--m-)
      - [git status](#git-status)
    - [Remote Repositories](#remote-repositories)
      - [git fetch](#git-fetch)
      - [git push](#git-push)
      - [git pull](#git-pull)
      - [git clone](#git-clone)
      - [git remote](#git-remote)
      - [git remote -v](#git-remote--v)
      - [git remote add (Name)](#git-remote-add-name)
      - [git remote rm (Name)](#git-remote-rm-name)
      - [git remote rename (Alter Name) (Neuer Name)](#git-remote-rename-alter-name-neuer-name)
      - [git revert](#git-revert)
      - [git cherry-pick](#git-cherry-pick)
      - [git branch](#git-branch)
      - [git checkout](#git-checkout)
      - [git log](#git-log)
      - [git merge](#git-merge)
      - [git rebase](#git-rebase)
      - [git reset --soft --mixed --hard](#git-reset---soft---mixed---hard)
      - [git status](#git-status-1)



## Was sind Git und GitHub und wofür werden die Systeme verwendet?

### Versionskontrollsysteme
> Versionskontrollsysteme sind hauptsächlich dazu da, Dateien zu *versionieren* - dass bedeutet, dass für jede Änderung, die vorgenommen wird, eine neue Version gespeichert wird, die diese Änderungen enthält. Das hat den Vorteil, dass fehlerhafte Änderungen jederzeit zurückgesetzt werden können. Ein weiterer Vorteil von Versionskontrollsystemem ist, dass die Zusammenarbeit mit Teammitgliedern deutlich vereinfacht.

> Letzte Änderungen vom 28. Feburar, 2024 - Paul von Napolski

#### Git
> Das aktuell beliebteste Versionskontrollsystem ist **Git**. Git ist mittlerweile fast schon zum Standart-Versionskontrollsystem für Entwickler geworden; die meisten modernen Entwicklungsumgebungen wie VisualStudio oder IntelliJ unterstüzen die Versionierung mit Git. Entwickelt wurde Git [2005](https://de.wikipedia.org/wiki/Git) von Linus Torvalds, als Ersatz für die kostenpflichtige BitKeeper Software. Git gehört zu den *dezentralen Versionskontrollsystemen*.

> Letzte Änderungen vom 04. März, 2024 - Paul von Napolski

### GitHub
> GitHub ist ein Online-service Anbieter, der Server für Versionskontrollsystem anbietet. GitHub wird benutz als ein Tool um das Bearbeiten von Programmen in Teams einfacher zu gestalten und Programmieren ein sogenantes "Repository" als allgemeinen Speicherort für ihre Projekte zu geben. 

> Letzte Änderungen vom 4. März, 2024 - Felix Andreas Assert

## Wie funktioniert Git?
> Wenn man mit Git arbeitet, kommt man an denn folgenden drei Begriffen nicht vorbei: Das Working Directory, die Staging Area und das Repository.
Das Working Directory dient als eine Art Aufnahme der Dateien und Ordner, welchen man Git erlaubt zu tracken und dessen Versionen zu kontrollieren. Dort sind also die
Daten untergebracht, mit welchen gearbeitet werden sollen.
Die Staging Area kann als ein temporärer Platz für ausgewählte Dateien gesehen werden, dessen Änderungen man im nächsten Schritt comitten möchte. Es ist also ein
Zwischenschritt vor dem Commit.
Das Repository kann daher als das Endergebnis betrachtet werden, wo alle Commits und Historien der Projekte hinterlegt werden. Das Repository wird mit einer
versteckten .git-Datei gekennzeichnet.

> Letzte Änderungen vom 4. März, 2024 - Patrick Scheuer

## Wie funktioniert Git? (Alternative Beschreibung) 
> Um Git zu benutzen, muss zuerst ein sogenanntes *Repository* mit dem Befehl ```git init [Name]```angelegt werden. Dieser Befehl *merkiert* einen Ordner sozusagen als Git-Repository, durch das erstellen eines Ordners *.git/*. Dieser Ordner enthält alle für Git relevanten Dateien, wie z.B. *refs/* (siehe [Remote Branches](#remote-branches---von-paul-von-napolski)). In jedem Git Repository gibt es drei Bereiche - den *Working Tree*, die *Staging Area* und das *Repository*.
> 
> Der **Working Tree** ist der Bereich, in dem gearbeitet wird. Er enthält alle Dateien in ihrem aktuellen Zustand. Änderungen im Working Tree können *gestaged* werden, um sie dann zu *commiten*. Dadurch werden sie dem Repository hinzugefügt.
> 
> Die **Staging Area** enthält alle *gestageten* Änderungen, dass Änderungen, die markiert wurden, um sie später zu commiten.
> 
> Das **Repository** enthält alle bereits committeten Änderungen. Diese werden jeweils als eigenständige [*Commits*](#commits) gespeichert, die jeweils nur ihre entsprechenden Änderungen enthalten.

> Letzte  Änderungen vom 6. März, 2024 - Paul von Napolski

### Commits
> Commits sind sozusagen gespeicherte *Zustände* oder *Versionen* des Repositorys. Sie enthalten alle gespeicherten Änderungen, basierend auf ihrem jeweiligen *Vorgänger-Commit*. Das heißt, wenn z.B. die Datei README<span>.md</span> geändert wird, und diese Änderung dann gespeichert - *committet* - wird, dann enthält dieser Commit alle Änderungen an der Datei README<span>.md</span> seit dem letzten Commit. Zusätzlich verweist jeder Commit auf seine jeweiligen Vorgänger-Commits. Meistens hat ein Commit genau einen Vorgänger, [*Merge-Commits*](#merging) beispielsweise können jedoch auch mehrere Vorgänger haben. Des weiteren dient jeder Commit auch als [Wiederherstellungspunkt](#commits-als-wiederherstellungspunkte). Das heißt, dass Branches und HEAD jederzeit auf den Stand eines bestimmten Commits zurückgesetzt werden können.

> Letzte Änderungen vom 11. März, 2024 - Paul von Napolski

### Commits (Alternative Beschreibung)
> Commits können als Snapshots oder Checkpoints deines Projektes angesehen werden. Es ist grob gesagt eine Version in deinem Repository, also eine Kopie über die zum Zeitpunkt aufgenommene Dateien im Projekt. Man kann es auch als Fortschritte sehen, welche in einem Projekt erzielt und aufgezeichnet wurden. Auf diese kann man auch immer zugreifen, indem man mit "git checkout" zu dem jeweilien Commit auscheckt.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer


### Branches und HEAD

> Branches und Head lässt sich erstmal einfacher erklären, wenn wir uns Git wie eine Zeitmachine vorstellen. Master ist gewöhnlich die "Haupt-Timeline" und somit der Standard-Branch. Wenn wir nun allerdings etwas verändern möchten, was für diese Timeline (zumindest erstmal) nicht vorgesehen ist, erstellen wir einen neuen Branch. Es ist in diesem Fall ein neuer Entwicklungszweig, beispielweise für ein Feature, Experimente oder sonstige Änderungen, die unseren Standard-Branch nicht betreffen dürfen. Diese verschiedenen Zweige kann man auch zusammenführen, aber dazu mehr bei "Merge und Rebase". Doch was ist nun der HEAD? Der HEAD dient ganz einfach als Zeiger, welcher uns sagt, auf welchem Branch wir uns befinden. Es ist also der Ort, zu welchem wir "auschecken" und auf welchem wir uns aktuell befinden. Ein Beispiel: Du befindest dich im Branch master - der HEAD ist auf master. Wenn du nun auf den Branch "Test" auscheckst, ist ebenfalls der HEAD auf "Test". Man kann auch auf vorherige Commits auschecken, wodurch der HEAD sich ebenfalls auf diesem Commit befindet. Allerdings ist der HEAD in diesem Fall auf keinem Branch, sondern nur dem einzelnen Commit. Man nennt dies auch "detached HEAD".

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

### Merge und Rebase

> Wie bereits bei "Branches und HEAD" erwähnt, kann man zwei Branches auch zusammenführen. Dies ist nützlich, wenn man beispielweise ein Feature, welches sich auf einem anderen Branch befindet, zu dem Master-Branch hinzufügen möchte. Hierbei gibt es mehrere Methoden/Befehle, um dies zu erreichen, aber Merge und Rebase sind die Gängisten. Zunächst schauen wir uns Merging an: Mit dem Befehl "git merge <branch>" wird ein sogenannter "Merge-Commit" in dem Branch erstellt, von welchem du mergen möchtest. Dieser vereint den Verlauf beider Branches und somit wird die Historie nicht umgeschrieben oder verändert. Dies kann allerdings, besonders bei Teamarbeit, schnell unübersichtlich werden, da für jedes Mergen ein neuer Commit erstellt wird. Rebase erledigt dies anders. Mit dem Befehl "git rebase <branch>" werden ebenso beide Branches zusammengefasst, allerdings wird hierbei die Historie des Branches, von welchem ge-rebased wird, an die Spitze des anderen Branches verschoben. Beispielweise befinden sich somit alle Commits bzw. Kopien der Commits des Test-Branches vorne im Master-Branch. Dies sorgt dafür, dass die Historie umgeschrieben wird und es einen linearen Verlauf gibt. Dies hat allerdings ohne einen extra Commit wie beim Merging den Nachteil, dass Änderungen nicht mehr nachvollziehbar werden können. Daher sollte man sich gut überlegen, welchen der Methoden man benutzt.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

### Commits als Wiederherstellungspunkte
> Commits dienen nicht nur als Snapshots deines bisherigen Fortschrittes im Projekt, sondern können auch genutzt werden, um dein Projekt auf einen früheren Zeitraum wiederherzustellen. Stellen wir uns mal vor, du hast die letzten 3 Commits "verkackt" und möchtest auf den Zustand eines anderes Commits zurückkehren. Zunächst lässt du dir den kompletten Verlauf aller Commits mit dem Befehl "git log" anzeigen. Hier suchst du nach dem Commit, zu welchenm du zurückkehren möchtest du kopierst den Hashwert. Darauf kannst du das Projekt zu diesem Commit reseten, indem du "git reset <hashwert>" in die Konsole eingibst. Dabei gibt es noch eine Sache zu beachten. der "git reset" Command hat drei verschiedene Parameter: soft, mixed und hard. Der Defaultwert ist mixed, was bedeutet, dass die letzten Commits nicht entgültig gelöscht werden, sondern die Änderungen weiterhin in den Dateien und der Staging Area bestehend bleiben. Mit "git reset --soft" bleibt ebenfalls alles unverändert und man müsste nur neu commiten, was praktisch ist, wenn man nur die Nachricht des Commites ändern möchte. In unserem Bespiel möchten wir mit "git reset --hard" gehen, was alle Änderungen entgültig löscht. Es ist, wie es im Namen steckt, ein Hardreset. Mit dieser Methode befindet sich das Projekt auf den Zustand, zu welchem man zurücksetzen möchte.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

## Was sind Remote-Repositoris und wie funktionieren sie?
> Remote Repositories sind andere Versionen des eigenen Repositories, die sich an einem anderen Ort befinden. Das kannn einfach ein anderer Ordner auf demselben Gerät sein, meistens wird man Remote Repositories jedoch auf anderen Geräten, häufig auch einem dedizierten Server, antreffen.

> Letzte Änderungen vom 4. März, 2024 - Paul von Napolski

### Remote Branches
> Ein Remote Branch ist im Grunde erstmal nichts weiteres, als ein Branch in einem Remote Repository. Wenn das lokale Repository mit einem Remote Repository verbunden ist, speichert Git *Referenzen*, in diesem Fall Links, in dem Ordner *'refs/'*. Um den Remote Branch jetzt meit einem lokalen Branch zu verbinden, wird der Befehl: 
 ```git --set-upstream [RemoteRepoName] [RemoteBranchName]``` 
 Wenn ein Remote Branch auf diese Weise mit einem lokalen Branch verbunden ist, wird als *Upstream Branch* bezeichnet.

> Letzte Änderungen vom 4. März, 2024 - Paul von Napolski

### Origin - von Patrick Scheuer
> Die Origin beschreibt den Namen für ein remote Repository, welches ein dazugehöriges lokales Repository hat, aus welchem geklont wurde. Ebenso haben die Branches eigene Origins im remote Repository, welche auf das Lokale zurückgreifen. Beispielweise ist o/master der remote Branch vom lokalen Branch "master". Das "o" steht dbei für "origin".

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

### GitHub als Remote Repository 

> Die GitHub-Server sind innerhalb des Internets addressierbar, was Menschen - zum größtenteil Entwicklern - die Möglichkeit bietet Lokale Repositories hochzuladen und als Remote Repository zu benutzen.

> Letzte Änderungen vom 4. März, 2024 - Felix Andreas Assert

## Best-Practices
> Grundregeln wie man mit einer Repository arbeiten soll um einen möglichs Übersichtlichen und stabile main/master branch zu haben.

> Letzte Änderungen vom 28. Feburar, 2024 - Weiting Zhou

### Wann sollte man commiten?
> Man sollte am besten nach jeder Teilaufgabe, die man Aufgestellt hat, einmal nach der Fertigstellung Committen um die Änderung zu speichern und ggf. Rückgängig zu machen.

> Letzte Änderungen vom 28. Feburar, 2024 - Weiting Zhou

### Wann und wofür sollten neue Branches erstellt werden?
> Man sollte einen neuen Branch erstellen, wenn z.B. eine weitere Person am Projekt arbeitet oder man den Projekt in verschiedenen Teilaufgaben aufteilt.

> Letzte Änderungen vom 28. Feburar, 2024 - Weiting Zhou

### Wann sollte gepusht und gemergt werden?
> Man sollte Grundsätzlich nach jeden Commit einmal pushen um die Änderung extern zu haben und man sollte nach jeder Fertiggestellter Teilaufgabe, einmal seine Änderungen mit den main/master mergen.

> Letzte Änderungen vom 28. Feburar, 2024 - Weiting Zhou

### Wie arbeitet man mit dem main/master branch?
> Im main/master branch sollte man grundsätzlich nur Fertige Teilaufgaben hinzufügen, damit der main/master sauber und stabil läuft

> Letzte Änderungen vom 28. Feburar, 2024 - Weiting Zhou

## Git Befehle

### Lokales Repository 

#### git init
> Initialisiert ein neues Git-Repository.

> Letzte Änderungen vom 28. Feburar, 2024 - Bardia Azmoun

#### git add
> Verschiebt Änderungen aus dem Arbeitsverzeichnis in die Staging-Area, bevor man sie in den offiziellen Verlauf committet.

> Letzte Änderungen vom 28. Feburar, 2024 - Bardia Azmoun

#### git commit -m "..." 
>  Speichert den aktuellen Zustand des Staging-Bereichs im Repository mit einer beschreibenden Nachricht.

> Letzte Änderungen vom 11. März, 2024 - Bardia Azmoun

#### git status 
> Gibt den Status des Arbeitsverzeichnisses und der Staging-Area zurück.

> Letzte Änderungen vom 4. März, 2024 - Bardia Azmoun

### Remote Repositories 

#### git fetch 
> Ein Branch von einem anderen Repository wird zusammen mit allen zugehörigen Commits und Dateien heruntergeladen. Dabei wird jedoch nichts in dein lokales Repository integriert. Auf diese Weise hast du die Möglichkeit, Änderungen vor dem Merge in dein Projekt noch zu überprüfen.

> Letzte Änderungen vom 4. März, 2024 - Bardia Azmoun

#### git push
> Mit diesem Befehl kann man einen lokalen Branch in ein anderes Repository verschieben.

> Letzte Änderungen vom 4. März, 2024 - Bardia Azmoun

#### git pull
> Pulls sind die automatisierte Version von git fetch. Dabei wird ein Branch von einem Remote-Repository heruntergeladen und dann direkt in den aktuellen Branch gemergt.

> Letzte Änderungen vom 4. März, 2024 - Bardia Azmoun

#### git clone
> Erstellt eine Kopie eines bestehenden Git-Repositorys.

> Letzte Änderungen vom 4. März, 2024 - Bardia Azmoun

#### git remote
> Ermöglicht mit entfernten Repositorys zu interagieren.

> Letzte Änderungen vom 11. März, 2024 - Bardia Azmoun

#### git remote -v
> Zeigt die Liste der entfernten Repositorys an, die mit deinem lokalen Repository verknüpft sind, sowie deren URLs.

> Letzte Änderungen vom 11. März, 2024 - Bardia Azmoun

#### git remote add (Name)
> Fügt ein neues entferntes Repository hinzu, das du verfolgen möchtest.

> Letzte Änderungen vom 11. März, 2024 - Bardia Azmoun

#### git remote rm (Name)
> Entfernt das entfernte Repository mit dem angegebenen Namen aus der Liste der verfolgten entfernten Repositorys.

> Letzte Änderungen vom 11. März, 2024 - Bardia Azmoun

#### git remote rename (Alter Name) (Neuer Name)
> Benennt ein entferntes Repository um.

> Letzte Änderungen vom 11. März, 2024 - Bardia Azmoun

#### git revert
> Macht einen Commit rückgängig, indem ein neuer Commit erstellt wird, der die Änderungen des vorherigen Commits aufhebt.

> Letzte Änderungen vom 11. März, 2024 - Bardia Azmoun

#### git cherry-pick
> Übernimmt die Änderungen eines bestimmten Commits und fügt sie dem aktuellen Branch hinzu.

> Letzte Änderungen vom 11. März, 2024 - Bardia Azmoun

#### git branch
> Erstellt einen neuen Branch oder lässt alle Branches des Repositories anzeigen.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

#### git checkout
> Navigation zwischen den verschiedenen Branches. Man kann zu einem anderen Branch wechseln/auschecken oder auch zu bestimmten Commits.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

#### git log
> Dient als Übersicht zu allen bisherigen Commits in chronologischer Reihenfolge und den dazugehörigen Hashwerten.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

#### git merge
> Zusammenfügen zweier oder mehrerer Branches. Die Historie bleibt unverändert und es wird ein Merge-Commit erstellt.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

#### git rebase
> Zusammenfügen zweier Branches. Die Historie wird verändert, indem die Commits des einen Branches an die Spitze des anderen Branches gesetzt werden. Es wird kein extra Commit erstellt.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

#### git reset --soft --mixed --hard
> Setzt den Verlauf des Projekts auf einen bestimmten Zeitpunkt zurück. Dabei wird der entsprechende Commit mit dessen Hashwert angegeben, auf welchen zurückgesetzt werden soll.
> --soft: Alle Änderungen bleiben erhalten; nützlich, wenn man nur die Commit-Nachricht ändern möchte.
>--mixed: Standard-Parameter; Änderungen werden aus der Staging Area entnommen, das Index wurde zurückgesetzt.
>--hard: Alle Änderungen werden unwiderruflich gelöscht.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer

#### git status
> Gibt den Status des Working Directories an. Es werden Änderungen in der Staging Area angezeigt und Dateien, welche noch nicht getrackt wurden.

> Letzte Änderungen vom 11. März, 2024 - Patrick Scheuer




