```mermaid
erDiagram
    EMPLOYEE {
        int Person_ID PK
        string First_name
        string Last_name
        string Student_mail
        string mail
        int Role_ID FK
    }
    ROLE {
        int Role_ID PK
        string Leader
        string Instructor
        string Apprentice
        string Drift
    }
    ITEM {
        int Item_ID PK
        string Item_Name
        string Model
        string Serial_No FK
        string Location FK
        string Status
    }
    WAREHOUSE {
        int Warehouse_ID PK
        string Location
    }
    LENT_OUT {
        int Lent-ID PK
        int Item_ID FK
        int Person_ID FK
        string Lent_date
        int Return_ID
        string Return_date
        string Responsible
        string Serial_no FK
        string Lent_Description
    }
    ITEM_GIFTS {
        int Gift_ID PK
        string Gift_Name
        string Gift_Description
        int Location FK
    }
    GIFTS {
        int ID_In_Gifts PK
        int ID_Person FK
        string Free_text
    }
    HISTORY {
        int History_ID PK
        int Person_ID
        string Before_correction
        string After_correction
        int Item_ID FK
        string Correction_Date
    }
    SERIAL_No{
        int Serial_No_ID PK
        int Serial_no
    }
    EMPLOYEE ||--|{ LENT_OUT : ""
    EMPLOYEE ||--|| ROLE : ""
    ITEM }|--|| WAREHOUSE : ""
    ITEM ||--|| LENT_OUT : ""
    SERIAL_No ||--|| ITEM : ""
    HISTORY ||--|{ ITEM : ""
    HISTORY ||--|{ EMPLOYEE : ""
    ITEM_GIFTS ||--|{ WAREHOUSE : ""
    GIFTS ||--|| ITEM_GIFTS : ""
    GIFTS ||--|{ EMPLOYEE : ""
