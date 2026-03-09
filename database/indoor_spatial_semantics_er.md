```mermaid
erDiagram
    buildings ||--o{ floors : contains
    floors ||--o{ partitions : contains

    partitions ||--o{ partition_doors : has
    doors ||--o{ partition_doors : belongs_to

    partitions ||--o{ door_distances : contains
    doors ||--o{ door_distances : from
    doors ||--o{ door_distances : to

    partitions ||--o{ pois : contains

    buildings {
        int id PK
        varchar name
        text address
    }

    floors {
        int id PK
        int building_id FK
        int level "0=ground"
        varchar name
    }

    partitions {
        int id PK
        int floor_id FK
        enum type "room, hallway, staircase"
    }

    doors {
        int id PK
    }

    partition_doors {
        int door_id FK
        int partition_id FK
    }

    door_distances {
        int partition_id FK
        int from_door_id FK
        int to_door_id FK
        float distance
    }

    pois {
        int id PK
        int partition_id FK
        varchar name
        varchar category
    }
```
