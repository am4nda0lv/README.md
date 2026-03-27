# README.md
Diagrama
flowchart LR
  classDef redNode fill:#D50000,color:#000000;
  classDef pinkNode fill:#E1BEE7,color:#000000;
  classDef yellowNode fill:#FFF9C4,color:#000000;
  classDef blackNode fill:#000000,stroke:#FFD600,stroke-width:4px,stroke-dasharray: 0,color:#FFFFFF;
  classDef greenNode fill:#00F840,color:#000000;
  classDef reminderNode stroke:#FFD600,stroke-width:4px,stroke-dasharray: 0,fill:#000000,color:#FFFFFF;
  classDef blueSubgraph fill:#BBDEFB;

  subgraph subgraph_zv2q8ucnp["Shape descriptions"]
      customer((Customer)):::redNode
      Support["Support"]:::pinkNode
      Technician{{Technician}}:::yellowNode
      Decision{"Decision"}:::blackNode
  end

  A((Reported issue)):::redNode --> B["Ticket is created"]
  B --> C{"Working hours?"}:::blackNode
  C -- Yes --> E{{"Tickets are sent to day team for response"}}:::yellowNode
  C -- No --> F["Tickets are sent to on-call staff for response"]:::pinkNode
  E --> Worked{"Ticket being worked on?"}:::reminderNode
  F --> Worked
  Worked -- Yes --> G["Work on the tickets based on priority"]:::pinkNode
  Worked -- No --> Reminder["Reminder is sent"]
  Reminder --> Worked
  G --> H["Team fixes the issue"]:::pinkNode
  H --> I{"Is the issue resolved?"}:::reminderNode
  I -- Yes --> Done["Ticket is closed and follow-up email is sent"]:::greenNode
  I -- No --> H

  subgraph_zv2q8ucnp:::blueSubgraph

  linkStyle 2 stroke:#00C853,fill:none
  linkStyle 3 stroke:#D50000,fill:none
  linkStyle 6 stroke:#00C853,fill:none
  linkStyle 7 stroke:#D50000,fill:none
  linkStyle 11 stroke:#00C853,fill:none
  linkStyle 12 stroke:#D50000,fill:none
