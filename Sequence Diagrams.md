# Sequence Diagrams

## For user 'use cases'

1. Wybór biletu
```
@startuml

== Wybór biletu ==
actor Użytkownik as User
participant "Ekran Biletomatu" as Screen
participant "System Biletowy" as TicketSystem

User -> Screen : Wybierz typ biletu
Screen -> TicketSystem : Pobierz listę dostępnych biletów
TicketSystem --> Screen : Wyślij listę biletów
Screen -> User : Wyświetl dostępne bilety

@enduml
```

2. Zakup biletu
```
@startuml

== Zakup biletu ==
actor Użytkownik as User
participant "Ekran Biletomatu" as Screen
participant "System Transakcyjny" as TransactionSystem
participant "System Biletowy" as TicketSystem

User -> Screen : Potwierdź zakup biletu
Screen -> TransactionSystem : Zainicjuj transakcję płatniczą
TransactionSystem --> Screen : Status transakcji (Sukces)
Screen -> TicketSystem : Rejestruj bilet
TicketSystem --> Screen : Potwierdzenie rejestracji
Screen -> User : Wyświetl potwierdzenie zakupu

@enduml
```
