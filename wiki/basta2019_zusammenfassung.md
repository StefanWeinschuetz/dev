#Basta 2019

## C#7
.net core implementiert .net standard.
.net framework bleibt auf .net standard 2.0. .net Framework wird nicht .net standard 2.1 implementieren.

Soll eine BL geschrieben werden, der auf so vielen Implementierungen wie möglich laufen soll, dann .Net Standard benutzen.

Die Main-Methode kann async gemacht werden.

Task.Delay(1000);
SonarQube + SonarLint

https://github.com/0xd4d/dnSpy


.Net Object Allocation tracking

Lokale Funktionen schreiben sich wie jede andere Funktion auch.

Pattern Matching
    IEnumerable -> IList

IList hat mehr Methoden als IEnumerable.

double? ->Nullable double

Ein Tupel ist eine Variable die aus mehreren Teilen besteht.
Es muss für mehrere Rückgaewerte keine Klasse dafür geschrieben werden.

Neu ist das die Tupel Values sind und somit über den Stack und nicht über den Heap zurückgegeben werden.

BenchmarkDotNet
https://benchmarkdotnet.org/articles/overview.html

shallow und deep immutable


BestPractice: Structuren sollen ReadOnly sein.
Besser für Multithreading.

readonly struct

in keyword als argument. Variablen können als Referenz übergeben werden, aber nicht beschrieben werden.

closures -> 

ReadOnly modifier funktioniert bei der deklaration der struktur oder bei der deklaration der variablen.

Ref rein und ref raus:
ref argument + ref return

ref + readonly

ref structs können nur am Stack leben, können NIE an den Heap übergeben werden.
Wenn die Variable dann auf dem Stack lebt, dann ist diese ThreadSafe.
Das ref Schlüsselwort kann auch bei der deklaration und dem anlegen der variablen benutz werden.

Span<T> Immer ThreadSave: Lebt am Stack (ref) und immutable (readonly)


Mittels stackalloc können Arrays auf dem Stack angelegt werden.
Ansonnsten werden Arrays immer auf dem HEAP erzeugt.

Klasse lebt am HEAP und nicht am Stack.
Klassen leben IMMER im HEAP.

ManagedHeap
ManagedStack
UnmanagedHeap
UnmanagedStack

Span<T> kann auf den STack und den Heap zugreifen sowohl managed als auch unmanaged.
Einheitliches Programmiermodell.

Span<T> ist ein Zugriff auf irgendeinen Speicherplatz mit Länge. Egal ob managed, unmanaged, Heap oder Stack.

ducktyping

ReadOnlySpan -> Deep immutable!
Span ist kein Deep Immutable!

in: Per reference übergeben, aber nicht änderbar!

Memory<T> ist ein Wrapper um Span<T>.
Span<T> kann nur auf dem Stack leben.

Memory<T> kann auf dem Heap arbeiten.

TIP: Nimm immer Span<T>. Wenn dies nicht funktioniert, dann nehme ein Memory<T>.

Die bekannten Stringoperationen sind nicht so hoch optimiert, wie wenn mit Span,Memory<T> gearbeitet wird.
Jedoch sind diese einfacher zu lesen, d.h. die Entwicklereffizienz ist an dieser Stelle viel höher.

## C#8
IEnumerable + yield-return

neues Interface IAsyncEnumerable

IDisposable
IAsyncDisposable

await foreach -> Neues Schlüsselwortpaar

switch expression

Neuer Datentyp "Index"

Vorne Zero-Based
Hinten One-Based

Hallo

Index = 1 = a
Index = 0 = H

Index = ^1 = o


## Dokumentation
Prototyping

Markdown

mermaidjs

https://mermaidjs.github.io/

reveal js

Konzeptionelle Doku muss wie Code angesehen werden!

https://jekyllrb.com/

github pages

https://gohugo.io/

https://dotnet.github.io/docfx/

Stropek -> Timecockpit -> Selbst implementierte DSL

C# Codedoku: 
source code -> Auf ranges verweisen


CalculatorWebApi ->Swashbuckle.AspNetCore.Cli
Continuous integration -> generierung von swagger-files in der pipeline


azure-pipelines.yml

jobs:
    job: BuildAndTestCode
    job: BuildDocumentation


AzureDevOps

DeploymentSlots
AzureWebService

AzureDockerRegistry

nginx:alpine

fork vs. branch?

## Konferenz
Todo: Uno Playground???
Todo: Electron Godova???
Circuit Breaker Pattern
Am besten bei jeder REST Kommunikation einbauen.
Stateful Retry
BPMN Workflow Engine
Camunda
Azure Durable Functions
HTTP202 Accepted: Habs bekommen und gebe dir das Ergebnis später

Idempotenz

SAGA Pattern

Camunda: Pull-Mechanismus. Ein Client kann sich subscriben um Arbeit entgegenzunehmen.

GraphQl kann sich per Websockets registrieren um Daten gepushed zu bekommen.
Der GraphQL-Client sollte Batching unterstützen.

CloundFoundry?

MongoDb:
Integriert first Denkansatz

TODO: Test: Ein Ubuntu via Docker starten und MongoDb installieren. Den Container stoppen und wieder starten, ist die Datenbank dann noch vorhanden?

MongoDb Tool Robo 3T

Erweiterung der WindowsConsole mit ConEMU
Strg Shift e splittet die Console.

Speakerdeck
Domain Storytelling
Verschiedene Modelle (Sichten) für ein und die selbe Sache, wie ein Atlas z.B. Es gibt geografische Sichten, politische usw.

Structure 101 Software???

## DevOps Workshop

Staging
SwapSlots
Langlaufende Tests nur im DailyBuild.

Newman ist Postman CLI um automatisch PostmanCollections zu testen.

__Monitoring wichtiger als Testing__

RDPManager Software

Eine Pipeline kann konfiguriert werden, viele Branches zu bauen.
Man kann einer Pipeline sagen das diese zuständig ist, alle FeatureBranches zu bauen:

Features/*

Artifacts

Ein Release kann Input aus mehreren BuildPipelines erhalten.

Dependencies können als Artifacte gecached werden. Wenn NuGet dann einmal nicht vorhanden ist, funktioniert der Build trotzdem. DAnn wird die gecachte Variante genommen, ist Nuget vorhanden, dann wir die aktuelle genommen.

Semantic Versioning
gitversion

In AzureDevOps können Branch-Policies definiert werden. Wer darf in Master pullen?

GIT Pull-Push
Simulierte Merges
Google Mono Repository

Cherry Picking
Eine schon releaste Version die älter ist als der Master fixen.