To Get My_ID and My_Secret_Key:  
Click profile dropdown (upper right hand corner)  
Click **Application** on left side bar  
Click **Developer Application** tab  
Click on registered application  


```{R}
oauth_endpoints("github")
myapp <- oauth_app("github", "My_ID", secret="My_Secret_Key")
github_token <- oauth2.0_token(oauth_endpoints("github"), myapp)
gtoken <- config(token = github_token)
req <- GET("https://api.github.com/repos/jtleek/datasharing", config(token = github_token))
stop_for_status(req)
json1 = content(req)
json1$created_at
```
