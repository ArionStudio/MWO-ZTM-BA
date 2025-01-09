```
@startuml

left to right direction

actor Użytkownik as User
actor Administrator as Admin

package "Przypadki użycia użytkownika" {
    usecase "Wybór biletu" as UC1
    usecase "Zakup biletu" as UC2
}


package "Przypadki użycia administratora" {
    usecase "Zdalna aktualizacja oprogramowania biletomatów" as AC1
    usecase "Dostęp do raportów sprzedaży w czasie rzeczywistym" as AC2
    usecase "Konfiguracja biletów, promocji i taryf" as AC3
}

User --> UC1
UC1 --> UC2 : <<invoke>>

Admin --> AC1
Admin --> AC2
Admin --> AC3

@enduml
```
