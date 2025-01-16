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
3. Zdalna aktualizacja oprogramowania biletomatów
```
@startuml

== Zdalna aktualizacja oprogramowania biletomatów ==
actor Administrator as Admin
participant "System Centralny" as CentralSystem
participant "Biletomat" as TicketMachine

Admin -> CentralSystem : Rozpocznij aktualizację oprogramowania
CentralSystem -> TicketMachine : Wyślij nowe oprogramowanie
TicketMachine --> CentralSystem : Potwierdź instalację
CentralSystem -> Admin : Status aktualizacji

@enduml
```

4. Dostęp do raportów sprzedaży w czasie rzeczywistym
```
@startuml

== Dostęp do raportów sprzedaży w czasie rzeczywistym ==
actor Administrator as Admin
participant "System Centralny" as CentralSystem

Admin -> CentralSystem : Poproś o raport sprzedaży
CentralSystem --> Admin : Wyślij raport sprzedaży

@enduml
```
5.Konfiguracja biletów, promocji i taryf
```
@startuml

== Konfiguracja biletów, promocji i taryf ==
actor Administrator as Admin
participant "System Centralny" as CentralSystem
participant "Biletomat" as TicketMachine

Admin -> CentralSystem : Zaktualizuj taryfy i promocje
CentralSystem -> TicketMachine : Rozpocznij synchronizację danych
TicketMachine --> CentralSystem : Potwierdzenie synchronizacji
CentralSystem -> Admin : Potwierdzenie aktualizacji

@enduml
```
