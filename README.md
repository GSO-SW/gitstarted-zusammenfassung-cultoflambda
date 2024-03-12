# Richtiges Arbeiten mit Git und GitHub

## Inhalt

## Was sind Git und GitHub und wofür werden die Systeme verwendet?

### Versionskontrollsysteme - von Paul von Napolski
> Versionskontrollsysteme sind hauptsächlich dazu da, Dateien zu *versionieren* - dass bedeutet, dass für jede Änderung, die vorgenommen wird, eine neue Version gespeichert wird, die diese Änderungen enthält. Das hat den Vorteil, dass fehlerhafte Änderungen jederzeit zurückgesetzt werden können. Ein weiterer Vorteil von Versionskontrollsystemem ist, dass die Zusammenarbeit mit Teammitgliedern deutlich vereinfacht.

> 28.02.2024

#### Git - von Paul von Napolski
> Das aktuell beliebteste Versionskontrollsystem ist **Git**. Git ist mittlerweile fast schon zum Standart-Versionskontrollsystem für Entwickler geworden; die meisten modernen Entwicklungsumgebungen wie VisualStudio oder IntelliJ unterstüzen die Versionierung mit Git. Entwickelt wurde Git [2005](https://de.wikipedia.org/wiki/Git) von Linus Torvalds, als Ersatz für die kostenpflichtige BitKeeper Software.

> 28.02.2024

### GitHub - Von Felix Andreas Assert
> GitHub ist ein Online-service Anbieter, der Server für Versionskontrollsystem anbietet. GitHub wird benutz als ein Tool um das Bearbeiten von Programmen in Teams einfacher zu gestalten und Programmieren ein sogenantes "Repository" als allgemeinen Speicherort für ihre Projekte zu geben. 

> Änderungen vom 4. März, 2024

## Wie funktioniert Git?

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

### Lokales Repository - von Bardia Azmoun

#### git init - von Bardia Azmoun
> Initialisiert ein neues Git-Repository.

> 04.03.2024

#### git add - von Bardia Azmoun
> Verschiebt Änderungen aus dem Arbeitsverzeichnis in die Staging-Area, bevor man sie in den offiziellen Verlauf committet.

> 28.02.2024

#### git commit -m "..." von Bardia Azmoun
>  Speichert den aktuellen Zustand des Staging-Bereichs im Repository mit einer beschreibenden Nachricht.

> 11.03.2024

#### git status - von Bardia Azmoun
> Gibt den Status des Arbeitsverzeichnisses und der Staging-Area zurück.

> 04.03.2024

### Remote Repositories - von Bardia Azmoun

#### git fetch - von Bardia Azmoun
> Ein Branch von einem anderen Repository wird zusammen mit allen zugehörigen Commits und Dateien heruntergeladen. Dabei wird jedoch nichts in dein lokales Repository integriert. Auf diese Weise hast du die Möglichkeit, Änderungen vor dem Merge in dein Projekt noch zu überprüfen.

> 04.03.2024

#### git push - von Bardia Azmoun
> Mit diesem Befehl kann man einen lokalen Branch in ein anderes Repository verschieben.

> 04.03.2024

#### git pull - von Bardia Azmoun
> Pulls sind die automatisierte Version von git fetch. Dabei wird ein Branch von einem Remote-Repository heruntergeladen und dann direkt in den aktuellen Branch gemergt.

> 04.03.2024

#### git clone - von Bardia Azmoun
> Erstellt eine Kopie eines bestehenden Git-Repositorys.

> 04.03.2024

#### git remote - von Bardia Azmoun
> Ermöglicht mit entfernten Repositorys zu interagieren.

> 11.03.2024

#### git remote -v - von Bardia Azmoun
> Zeigt die Liste der entfernten Repositorys an, die mit deinem lokalen Repository verknüpft sind, sowie deren URLs.

> 11.03.2024

#### git remote add (Name) - von Bardia Azmoun
> Fügt ein neues entferntes Repository hinzu, das du verfolgen möchtest.

> 11.03.2024

#### git remote rm (Name) - von Bardia Azmoun
> Entfernt das entfernte Repository mit dem angegebenen Namen aus der Liste der verfolgten entfernten Repositorys.

> 11.03.2024

#### git remote rename (Alter Name) (Neuer Name) - von Bardia Azmoun
> Benennt ein entferntes Repository um.

> 11.03.2024

#### git revert - von Bardia Azmoun
> Macht einen Commit rückgängig, indem ein neuer Commit erstellt wird, der die Änderungen des vorherigen Commits aufhebt.

> 11.03.2024

#### git cherry-pick - von Bardia Azmoun
> Übernimmt die Änderungen eines bestimmten Commits und fügt sie dem aktuellen Branch hinzu.

> 11.03.2024