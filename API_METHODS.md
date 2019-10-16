
**ManageIQ API Implementation Methods:**

- GET
  - /collection
    - action: **read**
    - method: index
    - methods:
       - index (base_controller.rb)
       - index (collection controller)
  - /collection/:id
    - action: **read**
    - method: show
    - methods:
      - show (base_controller.rb)
      - show (collection controller)
- POST (no actions specified)
  - /collection
    - action: **create**
    - method: create
    - methods
      - create (base_controller.rb)
      - create_resource (collection controller)
- POST (**\<action\>** specified)
  - /collection
    - action: **\<action\>**
    - method: update
    - methods:
      - update (base_controller.rb)
      - update_collection (manager.rb)
      - **\<action\>**_collection (collection controller) - for Collection action
      - **\<action\>**_resource (collection controller) - for Bulk action
  - /collection/:id
    - action: **\<action\>**
    - method: update
    - methods:
      - update (base_controller.rb)
      - update_collection (manager.rb)
      - **\<action\>**_resource  (collection controller)
- PUT
  - /collection/:id
    - action: **edit**
    - method: update
    - methods:
      - update (base_controller.rb)
      - update_collection (manager.rb)
      - put_resource (manager.rb)
      - edit_resource (generic.rb)
      - edit_resource (collection controller)
- PATCH
  - /collection/:id
    - action: **edit**
    - method: update
    - methods:
      - update (base_controller.rb)
      - update_collection (manager.rb)
      - patch_resource (manager.rb)
      - edit_resource (generic.rb)
      - edit_resource (collection controller)
- DELETE
  - /collection/:id
    - action: **delete**
    - method: destroy
    - methods:
      - destroy (base_controller.rb)
      - delete_resource (generic.rb)
      - delete_resource (collection controller)
- OPTIONS
  - /collection
    - action: **options**
    - method: options
    - methods:
      - options (base_controller.rb)
      - options (collection controller)


Method Name Constructs:

| Method Name | Description |
| ----------- | ----------- |
| **\<action\>**_resource(type, id, data)       | Implementation of \<action\> on the collection for individual resource or bulk operations |
| **\<action\>**_collection(type, data)         | Implementation of \<action\> on the collection |
| **\<sub_collection\>**_query_resource(object) | Methods that query the \<sub_collection\> for a given resource |
| find_**\<collection\>**(id)                   | When a class find for a collection class id is not sufficient and additional constraints or alternate methods are needed to fetch a resource by id |
| **\<collection\>**_search_conditions          | Optional scope needed for the Collection when doing a collection search (GET /api/\<collection\> that triggers the index method) |

**Note:** The \<action\>_resource signature above is for all actions, create, edit, delete (these being provided by the base controller), as well as the additional actions declared for the collection controller.
