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

The book itself is updated frequently with bug fixes and new content. If you're reading a PDF, e-book, or print version, check the official website \([littleasp.net/book](http://www.littleasp.net/book)\) to see if there's an updated version available. Check the very last page of the book for version information and a changelog.

## Who this book is for

If you're new to programming, this book will introduce you to the patterns and concepts used to build modern web applications. You'll learn how to build a web app \(and how the big pieces fit together\) by building something from scratch! While this little book won't be able to cover absolutely everything you need to know about programming, it'll give you a starting point so you can learn more advanced topics.

If you already code in a backend language like Node, Python, Ruby, Go, or Java, you'll notice a lot of familiar ideas like MVC, view templates, and dependency injection. The code will be in C\#, but it won't look too different from what you already know.

If you're an ASP.NET MVC developer, you'll feel right at home! ASP.NET Core adds some new tools and reuses \(and simplifies\) the things you already know. I'll point out some of the differences below.

No matter what your previous experience with web programming, this book will teach you everything you need to create a simple and useful web application in ASP.NET Core. You'll learn how to build functionality using backend and frontend code, how to interact with a database, and how to test and deploy the app to the world.

## What is ASP.NET Core?

ASP.NET Core is a web framework created by Microsoft for building web applications, APIs, and microservices. It uses common patterns like MVC \(Model-View-Controller\), dependency injection, and a request pipeline comprised of middleware. It's open-source under the Apache 2.0 license, which means the source code is freely available, and the community is encouraged to contribute bug fixes and new features.

ASP.NET Core runs on top of Microsoft's .NET runtime, similar to the Java Virtual Machine \(JVM\) or the Ruby interpreter. You can write ASP.NET Core applications in a number of languages \(C\#, Visual Basic, F\#\). C\# is the most popular choice, and it's what I'll use in this book. You can build and run ASP.NET Core applications on Windows, Mac, and Linux.

## Why do we need another web framework?

There are a lot of great web frameworks to choose from already: Node/Express, Spring, Ruby on Rails, Django, Laravel, and many more. What advantages does ASP.NET Core have?

* **Speed.** ASP.NET Core is fast. Because .NET code is compiled, it executes much faster than code in interpreted languages like JavaScript or Ruby. ASP.NET Core is also optimized for multithreading and asynchronous tasks. It's common to see a 5-10x speed improvement over code written in Node.js.

* **Ecosystem.** ASP.NET Core may be new, but .NET has been around for a long time. There are thousands of packages available on NuGet \(the .NET package manager; think npm, Ruby gems, or Maven\). There are already packages available for JSON deserialization, database connectors, PDF generation, or almost anything else you can think of.

* **Security.** The team at Microsoft takes security seriously, and ASP.NET Core is built to be secure from the ground up. It handles things like sanitizing input data and preventing cross-site request forgery \(XSRF\) automatically, so you don't have to. You also get the benefit of static typing with the .NET compiler, which is like having a very paranoid linter turned on at all times. This makes it harder to do something you didn't intend with a variable or chunk of data.

## .NET Core and .NET Standard

Throughout this book, you'll be learning about ASP.NET Core \(the web framework\). I'll occasionally mention the .NET runtime \(the supporting library that runs .NET code\).

You may also hear about .NET Core and .NET Standard. The naming gets confusing, so here's a simple explanation:

**.NET Standard** is a platform-agnostic interface that defines what features and APIs are available in .NET. .NET Standard doesn't represent any actual code or functionality, just the API definition. There are different "versions" or levels of .NET Standard that reflect how many APIs are available \(or how wide the API surface area is\). For example, .NET Standard 2.0 has more APIs available than .NET Standard 1.5, which has more APIs than .NET Standard 1.0.

**.NET Core** is the .NET runtime that can be installed on Windows, Mac, or Linux. It implements the APIs defined in the .NET Standard interface with the appropriate platform-specific code on each operating system. This is what you'll install on your own machine to build and run ASP.NET Core applications.

And just for good measure, **.NET Framework** is a different implementation of .NET Standard that is Windows-only. This was the only .NET runtime until .NET Core came along and opened .NET up to Mac and Linux. ASP.NET Core can also run on Windows-only .NET Framework, but I won't touch on this too much.

If you're confused by all this naming, no worries! We'll get to some real code in a bit.

## A note to ASP.NET 4 developers

If you haven't used a previous version of ASP.NET, skip ahead to the next chapter!

ASP.NET Core is a complete ground-up rewrite of ASP.NET, with a focus on modernizing the framework and finally decoupling it from System.Web, IIS, and Windows. If you remember all the OWIN/Katana stuff from ASP.NET 4, you're already halfway there: the Katana project became ASP.NET 5 which was ultimately renamed to ASP.NET Core.

Because of the Katana legacy, the `Startup` class is front and center, and there's no more `Application_Start` or `Global.asax`. The entire pipeline is driven by middleware, and there's no longer a split between MVC and Web API: controllers can simply return views, status codes, or data. Dependency injection comes baked in, so you don't need to install and configure a container like StructureMap or Ninject if you don't want to. And the entire framework has been optimized for speed and runtime efficiency.

Alright, enough introduction. Let's dive in to ASP.NET Core!

