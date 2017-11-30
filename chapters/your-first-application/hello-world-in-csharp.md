## Hallo Welt in C\#

Bevor Du mit ASP.NET Core loslegst, starte mit einer einfachten C\# Anwendung.

All dies kannst Du über die Kommandozeile erledigen. Öffne ein Terminal \(oder PowerShell unter Windows\), navigiere zu einem Ordner wo Du Projekte lagern möchtest, beispielweise "Eigene Dokumente":

```
cd Documents
```

Nutze den`dotnet` Befehl um ein neues Projekt zu erzeugen:

```
dotnet new console -o CsharpHelloWorld
cd CsharpHelloWorld
```

Dies erstellt ein simples C\# Programm welches Text auf der Kommandozeile ausgibt. Es besteht aus zwei Dateien: eine Projektdate \(mit der `.csproj` Endung\) und eine C\# Codedatei \(mit der `.cs`Endung\). Wenn Du ersteres in einem Editor öffnest siehst Du folgendes:

`CsharpHelloWorld.csproj`

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Die Projektdatei ist XML-basiert und definiert eine Metadaten des Projektes. Später, wenn Du andere Paketverweise hinzufügst werden diese dort zu finden sein \(ähnlich der `project.json` Datei bei npm\). Du wirst diese Datei selten per Hand editieren.

`Program.cs`

```csharp
using System;

namespace CsharpHelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

`static void Main`ist die Einstiegspunktmethode einer C\# Anwendung und in einer Klasse enthalten \(ein Typ von Codestruktur oder Modul\) namens `Program`. Die `using`Anweisung am Anfang der Datei importiert die eingebetteten Systemklassen von .NET und stellt diese zur Verfügung.



From inside the project directory, use `dotnet run` to run the program. You'll see the output written to the console after the code compiles:

```
dotnet run

Hello World!
```

That's all it takes to scaffold and run a .NET program! Next, you'll do the same thing for an ASP.NET Core application.

