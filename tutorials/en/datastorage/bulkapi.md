#####In this section

In this section you'll learn about how to save and delete more than one CloudObject at a Time. You'll learn about the Bulk API for Save and Delete in CloudBoost.

#Saving Multiple CloudObjects

To save multiple CloudObjects, you need to pass an array of CloudObjects to the bulk save function. Here's a quick example:

==JavaScript==
<span class="js-lines" data-query="bulksave">
```
var obj1 = new CB.CloudObject('Custom');
obj1.set('name','abcd');
var obj2 = new CB.CloudObject('Custom');
obj2.set('name','pqrs');
CB.CloudObject.saveAll([obj1,obj2],{
    success: function(res){
        //res has the array of saved CloudObjects.
    },error: function(err){
        // if there is an error, then err will be an array fo error messages respective to the array of CloudObjects
});
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="bulksave">
```
var obj1 = new CB.CloudObject('Custom');
obj1.set('name','abcd');
var obj2 = new CB.CloudObject('Custom');
obj2.set('name','pqrs');
CB.CloudObject.saveAll([obj1,obj2],{
    success: function(res){
        //res has the array of saved CloudObjects.
    },error: function(err){
        // if there is an error, then err will be an array fo error messages respective to the array of CloudObjects
});
```
</span>

==cURL==
<span class="curl-lines" data-query="bulksave">
```
curl -X PUT --header 'Content-Type: application/json' --header 'Accept: application/json' -d '{
  "key": ${client_key},
    "document": [{
        "_type": "custom",
        "expires": null,
        "name": "egima",
        "_modifiedColumns": ["createdAt",
        "updatedAt",
        "ACL",
        "expires",
        "name"],
        "_tableName": "data",
        "ACL": {
            "write": {
                "allow": {
                    "role": [],
                    "user": ["all"]
                },
                "deny": {
                    "role": [],
                    "user": []
                }
            },
            "read": {
                "allow": {
                    "role": [],
                    "user": ["all"]
                },
                "deny": {
                    "role": [],
                    "user": []
                }
            }
        },
        "_isModified": true
    },
    {
        "_type": "custom",
        "expires": null,
        "name": "bengi",
        "_modifiedColumns": ["createdAt",
        "updatedAt",
        "ACL",
        "expires",
        "name"],
        "_tableName": "data",
        "ACL": {
            "write": {
                "allow": {
                    "role": [],
                    "user": ["all"]
                },
                "deny": {
                    "role": [],
                    "user": []
                }
            },
            "read": {
                "allow": {
                    "role": [],
                    "user": ["all"]
                },
                "deny": {
                    "role": [],
                    "user": []
                }
            }
        },
        "_isModified": true
    }]
}' 'http://api.cloudboost.io/data/${app_id}/${table_name}'
```
</span>

#Deleting Multiple CloudObjects

To delete multiple objects pass an array of CloudObjects to the bulk delete function. For example:

==JavaScript==
<span class="js-lines" data-query="bulkdelete">
```
CB.CloudObject.deleteAll([obj1,obj2],{
    success: function(res){
        //successfully delete CloudObjects.
    },error: function(err){
        // error while deleting CloudObjects. err is an array of error objects.
    });
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="bulkdelete">
```
CB.CloudObject.deleteAll([obj1,obj2],{
    success: function(res){
        //successfully delete CloudObjects.
    },error: function(err){
        // error while deleting CloudObjects. err is an array of error objects.
    });
```
</span>

==cURL==
<span class="curl-lines" data-query="bulkdelete">
```
curl -X PUT --header 'Content-Type: application/json' --header 'Accept: application/json' -d '{
  "key": ${client_key},
  "method":"DELETE",
    "document": [{
        "updatedAt": "2016-03-16T13:28:20.936Z",
        "_type": "custom",
        "_version": 0,
        "expires": null,
        "_id": "LYm3d7Bh",
        "createdAt": "2016-03-16T13:28:20.936Z",
        "name": "egima",
        "_tableName": "data",
        "ACL": {
            "write": {
                "allow": {
                    "role": [],
                    "user": ["all"]
                },
                "deny": {
                    "role": [],
                    "user": []
                }
            },
            "read": {
                "allow": {
                    "role": [],
                    "user": ["all"]
                },
                "deny": {
                    "role": [],
                    "user": []
                }
            }
        }
    },
    {
        "updatedAt": "2016-03-16T13:28:20.938Z",
        "_type": "custom",
        "_version": 0,
        "expires": null,
        "_id": "dJ6mwXom",
        "createdAt": "2016-03-16T13:28:20.938Z",
        "name": "bengi",
        "_tableName": "data",
        "ACL": {
            "write": {
                "allow": {
                    "role": [],
                    "user": ["all"]
                },
                "deny": {
                    "role": [],
                    "user": []
                }
            },
            "read": {
                "allow": {
                    "role": [],
                    "user": ["all"]
                },
                "deny": {
                    "role": [],
                    "user": []
                }
            }
        }
    }]
}' 'http://api.cloudboost.io/data/${app_id}/${table_name}'
```
</span>


