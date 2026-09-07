erDiagram
    Role {
        int Role_ID PK
        string Leader
        string Instructor
        string Apprentice
        string Drift
    }
    Employee {
        int Person_ID PK
        string First_name
        string Last_name
        string Student_mail
        string mail
        int Role_ID FK
    }
    Warehouse {
        int Warehouse_ID PK
        string Location
    }
    Serial_No {
        int Serial_No_ID PK
        string Serial_no
    }
    Item {
        int Item_ID PK
        string Item_Name
        string Model
        string Serial_No
        string Location
    }
    Lent_Out {
        int Lent_ID PK
        int Item_ID FK
        int Person_ID FK
        string Lent_date
        int Return_ID
        string Return_date
        string Responsible
        string Serial_no
        string Lent_Description
    }
    Item_Gifts {
        int Gift_ID PK
        string Gift_Name
        string Gift_Description
    }
    Gifts {
        int ID_In_Gifts PK
        int ID_Person FK
        string Free_text
    }
    History {
        int History_ID PK
        int Person_ID FK
        string Before_correction
        string After_correction
        int Item_ID FK
        string Correction_Date
    }

    Role ||--o{ Employee : "has"
    Employee ||--o{ Lent_Out : "borrows"
    Item ||--o{ Lent_Out : "included_in"
    Employee ||--o{ Gifts : "has"
    Employee ||--o{ History : "includes"
    Item ||--o{ History : "includes"
