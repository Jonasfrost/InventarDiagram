```mermaid
erDiagram
    EMPLOYEE {
        int Person_ID PK
        string First_name
        string Last_name
        string Student_mail
        string mail
        int Role_ID FK
        int Instructor_ID
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
        string Name
        string Model
        string Serial_No
        string Location
    }
    WAREHOUSE {
        int Warehouse_ID PK
        string Location
    }
   SERIAL_No{
        int Serial_No_ID PK
        int Serial_no
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
        string Name
        string Gift_Description
    }
    GIFTS {
        int ID_In_Gifts PK
        int ID_Person FK
        string Free_text
    }
    HISTORY {
        int History_ID_PK
        int Person_ID
        string Before_correction
        string After_correction
        int Item_ID
        string Correction_Date
    }

    EMPLOYEE ||--o{ LENT_OUT : "borrows"
    ROLE ||--o{ EMPLOYEE : "has"
    ITEM ||--o{ WAREHOUSE : "located_in"
    ITEM ||--o{ LENT_OUT : "included_in"
    SERIAL_No ||--o{ ITEM : "has"
    HISTORY ||--o{ ITEM : "includes"
    HISTORY ||--o{ EMPLOYEE : "includes"
    ITEM_GIFTS ||--o{ WAREHOUSE : "located_in"
    ITEM_GIFTS ||--o{ GIFTS : "has"
    GIFTS ||--o{ EMPLOYEE : "man idk"
    
    
    
