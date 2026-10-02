```mermaid

erDiagram
    direction LR

    subgraph Lager ["Lager & Produkter"]
        CATEGORY {
            int id PK
            varchar category_name
        }

        WAREHOUSE {
            int id PK
            varchar location_name
        }

        MODEL {
            int id PK
            varchar model_name
            int category_id FK
        }

        ITEM {
            int id PK
            int warehouse_id FK
            varchar status
            varchar serial
            varchar name
            varchar model_name
            int category_id FK
        }
    end

    subgraph Bruger ["Bruger & Sikkerhed"]
        EMPLOYEE {
            int id PK
            varchar first_name
            varchar last_name
            varchar mail
            int role_id FK
        }

        ROLE {
            int id PK
            varchar role_name
        }

        PERMISSION {
            int id PK
            varchar permission_name
            varchar description
        }

        ROLE_PERMISSION {
            int role_id PK, FK
            int permission_id PK, FK
        }
    end

    subgraph Udlan ["Udlånssystem"]
        LOAN {
            int id PK
            int employee_id FK
            datetime loan_date
            datetime expected_return_date
            datetime actual_return_date
        }
    end

    CATEGORY ||--|{ ITEM : "kategoriserer"
    CATEGORY ||--|{ MODEL : "indeholder"
    WAREHOUSE ||--|{ ITEM : "huser"
    ROLE ||--|{ EMPLOYEE : "har"
    ROLE ||--|{ ROLE_PERMISSION : "tildeles"
    PERMISSION ||--|{ ROLE_PERMISSION : "tilknyttes"
    EMPLOYEE ||--|{ LOAN : "foretager"
    ITEM ||--|| LOAN : ""
