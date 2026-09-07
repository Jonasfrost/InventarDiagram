```mermaid
erDiagram
    EMPLOYEE {
        string Person_ID PK
        string First_name
        string Last_name
        string Student_mail
        string mail
        string Role_ID_FK
        string Instructor_ID
    }
    ROLE {
        string Role_ID PK
        string Leader
        string Instructor
        string Apprentice
        string Operations
    }
    ITEM {
        string Item_ID PK
        string Name
        string Model
        string Serial_No
    }
    WAREHOUSE {
        string Item_ID_FK
        string Quantity_serial_no
        string Location
    }
    LENT_OUT {
        string Item_ID_FK
        string Person_ID_FK
        string Lent_date
        string Return_ID_FK
        string Delivery_date
        string Responsible
        string Serial_no
        string Description
    }
    ITEM_GIFTS {
        string Name
        string ID
        string Desc
    }
    GIFTS {
        string ID_In_Gifts
        string ID_Person
        string Free_text
    }
    HISTORY {
        string ID_PK
        string Login_ID
        string Before_correction
        string After_correction
        string Item_ID
        string Date
    }

    EMPLOYEE ||--o{ LENT_OUT : "borrows"
    ROLE ||--o{ EMPLOYEE : "has"
    ITEM ||--o{ WAREHOUSE : "located_in"
    ITEM ||--o{ LENT_OUT : "included_in"
    ITEM_GIFTS ||--o{ GIFTS : "has"
    HISTORY ||--o{ ITEM : "includes"
    HISTORY ||--o{ EMPLOYEE : "includes"
    
    
    
