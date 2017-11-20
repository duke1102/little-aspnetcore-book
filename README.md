# Hinweis!

Dies ist die deutsche Übersetzung des Buches. Momentan befindet sich diese am Anfang und viele Dinge werden im Laufe der Zeit verändert oder umstrukturiert. Manche Textpassagen mögen derzeit noch etwas merkwürdig oder überkompliziert klingen, dies wird später noch optimiert!

# Einführung

Danke dass Du das kleine ASP.NET Core Buch heruntergeladen hast! Ich habe dieses Buch mit dem Ziel verfasst um Entwicklern und Interessenten der Webentwicklung einen Einblick in ASP.NET Core 2.0, ein neues Framework für Webanwendungen und APIs, zu geben.

Das kleine ASP.NET Core Buch ist wie ein Tutorial aufgebaut. Du wirst eine To-Do App von Anfang bis Ende entwickeln und folgende Themen lernen:

* Die Grundlagen des MVC \(Model-View-Controller\) Musters
* Wie Frontend Code \(HTML, CSS, JavaScript\) mit Backend Code zusammenarbeitet
* Was "Dependency Injection" ist und warum es nützlich ist
* Wie man eine Datenbank ansteuert
* Wie man eine sichere Login- und Registrierungsfunktion implementiert 
* Wie man die App ins Web veröffentlicht

Keine Bange, um loszulegen brauchst Du überhaupt nichts über ASP.NET Core \(oder den oben genannten Themen\) zu wissen.

## Bevor Du anfängst

