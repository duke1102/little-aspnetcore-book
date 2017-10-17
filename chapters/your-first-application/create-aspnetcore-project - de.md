## Ein ASP.NET Core Projekt erstellen
Falls Du noch im Ordner des Hello World Beispielprojektes bist, geh eine Ebene zurück zu Deinen Dokumenten oder Benutzerverzeichnis:

```
cd ..
```

Erstelle danach per `dotnet new` ein neues Projekt, diesmal mit ein paar Extras:

```
dotnet new mvc --auth Individual -o AspNetCoreTodo
cd AspNetCoreTodo
```

Dies erzeugt ein neues Projekt unter Nutzung der `mvc` Vorlage und fügt einige Zusatzmodule für Authentifizierung und Sicherheit zum Projekt. (Sicherheit wird nochmal genauer im *Sicherheit und Identität* Kapitel behandelt.) 

Du wirst einige neue Dateien im Projektordner auffinden. Alles was du jetzt machen musst ist das Projekt zu starten:

```
dotnet run

Now listening on: http://localhost:5000
Application started. Press Ctrl+C to shut down.
```

Anstatt alles zum Terminal zu schreiben und sich danach beenden startet das Programm einen Webserver zum Einsatz auf dem Port 5000.

Öffne Deinen Browser und navigiere zu `http://localhost:5000`. Du wirst die Standard ASP.NET Core Startseite sehen, wenn alles richtig läuft! Wenn du fertig bist kannst du den Server per STRG-C im Terminal beenden.

### Teile eines ASP.NET Core Projektes

Die `dotnet new mvc` Vorlage generiert eine Vielzahl an Dateien und Ordner für Dich. Hier sind die wichtigsten Dinge an Bord: 

* Die **Program.cs** und **Startup.cs** konfigurieren den Webserver und die ASP.NET Core pipeline.
In der `Startup` Klasse fügst du Middleware ein, welche eingehende Requests verarbeitet, Dinge wie statischen Content oder Fehlerseiten serviert.
Ebenso fügst Du hier Deine eigenen Services zum Dependency Injection Container hinzu. (Später mehr hierzu.)

* The **Models**, **Views**, and **Controllers** directories contain the components of the Model-View-Controller (MVC) architecture. You'll explore all three in the next chapter.

* The **wwwroot** directory contains static assets like CSS, JavaScript, and image files. By default, the bower tool is used to manage CSS and JavaScript packages, but you can use whatever package manager you prefer (npm and yarn are popular choices). Files in `wwwroot` will be served as static content, and can be bundled and minified automatically.

* The **appsettings.json** file contains configuration settings ASP.NET Core will load on startup. You can use this to store database connection strings or other things that you don't want to hard-code.

### Tips for Visual Studio Code

If you're using Visual Studio Code (or Visual Studio) for the first time, here are a couple of helpful tips to get you started:

* **F5 to run (and debug breakpoints)**: With your project open, press F5 to run the project in debug mode. This is the same as `dotnet run` on the command line, but you have the benefit of setting breakpoints in your code by clicking on the left margin:

![Breakpoint in Visual Studio Code](breakpoint.png)

* **Lightbulb to fix problems**: If your code contains red squiggles (compiler errors), put your cursor on the code that's red and look for the lightbulb icon on the left margin. The lightbulb menu will suggest common fixes, like adding a missing `using` statement to your code:

![Lightbulb suggestions](lightbulb.png)

* **Compile quickly**: Use the shortcut `Command-Shift-B` or `Control-Shift-B` to run the Build task, which does the same thing as `dotnet build`.

### A note about Git

If you use Git or GitHub to manage your source code, now is a good time to do `git init` and initialize a Git repository in the project directory. Make sure you add a `.gitignore` file that ignores the `bin` and `obj` directories. The Visual Studio template on GitHub's gitignore template repo (https://github.com/github/gitignore) works great.

There's plenty more to explore, so let's dive in and start building an application!
