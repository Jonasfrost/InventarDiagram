```mermaid
erDiagram
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

    LOAN {
        int id PK
        int employee_id FK
        datetime loan_date
        datetime expected_return_date
        datetime actual_return_date
    }

    LOAN_ITEM {
        int loan_id PK, FK
        int item_id PK, FK
    }

    CATEGORY ||--o{ ITEM : "kategoriserer"
    CATEGORY ||--o{ MODEL : "indeholder"
    WAREHOUSE ||--o{ ITEM : "huser"
    ROLE ||--o{ EMPLOYEE : "har"
    ROLE ||--o{ ROLE_PERMISSION : "tildeles"
    PERMISSION ||--o{ ROLE_PERMISSION : "tilknyttes"
    EMPLOYEE ||--o{ LOAN : "foretager"
    LOAN ||--|{ LOAN_ITEM : "omfatter"
    ITEM ||--o{ LOAN_ITEM : "udlånes_i"
