### Associations:

1) **TO-ONE:** 
    
    - association between *Books* and *Authors* is defined through the `author` element in the *Books* entity.
    
    - this `author` element creates a link to the *Authors* entity, which established a relationship where you can navigate from *Books* entity to associated `author` *(to retrieve more details)*.

    ```
    entity Books {
        key ID: UUID;
            author: Association to Authors;
            ...
    }
    ```
    ```
    entity Authors {
        key ID: UUID;
            ...
    }
    ```

    * in this example above the **TO-ONE** association `Books:author` is so-called *MANAGED association*, where **FK** and `ON` conditions are added automatically *(behind the scene)*.

2) **TO-MANY:**
    
    - `author` can write any number of *books*, so `author` can be associated with **none, one or any number of books*.

    ```
    entity Authors {
        key ID: UUID;
            books: Association to many Books 
                        on books.author = $self;   // $self - a placeholder that refers to the current entity
    }
    ```

3) **MANY-TO-MANY:**

    - CDS does not currently provide any special support for *MANY-TO-MANY* associations, thus we must resolve it into *TWO ONE-TO-MANY associations* using a 'link entity' *(to connect the two)*.

### Composition 
*means that the child entity **(e.g. Order Items)** cannot exist independently of the parent entity **(Order)**:*

    ```
    entity Orders {
        ...
        items: Composition of many OrderItems
                    on items.order = $self;
    }
    ```
    ```
    entity OrderItems {
        key order: Association to Orders;
            ...
    }
    ```

* The child is contained in a parent, and can only be accessed via the parent.

* Features in comparison to association (aggregation):
    1. Cascaded delete *- the deletion of the order would also result in the deletion of all order items;*
    2. Deep Insert *- in the generated OData Service, both Order and OrderItems can be created via single POST request.*

### 'extend' directive 
*allows us to add extension fields to existing definitions:*

    ```
    entity Authors { ... };
    ```
    ```
    extend Authors with {
        someNewField: String;
    }
    ```

* *extend can also be used to set a new type of existing fields.*

### 'aspect' 
*can be applied to multiple targets with 'extend':*

    ```
    aspect ManagedObject {
        createdAt: Timestamp;
        createdBy: String(255);
    };

    extend Books with ManagedObject;
    extend Authors with ManagedObject;
    ```

* can also be used with inheritance-like syntax;
* using {cuid, managed} from '@sap/cds/common';

### 'localized' modifier 
*is used to declare localized fields `title: localized String(255);`*