
# Swift Todo App
En todo app skrevet i Swift og SwiftUI for at prøve at bruge Swift i et reelt produkt.
Appen er lavet som en iOS app, i Xcode.

Efter at have undersøgt programmeringssproget Swift, valgte jeg for at afprøve sproget i praksis at lave en todo app. Denne app har jeg lavet ved hjælp af en tutorial på YouTube[^1], da jeg ikke følte jeg kunne lære nok af teknologierne  i den givne tid til at kunne klare det på egen hånd. 

## App overblik
- For iOS
- Sprog: Swift
- Framework: SwiftUI
- Arkitektur: Model-View-ViewModel (MVVM)

## Features
- Todo list med CRUD egenskaber

## Test
Appen er testet i iPhone 17 pro simulator i Xcode

## Tekniske valg
Jeg har brugt frameworket SwiftUI, IDE: Xcode, og Swift til at bygge denne app. SwiftUI har jeg brugt da det var hvad der blev brugt i den tutorial jeg har fulgt. Xcode har jeg brugt da det kommer med indbygget iPhone simulator og compiler så jeg kan teste koden undervejs.


## Teknologien i praksis
### Arkitektur: Model-View-ViewModel (MVVM)

Jeg har bygget appen efter MVVM arkitekturen for at sørge for der er en klar seperation of concerns, ved at adskille appens data, logik og visuelle del.

- **Model:** Er datastrukturen for appen, den fortæller der er et todo-element der har et ID, en string, og et flueben for ja/nej. Der er ikke noget visuelt her.
- **View:** Er den visuelle del af appen. Det er her det vi laver det som brugeren interagere med. Så knapper, todo's osv. Så når en bruger trykker "Delete" i appen sender denne del beskeden videre til ViewModel, som så sletter todo'en. 
- **ViewModel:** Denne del hjernen i appen. ViewModel håndtere logikken. Den henter todo's, sletter todo's, tilføjer todo's osv.

## Dataflow og state management
For at appen kan opdatere sig selv automatisk, når der bliver tilføjet/fjernet todo'
s har jeg brugt et indbygget system is SwiftUI. Det fungere lidt på samme måde som useState og ContextProvider i React.

- **@Published:** 
```swift
   @Published var items: [ItemModel] = []
```
 Som er appens State, har jeg brugt i min ViewModel til a lave listen med alle todo's. Ved hjælp af dette, hvis der sker en ændring i staten, opdateres appen med det samme.

- **@StateObject:**
```swift
    @StateObject var listViewModel: ListViewModel = ListViewModel()
```
 Som er appens Context Provider bliver brugt i TodoListApp.swift. Den sørger for at state bliver oprettet og bibeholdt på tværs af appen.
 
- **@EnvironmentObject:** 
```swift
    @EnvironmentObject var listViewModel: ListViewModel
```
Som er appens useContext bruger jeg i ListView og AddView til at kalde de funktioner jeg har i min ViewModel, som opdatere staten. Så når der bliver oprettet en ny todo af en bruger bliver den funktion der opretter en todo i ViewModel kaldt på grund af @EnvironmentObject

## Hvad fungerede godt og hvilke udfordringer var der.

Den største udfordring var at lære Xcode at kende, det tager langt tid, men det er dog rart der er en iPhone simulator i Xcode man kan bruge til at køre en build version af sin app i. 
Det der fungere godt er at selve sproget er ret nemt at sætte sig ind i, og det er rigtig godt i Xcode at det løbende kompilere så man kan se hvad man laver hele tiden. 
En anden udfordring er at lære SwiftUI også da det er et nyt framework kunne jeg godt bruge en uge mere på også at lære det. Så tror jeg det villle gå lidt nemmere med at lave et projekt som dette. Men da der er mange ting i SwiftUI der minder om React kunne jeg opsnappe nogle af tingene ret hurtigt.

## Hvordan kan teknologien bruges professionelt?
Swift bliver aktivt brugt til app udvikling til både iOS og macOS hele tiden. Nu hvor jeg har snuset lidt til det, ville jeg ikke være bange for at søge job, hvor dette kunne være noget jeg skulle lære. Hvilket også var én af grundene til jeg valgte at arbejde med Swift.














#### Referencer

[^1]: https://youtube.com/playlist?list=PLwvDm4VfkdpheGqemblOIA7v3oq0MS30i&si=feHDh4AY6mXiHkJf
