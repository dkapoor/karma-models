## leakedSource-for-karma.jl

### PyTransforms
#### _username_sha1_
From column: _json_rep / data / username_
``` python
return SM.sha1_hash(getValue("username"))
```

#### _password_sha1_
From column: _json_rep / data / Real_Password_
``` python
return SM.sha1_hash(getValue("Real_Password"))
```

#### _email_domain_
From column: _json_rep / data / email_
``` python
return getValue("email").split("@")[1]
```

#### _email_name_sha1_
From column: _json_rep / data / email_
``` python
return SM.sha1_hash(getValue("email").split("@")[0])
```

#### _cdr_id_
From column: __id_
``` python
return getValue("_id")
```

#### _leaked_date_iso_
From column: _json_rep / leaked_
``` python
t =   getValue("leaked")
return DM.iso8601date(t,"%Y-%d-%m %H:%M:%S")
```

#### _login_credentials_uri_
From column: _json_rep / data / email_name_sha1_
``` python
return SM.sha1_hash(getValue("email").split("@")[0])
```

#### _exploit_uri_
From column: _json_rep / data / email_name_sha1_
``` python
return "exploit/"+ getValue("database").split('.')[0].lower()+"/"+SM.sha1_hash(getValue("email").split("@")[0])
```

#### _email_uri_
From column: _json_rep / data / email_domain_
``` python
x = getValue("email_name_sha1")
if len(x) > 0:
  return UM.uri_from_fields("email/",getValue("email_domain")) + "/" + x
return ''
```

#### _password_uri_
From column: _json_rep / data / password_sha1_
``` python
email_uri = getValue("email_uri")
if len(email_uri) > 0:
  return email_uri + "/password"
return ''
```

#### _database_uri_
From column: _json_rep / database_
``` python
return UM.uri_from_fields("organization/", getValue("database"))
```

#### _username_uri_
From column: _json_rep / data / username_sha1_
``` python
x = getValue("username_sha1")
if len(x) > 0:
   return UM.uri_from_fields("username/", getValue("email_domain")) + "/" + x
return ''
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _cdr_id_ | `schema:source` | `memex:Exploit1`|
| _database_ | `schema:name` | `schema:Organization1`|
| _database_uri_ | `uri` | `schema:Organization1`|
| _email_domain_ | `memex:domainName` | `memex:EmailAddress1`|
| _email_name_sha1_ | `memex:nameSHA1` | `memex:EmailAddress1`|
| _email_uri_ | `uri` | `memex:EmailAddress1`|
| _exploit_uri_ | `uri` | `memex:Exploit1`|
| _leaked_date_iso_ | `schema:datePublished` | `memex:Exploit1`|
| _login_credentials_uri_ | `uri` | `memex:LoginCredentials1`|
| _password_sha1_ | `memex:nameSHA1` | `memex:Password1`|
| _password_uri_ | `uri` | `memex:Password1`|
| _source_name_ | `schema:publisher` | `memex:Exploit1`|
| _username_sha1_ | `memex:nameSHA1` | `memex:UserName1`|
| _username_uri_ | `uri` | `memex:UserName1`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Exploit1` | `memex:itemStolen` | `memex:LoginCredentials1`|
| `memex:LoginCredentials1` | `memex:password` | `memex:Password1`|
| `memex:LoginCredentials1` | `memex:username` | `memex:UserName1`|
| `memex:LoginCredentials1` | `schema:email` | `memex:EmailAddress1`|
| `memex:LoginCredentials1` | `memex:isLoginCredentialFor` | `schema:Organization1`|
| `schema:Organization1` | `memex:hasLoginCredentials` | `memex:LoginCredentials1`|
