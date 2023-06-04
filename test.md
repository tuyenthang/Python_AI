````plantuml

@startuml

actor User

User -> Main.py: Execute

activate Main.py

Main.py -> BcpControl: run()

activate BcpControl

BcpControl -> BcpControl: __init__()

BcpControl -> Main.py: Read schema.json

activate Main.py

Main.py -> JSONFile: Open schema.json

activate JSONFile

JSONFile --> Main.py: File handle

Main.py -> JSONFile: Load JSON data

activate JSONFile

JSONFile --> Main.py: JSON data

deactivate JSONFile
deactivate Main.py

BcpControl -> BcpControl: on_execute()

BcpControl -> scol: run()

activate scol

scol -> BcpControl: Pass BcpControl object

activate BcpControl

BcpControl --> scol: Execution Result

deactivate BcpControl
deactivate scol

BcpControl -> BcpControl: save_variables()

deactivate BcpControl

Main.py --> User: Execution Result

deactivate Main.py

@enduml

