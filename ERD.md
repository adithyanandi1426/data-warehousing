erDiagram

    DIM_PRODUCT {
        int product_key PK
        varchar product_id
        varchar product_name
        varchar category
        numeric unit_cost
    }

    DIM_STORE {
        int store_key PK
        varchar store_id
        varchar store_name
        varchar region
    }

    DIM_DATE {
        int date_key PK
        date full_date
        int day
        int month
        int year
        varchar weekday
    }

    FACT_INVENTORY {
        int fact_id PK
        int date_key FK
        int product_key FK
        int store_key FK
        int quantity_on_hand
        int quantity_sold
        int quantity_received
        boolean stock_out_flag
    }

    DIM_PRODUCT ||--o{ FACT_INVENTORY : "product_key"
    DIM_STORE ||--o{ FACT_INVENTORY : "store_key"
    DIM_DATE ||--o{ FACT_INVENTORY : "date_key"
