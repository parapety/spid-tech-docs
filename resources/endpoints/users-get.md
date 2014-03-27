:introduction

List users. All query parameters are user properties that will be used to search
for users. When sending multiple query parameters, the API performs an `AND`
search. Some parameters are used to fuzzy match, while others perform exact
matches. See the parameter list for details on which does what.

All regular expression queries use
[Pearl Compatible Regular Expression](http://en.wikipedia.org/wiki/Perl_Compatible_Regular_Expressions)
syntax, as implemented in
[PHP](http://www.php.net/manual/en/reference.pcre.pattern.syntax.php) and other
places.

## Search examples

Get name, userId, email and gender from users where familyName starts with
"Olsen" and gender is male, limit to 10 users:

```sh
curl http://stage.payment.schibsted.no/api/2/users?oauth_token=TOKEN& \
  limit=10& \
  offset=0& \
  familyName=Olsen& \
  gender=male& \
  fields=name,userId,email,gender
```

Get the whole user object from users where email matches exactly
"daniel.bentes@vg.no":

```sh
curl http://stage.payment.schibsted.no/api/2/users?oauth_token=TOKEN& \
  email=daniel.bentes@vg.no
```

Get all users that where registered between 2011-01-20 (timestamp 1295478000)
and 2011-01-21:

```sh
curl http://stage.payment.schibsted.no/api/2/users?oauth_token=TOKEN& \
  since=1295478000& \
  until=2011-01-21
```

Get all users that where registered between yesterday and now:

```sh
curl http://stage.payment.schibsted.no/api/2/users?oauth_token=TOKEN& \
  since=yesterday& \
  until=now
```

## Filters

The endpoint supports many filters (see below). If no filters are provided,
active users for the client is returned. Users with status 0 and 1 are
considered active.