Der fertige Quelltext der Tutorialanwendung ist auf GitHub verfügbar \([https://www.github.com/nbarbettini/little-aspnetcore-todo](https://www.github.com/nbarbettini/little-aspnetcore-todo)\). Lade ihn herunter, falls Du Deinen eigenen Code damit vergleichen möchtest.

Das Buch selber wird regelmäßig aktualisiert mit Bugfixes und neuen Inhalten. Falls du die e-Book oder gedruckte Version liest, schaue auf der offiziellen Webseite \([littleasp.net/book](http://www.littleasp.net/book)\) nach, ob eine neuere Version verfügbar ist! Schaue auf der ganz letzten Seite des Buches für Versioninformationen und Änderungen nach.

## Für wen dieses Buch gedacht ist

Falls Du noch ein Anfänger im programmieren bist wird dieses Buch Dir Entwurfsmuster und Konzepte nahe bringen um moderne Webanwendungen zu entwickeln. Du wirst lernen wie man eine Webanwendung erstellt \(und wie große Teile zusammenarbeiten\), indem Du etwas von Anfang an baust!

Während dieses kleine Buch nicht in der Lage ist sämtliche Themen zu erläutern, die in der Programmierung wichtig sind, gibt es durchaus einen Anfangspunkt um weitere fortgeschrittene Themen zu verstehen.

Falls Du bereits in einer Backend Sprache wie Node, Python, Ruby, Go oder Java programmierst, werden Dir einige Konzepte, wie MVC, View Templates und Dependency Injection, bekannt vor kommen. Der Code wird in C\# verfasst, aber er wird nicht großartig abweichen von Dir bekannten Syntaxen.

Falls Du ein ASP.NET MVC Entwickler bist, wirst Du dich wie Zuhause fühlen! ASP.NET Core bringt einige neue Tool und verwendet \(und vereinfacht\) bereits bekannte Dinge. Ich erkläre einige Veränderungen weiter unten.

Egal wie Dein Wissenstand in der Webentwicklung ist, dieses Buch wird Dir alles beibringen um eine einfache und nützliche Webanwendung mit ASP.NET Core zu erstellen. Du wirst lernen, wie man Backend- und Frontendfunktionalität implementiert, mit einer Datenbank kommuniziert, \(Unit\) Tests schreibt und die Anwendung online stellt.

## Was ist ASP.NET Core?

ASP.NET Core ist ein Web Framework von Microsoft für die Erstellung von Webanwendungen, APIs und Microservices. Es nutzt bekannte Entwurfsmuster, wie MVC \(Model-View-Controller\), dependency injection und eine Request Pipeline bestehend aus Middleware. Es ist Open Source, lizenziert unter der Apache 2.0 Lizenz, der Quellcode ist frei verfügbar und die Community wird dazu ermutigt Bugfixes und neue Funktionen beizutragen.

ASP.NET Core läuft auf Microsoft's .NET Laufzeitumgebung, ähnlich der Java Virtual Machine \(JVM\) oder dem Ruby Interpreter.  
Du kannst ASP.NET Core Anwendungen in einer Vielzahl von Programmiersprachen \(C\#, Visual Basic, F\#\) verfassen. C\# ist die bevorzugte Sprache und wird auch in diesem Buch benutzt. Du kannst ASP.NET Core Anwendungen auf Windows, Mac und Linux entwickeln, sowie ausführen.

## Warum benötigen wir ein weiteres Web Framework?

Es existieren bereits eine breite Auswahl wunderbarer Webframeworks: Node/Express, Spring, Ruby on Rails, Django, Laravel und viele weitere. Welche Vorteile hat ASP.NET Core?

* **Geschwindigkeit. **ASP.NET Core ist schnell. Da .NET code kompiliert ist, läuft es deutlich schneller als Code von interpretierten Sprachen wie JavaScript oder Ruby. Ebenfalls ist ASP.NET Core für Multithreading und asynchrone Tasks optimiert. Es ist üblich eine 5 bis 10-fache Geschwindigkeit gegenüber Node.js Code zu beobachten.

* **Ökosystem.** ASP.NET Core mag neu sein, .NET ist allerdings schon länger verfügbar. Auf NuGet \(.NET Paket Manager; wie npm, Ruby gems oder Maven\) finden sich tausende von Pakete. Es gibt Lösungen für JSON Deserialization, Datenbankanbindung, PDF Erstellung und vieles, vieles mehr.

* **Security.** The team at Microsoft takes security seriously, and ASP.NET Core is built to be secure from the ground up. It handles things like sanitizing input data and preventing cross-site request forgery \(XSRF\) automatically, so you don't have to. You also get the benefit of static typing with the .NET compiler, which is like having a very paranoid linter turned on at all times. This makes it harder to do something you didn't intend with a variable or chunk of data.

* **Sicherheit.** Das Microsoft Team nimmt Sicherheit sehr ernst und ASP.NET Core wurde mit Bedacht für Sicherheit entwickelt. Dinge wie das reinigen von Eingabedaten und verhindern von Cross-Site Request Forgery \(XSRF\) werden automatisch erledigt.

## .NET Core und.NET Standard

In diesem Buch wirst Du ASP.NET Core \(das Webframework\) kennenlernen. Ich werde ab und zu das .NET Runtime \(die darunterliegende Bibliothek, welche .NET Code ausführt\) erwähnen.

Weiterhin wirst Du die Begriffe .NET Core und .NET Standard hören. Die Namenskonvention kann verwirrend sein, hier eine einfache Erklärung:

**.NET Standard **ist ein platform-unabhängiges Interface welches die enthaltenen Funktionen und APIs in .NET definiert. .NET Standard enthält keinen wirklichen Code oder Funktionalität, nur die API Definitionen. Es existieren verschiedene "Versionen" oder Level des .NET Standards die reflektieren wieviele APIs verfügbar sind \(oder wie groß die API Funktionalität ist\). Als Beispiel verfügt .NET Standard 2.0 über mehr APIs als .NET Standard 1.5 und dieser wieder rum mehr als .NET Standard 1.0.

**.NET Core** ist die .NET Laufzeitumgebung, welche auf Windows, Mac oder Linux genutzt werden kann. Es implementiert die APIs definiert im .NET Standard Interface mit dem dazugehörigen Platform-spezifischen Code. Du wirst dieses System auf Deinem Computer nutzen um ASP.NET Core Anwendungen zu programmieren und auszuführen.

Und zur Vervollständigung: **.NET Framework** ist eine andere Implementierung des .NET Standard, ausschließlich für Windows. Dies war der Standard bis .NET Core erschien und .NET auf Mac und Linux möglich machte. ASP.NET Core kann außerdem auf dem Windows-spezifischen .NET Framework aufbauen, allerdings werde ich darauf nicht weiter eingehen.

Falls Du durch die ganzen Namenskonventionen etwas verwirrt bist, keine Sorge! Wir gelangen zur richtigen Programmierung in einem Moment.

## Hinweis für ASP.NET 4 Programmierer

Falls Du zuvor noch keine Erfahrungen mit ASP.NET gemacht hast kannst Du dieses Kapitel überspringen!

ASP.NET Core ist ein von Grund auf Neuentwicklung von ASP.NET mit dem Fokus auf Modernisierung des Frameworks und die Abtrennung von System.Web, IIS und Windows. Wenn Du Dich an OWIN/Katana Zeugs von ASP.NET 4 erinnern kannst: das Katana Projekt wurde zu ASP.NET 5, welches final zu ASP.NET Core umbenannt wurde.

Aufgrund der Katana "Altlast", die`Startup` Klasse ist Vorderansicht und Mittelpunkt, weiter gibt es `Application_Start`oder`Global.asax`nicht mehr.   
Die gesamte Pipeline wird von Middleware verwaltet und die Abtrennung von MVC und Web API existiert so nicht mehr: Controller können Views, Status Codes oder Daten returnen. Dependency Injection ist bereits inkludiert, dadurch sparst Du die Installation und Konfiguration von Container wie StructureMap oder Ninject. Das gesamte Framework ist außerdem für Geschwindigkeit und Laufzeiteffizienz optimiert.

Okay, genug der Einleitung! Lass uns mit ASP.NET Core beginnen!

