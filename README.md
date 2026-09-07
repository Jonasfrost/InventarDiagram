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
    INVENTORY {
        string Item_ID PK
        string Name
        string Model
    }
    WAREHOUSE {
        string Item_ID_FK
        string Quantity_serial_no
        string Location
    }
    LOCATION_LOCKER {
        string Warehouse_location
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
    SERIAL_NO {
        string Id
        string Serial_Nr
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

    ROLE ||--o{ EMPLOYEE : "has"
    INVENTORY ||--o{ WAREHOUSE : "located_in"
    INVENTORY ||--o{ LENT_OUT : "included_in"
    EMPLOYEE ||--o{ LENT_OUT : "borrows"
    
    
