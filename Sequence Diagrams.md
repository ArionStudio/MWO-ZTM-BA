# Sequence Diagrams

## For user 'use cases'

1. Wybór biletu
```
@startuml

== Wybór biletu ==
actor Użytkownik as User
participant "Ekran Biletomatu" as Screen
participant "System Biletowy" as TicketSystem

User -> Screen : Wybierz język interfejsu [1.5]
activate Screen
Screen -> User : Zaktualizowano interfejs
User -> Screen : Wybierz typ biletu [1.4]
Screen -> TicketSystem : Pobierz listę dostępnych biletów [4.3]
activate TicketSystem
TicketSystem --> Screen : Wyślij listę biletów
deactivate TicketSystem
Screen -> User : Wyświetl dostępne bilety
Screen -> User : Wyświetl licznik czasu decyzji [1.3]
deactivate Screen

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

User -> Screen : Potwierdź wybór biletu
activate Screen
Screen -> TicketSystem : Zweryfikuj dostępność biletu
activate TicketSystem
TicketSystem --> Screen : Potwierdzenie dostępności
deactivate TicketSystem
Screen -> User : Wyświetl informacje o płatności
User -> Screen : Wybierz metodę płatności (karta/gotówka/NFC)
Screen -> TransactionSystem : Autoryzacja płatności
activate TransactionSystem
TransactionSystem --> Screen : Status transakcji (Sukces/Odrzucenie)
deactivate TransactionSystem
TransactionSystem -> User : Wydaj reszte 
Screen -> User : Wyświetl status transakcji
Screen -> TicketSystem : Zarejestruj bilet
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
participant "System Wsparcia Technicznego" as SupportSystem

Admin -> CentralSystem : Rozpocznij aktualizację oprogramowania [6.1]
activate CentralSystem
CentralSystem -> TicketMachine : Sprawdź stan biletomatu [5.1]
activate TicketMachine
TicketMachine -> SupportSystem : Zgłoś ewentualne błędy (np. brak papieru) [5.2]
SupportSystem --> TicketMachine : Potwierdzenie przyjęcia zgłoszenia
TicketMachine --> CentralSystem : Status biletomatu
CentralSystem -> TicketMachine : Wyślij nowe oprogramowanie
TicketMachine --> CentralSystem : Potwierdź instalację
deactivate TicketMachine
CentralSystem --> Admin : Status aktualizacji
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
participant "System Wsparcia Technicznego" as SupportSystem

Admin -> CentralSystem : Poproś o raport sprzedaży [6.2]
activate CentralSystem
CentralSystem -> TicketMachine : Pobierz dane sprzedaży [5.1]
activate TicketMachine
TicketMachine --> CentralSystem : Wyślij dane sprzedaży [5.2]
deactivate TicketMachine
CentralSystem -> SupportSystem : Zgłoś ewentualne problemy (np. brak raportów) [5.2]
SupportSystem --> CentralSystem : Potwierdzenie przyjęcia zgłoszenia
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
participant "System Wsparcia Technicznego" as SupportSystem

Admin -> CentralSystem : Rozpocznij konfigurację taryf i promocji [6.3]
activate CentralSystem
CentralSystem -> TicketMachine : Prześlij nowe ustawienia [4.4]
activate TicketMachine
TicketMachine -> SupportSystem : Potwierdź możliwość wdrożenia nowych taryf [5.1]
SupportSystem --> TicketMachine : Potwierdzenie synchronizacji
TicketMachine --> CentralSystem : Potwierdzenie synchronizacji
deactivate TicketMachine
CentralSystem --> Admin : Potwierdzenie konfiguracji
deactivate CentralSystem

@enduml
```
