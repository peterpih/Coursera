
https://reinteractive.net/posts/188-rails-discovery-magical-routes-part-1-major-usages  

`_path` is the suffix given to automatically geenrated path names
`edit_post_path` is called the **registered helper path**  
`edit_post` is called the **named route**  

###To see all the routes
```
rake routes
bundle exec rake routes

http://localhost:3000/rails/info/routes     # only available in `development`
```
###HTTP_METHODS
```
GET
POST
PATCH
PUT
DELETE
```
