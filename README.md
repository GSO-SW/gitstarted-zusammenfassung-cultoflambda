# Richtiges Arbeiten mit Git und GitHub

## Inhalt

## Was sind Git und GitHub und wofür werden die Systeme verwendet?

### Versionskontrollsysteme - von Paul von Napolski
> Versionskontrollsysteme sind hauptsächlich dazu da, Dateien zu *versionieren* - dass bedeutet, dass für jede Änderung, die vorgenommen wird, eine neue Version gespeichert wird, die diese Änderungen enthält. Das hat den Vorteil, dass fehlerhafte Änderungen jederzeit zurückgesetzt werden können. Ein weiterer Vorteil von Versionskontrollsystemem ist, dass die Zusammenarbeit mit Teammitgliedern deutlich vereinfacht.

> 28.02.2024

<<<<<<< Updated upstream
#### Git - von Paul von Napolski
> Das aktuell beliebteste Versionskontrollsystem ist **Git**. Git ist mittlerweile fast schon zum Standart-Versionskontrollsystem für Entwickler geworden; die meisten modernen Entwicklungsumgebungen wie VisualStudio oder IntelliJ unterstüzen die Versionierung mit Git. Entwickelt wurde Git [2005](https://de.wikipedia.org/wiki/Git) von Linus Torvalds, als Ersatz für die kostenpflichtige BitKeeper Software.

> 28.02.2024

### GitHub - Von Felix Andreas Assert
> GitHub ist ein Online-service Anbieter, der Server für Versionskontrollsystem anbietet. GitHub wird benutz als ein Tool um das Bearbeiten von Programmen in Teams einfacher zu gestalten und Programmieren ein sogenantes "Repository" als allgemeinen Speicherort für ihre Projekte zu geben. 

> Änderungen vom 4. März, 2024
=======
### GitHub - von Patrick Scheuer

## Wie funktioniert Git? - von Patrick Scheuer
> Wenn man mit Git arbeitet, kommt man an denn folgenden drei Begriffen nicht vorbei: Das Working Directory, die Staging Area und das Repository.
Das Working Directory dient als eine Art Aufnahme der Dateien und Ordner, welchen man Git erlaubt zu tracken und dessen Versionen zu kontrollieren. Dort sind also die
Daten untergebracht, mit welchen gearbeitet werden sollen.
Die Staging Area kann als ein temporärer Platz für ausgewählte Dateien gesehen werden, dessen Änderungen man im nächsten Schritt comitten möchte. Es ist also ein
Zwischenschritt vor dem Commit.
Das Repository kann daher als das Endergebnis betrachtet werden, wo alle Commits und Historien der Projekte hinterlegt werden. Das Repository wird mit einer
versteckten .git-Datei gekennzeichnet.

>04.03.2024
>>>>>>> Stashed changes


### Commits

### Branches und HEAD

## Was sind Remote-Repositoris und wie funktionieren sie? - von Paul von Napolski
> Remote Repositories sind andere Versionen des eigenen Repositories, die sich an einem anderen Ort befinden. Das kannn einfach ein anderer Ordner auf demselben Gerät sein, meistens wird man Remote Repositories jedoch auf anderen Geräten, häufig auch einem dedizierten Server, antreffen.

> 04.03.2024

### Remote Branches - von Paul von Napolski
> Ein Remote Branch ist im Grunde erstmal nichts weiteres, als ein Branch in einem Remote Repository. Wenn das lokale Repository mit einem Remote Repository verbunden ist, speichert Git *Referenzen*, in diesem Fall Links, in dem Ordner *'refs/'*. Um den Remote Branch jetzt meit einem lokalen Branch zu verbinden, wird der Befehl ```git --set-upstream [RemoteRepoName] [RemoteBranchName]```. Wenn ein Remote Branch auf diese Weise mit einem lokalen Branch verbunden ist, wird als *Upstream Branch* bezeichnet.

> 04.03.2024

### Origin

### GitHub als Remote Repository - Von Felix Andreas Assert

> GitHub ist ein Online-Service, welcher für Personen oder Gruppierungen Remote Repositorys über ihre eigenen Server zu verfügung stellt. Die GitHub Server sind innerhalb des Netzwerkes addressierbar, was Menschen - zum größtenteil Entwicklern - die Möglichkeit bietet ihre Lokalen Repositories ins Internet zu bringen und als Remote Repository zu benutzen.

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

### Remote Repositories

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

