```mermaid
erDiagram
    direction LR

    subgraph "Brugere & Rettigheder"
        ROLE {
            int Id PK
            string Role_Name
        }
        PERMISSION {
            int Id PK
            string Permission_Name
            string Description
        }
        ROLE_PERMISSION {
            int Role_Id FK
            int Permission_Id FK
        }
        EMPLOYEE {
            int Id PK
            string First_Name
            string Last_Name
            string Student_Mail
            string Mail
            int Role_Id FK
        }
    end

    subgraph "Lager & Genstande"
        MODEL {
            int Id PK
            string Model_Name
            string Brand
        }
        ITEM_STATUS {
            int Id PK
            string Status_Name
        }
        WAREHOUSE {
            int Id PK
            string Location_Name
        }
        ITEM {
            int Id PK
            int Model_Id FK
            int Warehouse_Id FK
            int Status_Id FK
        }
        SERIAL {
            int Id PK
            int Item_Id FK
            string Serial_No
        }
    end

    subgraph "Udlån & Historik"
        LENT_OUT {
            int Id PK
            int Item_Id FK
            int Borrower_Employee_Id FK
            int Responsible_Employee_Id FK
            datetime Lent_Date
            datetime Expected_Return_Date
            datetime Actual_Return_Date
            string Description
        }
        HISTORY {
            int Id PK
            int Item_Id FK
            int Employee_Id FK
            datetime Log_Date
            string Action_Type
            string Field_Name
            string Before_Value
            string After_Value
        }
    end

    subgraph "Gaver"
        ITEM_GIFTS {
            int Id PK
            string Gift_Name
            string Gift_Description
        }
        GIFTS {
            int Id PK
            int Employee_Id FK
            int Item_Gift_Id FK
            int Given_By_Employee_Id FK
            datetime Given_Date
            string Free_Text
        }
    end

    %% Relationer: Brugere & Rettigheder
    ROLE o|--|{ EMPLOYEE : "tildeles"
    ROLE o|--|{ ROLE_PERMISSION : "indeholder"
    PERMISSION o|--|{ ROLE_PERMISSION : "tilknyttes"

    %% Relationer: Lager & Genstande
    MODEL o|--|{ ITEM : "definerer"
    ITEM_STATUS o|--o{ ITEM : "angiver_tilstand"
    WAREHOUSE o|--o{ ITEM : "opbevarer"
    ITEM o|--o| SERIAL : "kan_have"

    %% Relationer: Udlån & Historik
    EMPLOYEE o|--o{ LENT_OUT : "låner"
    EMPLOYEE o|--o{ LENT_OUT : "ansvarlig_for"
    EMPLOYEE o|--o{ HISTORY : "udfører"
    ITEM o|--o{ LENT_OUT : "udlånes_i"
    ITEM o|--o{ HISTORY : "logges_i"

    %% Relationer: Gaver
    EMPLOYEE o|--o{ GIFTS : "modtager"
    EMPLOYEE o|--o{ GIFTS : "udleverer"
    ITEM_GIFTS o|--o{ GIFTS : "tildeles_i"
