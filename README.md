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


### Branches und HEAD

### Merge und Rebase

### Commits als Wiederherstellungspunkte

## Was sind Remote-Repositoris und wie funktionieren sie? - von Paul von Napolski
> Remote Repositories sind andere Versionen des eigenen Repositories, die sich an einem anderen Ort befinden. Das kannn einfach ein anderer Ordner auf demselben Gerät sein, meistens wird man Remote Repositories jedoch auf anderen Geräten, häufig auch einem dedizierten Server, antreffen.

> 04.03.2024

### Remote Branches - von Paul von Napolski
> Ein Remote Branch ist im Grunde erstmal nichts weiteres, als ein Branch in einem Remote Repository. Wenn das lokale Repository mit einem Remote Repository verbunden ist, speichert Git *Referenzen*, in diesem Fall Links, in dem Ordner *'refs/'*. Um den Remote Branch jetzt meit einem lokalen Branch zu verbinden, wird der Befehl: 
>> ```git --set-upstream [RemoteRepoName] [RemoteBranchName]``` 
> Wenn ein Remote Branch auf diese Weise mit einem lokalen Branch verbunden ist, wird als *Upstream Branch* bezeichnet.

> 04.03.2024

### Origin

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

