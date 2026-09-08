```mermaid
erDiagram
    EMPLOYEE {
        int Id PK
        string First_name
        string Last_name
        string Student_mail
        string mail
        int Role_ID FK
    }
    ROLE {
        int Id PK
        string Leader
        string Instructor
        string Apprentice
        string Drift
    }
    ITEM {
        int Id PK
        string Serial FK
        string WAREHOUSE_Location FK
        string Status
    }
    WAREHOUSE {
        int Id PK
        string Location
    }
    LENT_OUT {
        int Id PK
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
        int Id PK
        string Gift_Name
        string Gift_Description
        int Location FK
    }
    GIFTS {
        int Id PK
        int Employee_Id FK
        string Free_text
    }
    HISTORY {
        int Id PK
        int Employee_ID
        string Before_correction
        string After_correction
        int Item_ID FK
        string Correction_Date
    }
    SERIAL{
        int Id PK
        int Serial_no
        string Item_Name
        string Model
    }
    EMPLOYEE ||--|{ LENT_OUT : ""
    EMPLOYEE ||--|| ROLE : ""
    ITEM }|--|| WAREHOUSE : ""
    ITEM ||--|| LENT_OUT : ""
    SERIAL ||--|| ITEM : ""
    HISTORY ||--|{ ITEM : ""
    HISTORY ||--|{ EMPLOYEE : ""
    ITEM_GIFTS ||--|{ WAREHOUSE : ""
    GIFTS ||--|| ITEM_GIFTS : ""
    GIFTS ||--|{ EMPLOYEE : ""
