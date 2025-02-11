# Annotations
### CAP supports server-side input validations via annotations.

- **@mandatory** *- checks for non-empty input (null or trimmed);*
- **@readonly** *- as well as calculated elements are protected against write operations;*
- **@assert.format** *- allows to specify a regular expression string, that all string input must match;* 
`// @assert.format: '[a-z]ear -> Regex Pattern;`
- **@assert.range** *- allows to specify [min,max] ranges for elements with ordinal types (numeric/date/time)* 
`// for enum elements -> TRUE can be used to restrict all input only with the defined values of enum;`
- **@assert.notNull: true/false**
- **@assert.target** *- can be used for managed TO-ONE association to check if during CREATE/UPDATE operations the target entity, to which the association refers - exists.*
    * in another words - use this to ensure that a non-null FK in a table has a corresponding PK in the target table.

----------------------------------------------------------------------------------

### Concurrency Control ('одновременный / параллельный') 
    
**Concurrency control is used to ensure data integrity when concurrent modifications are executed simultaneously.**

 - **Optimistic locking**:
    - ETags (Entity Tags) - *to enable ETags for a model entity we should add **@odata.tag** annotation to an element.*
    * `annotate` directive is used for it:
    
        ```
        entity Authors:suid, managed 
            {
                ...
            };
        ```

        ```
        annotate Authors with {
                modifiedAt @odata.etag
            };
        ```

 - **Pessimistic locking**:
    - through transactions. 
    - lock data so that other transactions are blocked from changing the data.

-----------------------------------------------------------------------------------

### Service (Expose Denormolized Views):
    
    service CatalogService @(path:'/cat') {
        entity Authors as projection on db.Authors {
            *,
            epoch.name as period    // 'path expressions'
        } excluding {
            createdAt,
            createdBy
        };
    };

------------------------------------------------------------------------------------

### Service Handling (Custom Event Handlers):

- `before` and `after` event handlers just defined in **srv layer** using:

    ```
    class TestService extends cds.ApplicationService {
        
        // redefine init method
        async init() {
            this.before/after(['CREATE','UPDATE'], this.entities.Authors, Handler.onMethod);

            return await super.init();
        }
    }
    ```

- SAP recomends prefering *UNBOUND actions/functions*, as there are simplier implementation and invoke:
    
    1. Declare action in DB layer in `Service.cds`:
        
        `action ChangeStatus(param: Type) returns {test: Type};`

    2. Add event in SRV layer in `Service.js`:

        `this.on('ChangeStatus', Handler.onChangeStatus);`

        * **Action** - always POST request, which always modifies data and NOT always returns data. _*Consider it like a Button*_
        * **Function** - always GET request, which do not change data and always returns data (e.g. get number of active users). _*Consider it like a calculator*_

        * **Bound** - connected to a specific entity;
        * **Unbound** - Not linked to a specific entity;