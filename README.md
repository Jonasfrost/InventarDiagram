```mermaid
erDiagram
    EMPLOYEE {
        int Person_ID PK
        string First_name
        string Last_name
        string Student_mail
        string mail
        int Role_ID_FK
        int Instructor_ID
    }
    ROLE {
        int Role_ID PK
        string Leader
        string Instructor
        string Apprentice
        string Operations
    }
    ITEM {
        int Item_ID PK
        string Name
        string Model
        string Serial_No
    }
    WAREHOUSE {
        int Item_ID_FK
        string Quantity_serial_no
        string Location
    }
   SERIAL_No{
        int Serial_No_ID
        int Serial_no
    }
    LENT_OUT {
        int Item_ID_FK
        int Person_ID_FK
        string Lent_date
        int Return_ID_FK
        string Delivery_date
        string Responsible
        string Serial_no
        string Description
    }
    ITEM_GIFTS {
        int ID
        string Name
        string Desc
    }
    GIFTS {
        int ID_In_Gifts
        int ID_Person
        string Free_text
    }
    HISTORY {
        int ID_PK
        int Login_ID
        string Before_correction
        string After_correction
        int Item_ID
        string Date
    }

    EMPLOYEE ||--o{ LENT_OUT : "borrows"
    ROLE ||--o{ EMPLOYEE : "has"
    ITEM ||--o{ WAREHOUSE : "located_in"
    ITEM ||--o{ LENT_OUT : "included_in"
    SERIAL_No ||--o{ ITEM : "has"
    ITEM_GIFTS ||--o{ GIFTS : "has"
    HISTORY ||--o{ ITEM : "includes"
    HISTORY ||--o{ EMPLOYEE : "includes"
    ITEM_GIFTS ||--o{ WAREHOUSE : "located_in"
    
    
