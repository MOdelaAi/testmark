graph TD;
    A(START) --> B(WAIT THREAD<br>- LIGHT<br>- RESET<br>- MQTT<br>- STREAMING)
    B -->|YES| C{config.yaml}
    C -->|NO| D(Shut down)
    D --> E(END)
    C -->|YES| F{key == current key}
    F -->|NO| D
    F -->|YES| G{wifi? and server key}
    G -->|NO| F
    G -->|YES| H(Create model per camera)
    H --> I(START THREAD<br>- LIGHT<br>- RESET<br>- MQTT<br>- STREAMING)
    I --> J(TRUE)
    J -->|NO| K(Attempted connection)
    K -->|YES| L(AI PROCESS)
    K -->|NO| J
    F -->|YES| M(UNLOCK)
    M -->|YES| N(Exit from reboot mode)
    M -->|NO| D
    D --> E
