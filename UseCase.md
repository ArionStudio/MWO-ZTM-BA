@startuml

left to right direction

actor Użytkownik as User

package "Przypadki użycia użytkownika" {
    usecase "Wybór biletu" as UC1
    usecase "Zakup biletu" as UC2
}

User --> UC1
UC1 --> UC2 : <<invoke>>

@enduml
