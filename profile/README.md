# HealthHubert
Tablet dispenser system made in cooperation with Technical University of Denmark

```mermaid
graph TD
    subgraph backend[Backend]
        db[(PostgreSQL database)]
        broker[(Mosquitto MQTT broker)]

        subgraph fast[FastAPI]
            fastapi[fastapi]
            fastapi-mqtt[fastapi-mqtt]
        end

    end


    subgraph hardware[Hardware]
        dispenser[Dispensing mechanism]
        pi[Raspberry Pi]
    end

    subgraph frontend[Frontend]
        flutter[Flutter]
    end

    

    fastapi-mqtt <--> broker
    db <--> |SQL| fastapi-mqtt
    db <--> |SQL| fastapi

    flutter <--> |HTTPS| fastapi

    pi --> |GPIO| dispenser
    
    pi <--> |MQTT| broker
    pi <--> |HTTPS| fastapi
```

## DTU Courses involving development of HealthHubert
- 34315 IoT (Spring 2024):         Internet of things - application and infrastructure implementation
- Special course (Autumn 2024):    Rethinking medication management: Advanced design and usability of an IoT-integrated system 
- Special course (Spring 2025):    Forbedring af brugervenlighed i tablet dispenser design

## Authors
- Lars Dobrowohl
- Jacob Bonvang
- Juno Ngo
- Peter Bonvang
- Thomas Hegelund
- Vanda Nováková
