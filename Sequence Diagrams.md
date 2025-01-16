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
activate Screen
Screen -> TicketSystem : Pobierz listę dostępnych biletów
activate TicketSystem
TicketSystem --> Screen : Wyślij listę biletów
deactivate TicketSystem
Screen -> User : Wyświetl dostępne bilety
deactivate Screen
User -> Screen : Wybierz język interfejsu
activate Screen
Screen -> User : Wyświetl interfejs w wybranym języku
User -> Screen : Wyświetl licznik czasu decyzji

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
activate Screen
Screen -> TransactionSystem : Zainicjuj transakcję płatniczą
activate TransactionSystem
TransactionSystem -> Screen : Autoryzacja płatności (karta, gotówka, telefon)
TransactionSystem --> Screen : Status transakcji (Sukces/Odrzucenie)
deactivate TransactionSystem
Screen -> User : Wyświetl status transakcji
User -> Screen : Sprawdź poprawność transakcji
Screen -> TicketSystem : Rejestruj bilet
activate TicketSystem
TicketSystem --> Screen : Potwierdzenie rejestracji
deactivate TicketSystem
Screen -> User : Wyświetl potwierdzenie zakupu (wydruk biletu/elektroniczny bilet)
deactivate Screen

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
activate CentralSystem
CentralSystem -> TicketMachine : Wyślij nowe oprogramowanie
activate TicketMachine
TicketMachine -> CentralSystem : Zgłoś stan biletomatu (np. brak papieru)
TicketMachine --> CentralSystem : Potwierdź instalację
deactivate TicketMachine
CentralSystem -> Admin : Status aktualizacji
deactivate CentralSystem

@enduml
```

4. Dostęp do raportów sprzedaży w czasie rzeczywistym
```
@startuml

== Dostęp do raportów sprzedaży w czasie rzeczywistym ==
actor Administrator as Admin
participant "System Centralny" as CentralSystem
participant "Biletomat" as TicketMachine

Admin -> CentralSystem : Poproś o raport sprzedaży
activate CentralSystem
CentralSystem -> TicketMachine : Pobierz dane sprzedaży
activate TicketMachine
TicketMachine --> CentralSystem : Wyślij dane sprzedaży
deactivate TicketMachine
CentralSystem --> Admin : Wyślij raport sprzedaży
deactivate CentralSystem

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
activate CentralSystem
CentralSystem -> TicketMachine : Rozpocznij synchronizację danych
activate TicketMachine
TicketMachine --> CentralSystem : Zgłoś stan synchronizacji
deactivate TicketMachine
CentralSystem -> Admin : Potwierdzenie aktualizacji
deactivate CentralSystem

@enduml
```
