# Ausgangssituation

en der Browserplattform erläutern.[@Katz2013] Oder man könnte die organisatorische Seite betrachten und die Schwerfälligkeit von Standardisierungsprozessen anprangern.[@Walton2016] Oder aber man nimmt die historische Entwicklung in Augenschein. Die Zeiten statischer HTML/CSS Seiten auf Desktopgeräten ist mithin noch nicht lange her.

cript als Zielsprache betrachtet, die vielen Entwicklern Schwierigkeiten bereitet.[@Berner2016]

nftige Unsicherheiten abzuwägen.[@Dodson2016, S. 1-3] Die Unsicherheit, die Frameworks immer anhaftet, ist die Lebensdauer derselben.

Mit *Web Components* ist der Entwickler in der Lage, eigene HTML Elemente zu definieren und diese per Templates zu ex- & importieren. Darüber hinaus können sie JavaScript und CSS Funktionalität enthalten und diese vom Rest der Webseite abzukapseln. Ziel dieser Arbeit ist die systematische Erfassung und Risikoabwägung der neuen Technologien sowie eine praktische Erläuterung möglicher Architekturmodelle. Bisher gibt es keine einheitliche Bestpractice, wie denn die Komponenten umzusetzen sind, obwohl diese Technologien bereits länger durch Polyfills genutzt werden können. Manch ein Entwickler fürchtet schon eine Flut von schlecht gebauten Komponenten, die wiederum neue Probleme schaffen könnten.[@Keith2014]

# Vorgehensweise

Den Anfang dieser Arbeit soll eine Analyse der aktuellen Situation der Frontend Entwicklung aufzeigen. Dort soll auf die Problematik der bisherigen Architekturmodelle und die Probleme mit monolithischen Frameworks eingegangen werden. Außerdem soll dieser Teil vor Augen führen, warum es bisher nur mit zusätzlicher Abstraktionsebenen möglich war einen modularen Aufbau von Web Applikationen zu ermöglichen.

Im nächsten Abschnitt der Arbeit sollen die neuen Standards aufgeschlüsselt, zugänglich gemacht und auf Anwendungsmöglichkeiten untersucht werden. Explorativ sollen Bestpractices offengelegt werden und mögliche Einbettungen ins Gesamtsystem diskutiert werden. Auch die Probleme, wie sie beispielsweise bei alten Browsern auftreten können, sollen hier behandelt werden.  
So we are

> This is a blockquote

´hello world´

````javascript
Javascript baby
````

`so this is the js world`

   one more last test

1. This is the list

   This is a sub 

2. Anothoter list


- [ ] oohhhhhhh

Der letzte Abschnitt soll das Thema mit einer Metaebene abrunden, in der auch die neuen CSS Standards *Houdini* als Teil des Gesamtsystems betrachtet werden sollen.[^h]

[^manifesto]: https://extensiblewebmanifesto.org/

[^wc]: https://www.w3.org/standards/techs/components

[^h]: https://drafts.css-houdini.org/
