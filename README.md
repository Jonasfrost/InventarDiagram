```mermaid
erDiagram
    ROLE {
        int Id PK
        string Role_Name
    }

    EMPLOYEE {
        int Id PK
        string First_Name
        string Last_Name
        string Student_Mail
        string Mail
        int Role_Id FK
    }

    MODEL {
        int Id PK
        string Model_Name
        string Brand
    }

    SERIAL {
        int Id PK
        string Serial_No
        string Item_Name
        int Model_Id FK
    }

    WAREHOUSE {
        int Id PK
        string Location_Name
    }

    ITEM {
        int Id PK
        int Serial_Id FK
        int Warehouse_Id FK
        string Status
    }

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

    ITEM_GIFTS {
        int Id PK
        string Gift_Name
        string Gift_Description
    }

    GIFTS {
        int Id PK
        int Employee_Id FK
        int Item_Gift_Id FK
        string Free_Text
        datetime Given_Date
    }

    ROLE ||--|{ EMPLOYEE : "har"
    EMPLOYEE ||--|{ LENT_OUT : "låner"
    EMPLOYEE ||--|{ LENT_OUT : "ansvarlig_for"
    EMPLOYEE ||--|{ HISTORY : "udfører"
    EMPLOYEE ||--|{ GIFTS : "modtager"

    MODEL ||--|{ SERIAL : "definerer"
    SERIAL ||--|{ ITEM : "tilhører"
    WAREHOUSE ||--|{ ITEM : "opbevarer"
    ITEM ||--|{ LENT_OUT : "udlånes_i"
    ITEM ||--|{ HISTORY : "logges_i"

    ITEM_GIFTS ||--|{ GIFTS : "tildeles_i"
