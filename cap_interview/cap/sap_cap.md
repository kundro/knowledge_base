
# SAP CAP
*is a framework provided by SAP for building enterprise services and applications on the SAP BTP.*

**CDS** - is a modeling language which helps to define Domain Models and Service Definitions.
*CDS Models are represented in CSN (Core Schema Notation)*

**DB** *- SAP HANA, SQLite, PostgreSQL*
**UI** *- SAP Fiori, free SAPUI5, Vue, React*

- **Domain Entities** - are structured types with named and typed elements representing data sets, that can be read and manipulated using usual CRUD.
  *(db folder .cds)* 

    * *when translated into persistense models - entities become tables;*
    * *plural + capital letter;*

    ```
    define entity Authors {
        key ID: UUID;
            name: String(100);
            dateOfBirth: Date;
    };

    define type NoOfBooks: Integer;

    type Price {
        amount: Decimal;
        currency: String(3);
    };

    type Genre: Integer enum {
        fiction = 1;
        non_fiction = 2;
    };
    ```
    
- **Service Models** -> we can write a Service Definition with CDS and CQL (CDS Query Language):
  *(srv folder .cds)*

    ```
    service AdminService @(path:'/admin') {
        entity Books as projection on db.Books;      // we can also use 'as select from' instead of 'as projection on'
        entity Authors as projection on db.Authors;
    }
    ```

    * the `AdminService` above serves as a fully implemented **OData V4 service**.
    * `using` directive helps to import the definitions from domain model.

-----------------------------------------------------------------------------------------------------------------------------

### .CSV files
*we can populate the DB tables created for CAP app with **initial data**.*

* `.csv` file name should fully match with the corresponding namespace and entity definition name *(e.g. `cap.sap.learning-Authors.csv`).*
* we can create `.csv` files in the `test/data` or `db/data` - to distinguish between *sample data* and real *initial data*.