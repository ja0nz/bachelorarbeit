

# Introduction

> Simplicity is prerequisite for reliability. - Edsger W. Dijkstra



Introduction: from simplicity to Microservices to w3c specifications ... and beyond

Der Erfinder der Programmiersprache Clojure, Rich Hickey, ist ohne Zweifel eine Koryphäe auf seinem Gebiet, der Strukturierung von komplexen Systemen. In einer vielbeachteten Keynote aus dem Jahr 2012 geht er auf etymologisch-philosophische Spurensuche nach dem Wort **simplicity ** aus Sicht eines Softwareentwicklers.[^rich] Das Adjektiv *simple* hat demnach seinen Ursprung im lateinischen Wort *simplex*, was soviel wie *einfach* oder *einzeln* bedeutet. In Gegensatz dazu stehen Eigenschaften wie *complex* oder *multiplex*. Qualitative Software ist, so Hickey, vor allem simpel -  im Prozess, im Design, in der Struktur und in der Entwicklung.

[^rich]: [Rails Conf 2012 Keynote: Simplicity Matters by Rich Hickey](https://www.youtube.com/watch?v=rI8tNMsozo0&t=48s)

Bezeichnend für diese Keynote ist, dass sie von Rich Hickey im Rahmen einer Webentwicklerkonferenz gehalten wurde. Software für den Browser war (und ist) seit langer Zeit maßgeblich geprägt von **Komplexität** auf mehreren Ebenen. Im Laufe dieser Bachelorarbeit werden diese Stru





* Das *Document Object Model* als Rückgrad jeder Webapplikation ist hierarchisch strukturiert und deren Elemente damit keinesfalls unabhängig in ihrer Darstellung und Reihenfolge.
* JavaScript als single-threaded Skriptsprache lässt sich schlecht ihn ihrem Verhalten isolieren, ist Fehleranfällig und hatte lange Zeit nur sehr wenig idiomatische Lösungsansätze für komplexe Probleme, wie beispielsweise Asynchronität
* CSS ist geprägt von stetigem Überschreiben vorher definierter Regeln und verletzt damit Simplizität in ihrer Struktur, Design und dem Entwicklungsprozesses auf bester Art und Weise.




---

Betrachtet man andere populäre Webframeworks dieser Zeit, wie beispielsweise React oder Angular, lässt sich ziemlich schnell ein gemeinsames Designpattern ausmachen, wie Komponenten intern ihre Zuständen verwalten. Der Facebook Entwickler Dan Abramov hat dieses dichotome Pattern systematisch erfasst und in zwei Kategorien eingeteilt.

Nach Abramov existieren zum einen Komponenten,  die alleine für das **Darstellen von Information** zuständig sind. Diese Komponenten nehmen keinerlei Einfluss auf  Informationen oder anderen Komponenten um sich herum. Sie sind im wahrsten Sinne passiv und fremdgesteuert über klar definierte Schnittstellen. Diese Komponenten sind häufig flexibel einsetzbar und hochgradig wiederwerwendbar. Abramov nennt diese Komponenten "Presentational Components".[@Abramov2015] Verortet man diese Art von Komponenten innerhalb des *MVC Pattern*, sind die Komponenten reine *View-Elemente*.

Im Gegensatz dazu stehen Komponenten,  die für die **Verarbeitung von Informationen** zuständig sind. Diese so genannten "Container Components" haben oft einen internen Zustand, den sie verändern können und an ihre Kindkomponenten weiterreichen können.[@Abramov2015] Im *MVC Pattern* handelt es sich um die *Controller*. In der funktionalen Programmiersprache Elm werden diese Elemente *Updater* genannt, was ihre Funktion noch besser umschreibt. 

Ein üblicher eventgesteuerter Webservice setzt sich aus unterschiedlichsten Komponenten zusammen, die wiederum unterschiedlichste Eventlistener & -emitter  in sich subsummieren. Diese inhärente Komplexität verlangt geradezu nach einer klaren, deterministischen Struktur des Webservices, die das Zusammenspiel orchestriert. In der Analogie des Orchesters gesprochen, benötigt der Webservice (oder sogar die gesamte Webapplikation)  einen Dirigenten, der für die Steuerung verantwortlich ist.


# Microservices

Opening up the case for *Browsernative Microservices* brings up the question about the concept microservices in general. In fact the concept of microservices has many facets, stretching beyond disciplines and technical boundaries. It lacks a formal standardization but there are certain ideas emergine from this pattern. As a primary source of truth this articles relies on the work of Sam Newman, who has written a comprehensive guide in *Building Microservices*. The purpose of this section is to match those ideas against the manifestations of web components. 

In a nutshell a microservice is a small, autonomous service that works together with other services seamlessly.[@Newman2015, p. 2] or with the words of Fowler and Lewis: "It is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms,..."[@Fowler2014] Microservices incorporate many ideas, like *domain-driven design* where we try to represent the real world in our code.[@Newman, p. 2] Or making use of *continuous delivery* for pushing software rapidly through *automated deployment* mechanisms in production.[@Fowler2014] And, last but not least, microservices utilizes the idea of small teams with a lot of product knowledge working mostly autonomous on their very own service with their very own set of tools and techniques.

## Technical perspective

Shift of paradigms / BFF / Platform agnostic / changes in infrastructure like APIs Databanks / Deployment 

Talking about microservices  in a browsernative context isn't that far fetched as microservices themselves incorporate many ideas from the web. Exemplary, microservices often communicate via an HTTP request-response with resource API's and lightweight messaging.[@Fowler2014] Nevertheless, while (server-side) microservices offer wide ranges of technical possibilities, we must take into account that (client-side) browsers come with certain constraints and limitations.

Fowler and Lewis issue a call for using services as components. A component is regarded as a unit of software that is independently replaceable and upgradeable. The main advantage of a component in contrast of library is the possibility of an independent deployment. It aligns perfectly with the main goal of a microservice architecture to strip away most of the dependencies in favour of clean interfaces.[@Fowler2014] 



Components



First of all, from a technical perspective, a microservice reinforces the *Single Responsibility Principle* defined by Robert C. Martin: "Gather together those things that change for the same reason and separate those things that change for different reasons."[@Martin] An a way this principle tackles another often cited design principle of the *seperation of concerns*. Web Components incorporate this principle in multiple ways while still remaining flexible. 

Most obvious ist the gathering of all related code under the umbrellar of a single HTML tag. Grouping together HTML, JS and CSS Code in a safe, sandboxed environment exposes the possibility to build more cohesive and understandable services. In the typical global nature of web development those three pillars are separated. This circumstance left the developer switching back and forth between code bases developing a tricky (and sometimes biased) way to glue related parts together.

Secondly, the sub-standard *custom elements* introduces so called lifecycle methods and a getter/setter interface exposing the functionality to the developer. Event handling, for example, can be registered in place which is much more declarative than assigning event listeners from the outside. Of course, this events can be pushed down to nested tags, allowing an increasingly granular system design. This approach will be explained further in the upcoming sections.

The concept of microservices incooperates not only a technical perspective. Microservice patterns are a product of real-world usage.[@Newman2015, p. 1] In a real world we typical have to deal with the so called *Conway's Law*:

> "organizations which design systems ... are constrained to produce designs which are copies of the communication structures of these organizations". [@Conway1968]

 Following this logic any company, whether it is web-related or not,  should be devided in units grouped around a destinct business service to optimise the workflow. Fowler and Lewis outlines this approach as an "alignment of business capabilities"[@Fowler2014] While this  kind of structure may be true for companies like Google or Amazon, there is a vast majority of companies developing for the web which are grouped around tasks.[@Issa2016] A very common structure is formed by the technology stack (UX Designers, Frontend- & Backend Developers) or by separating teams along the product lifecycle (development, testing, deployment). 

Advocators from the microservice approach propose a different model.  best described by . Web components are one (but important) way to tie up those diciplines as one component can host a single independent business service. Combined with a flexible backend service these components can be huge gain over the cumbersome functional organizational approach.



The ideas transcending from the microservice approach offers plenty of choices and decisions how to proceed with designing a program or to structure a process.











Macroperspektive / Composition

http://alistair.cockburn.us/Hexagonal+architecture

MVC Pattern

Pure frontend vs heavy backend

# Progressive Enhancement

Chapter about progressive enhancement