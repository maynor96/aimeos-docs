
# decorators
## excludes

Excludes decorators added by the "common" option from the JSON API clients

```
client/jsonapi/review/decorators/excludes = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2020.10

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to remove a decorator added via
"client/jsonapi/common/decorators/default" before they are wrapped
around the JsonApi client.

```
 client/jsonapi/decorators/excludes = array( 'decorator1' )
```

This would remove the decorator named "decorator1" from the list of
common decorators ("\Aimeos\Client\JsonApi\Common\Decorator\*") added via
"client/jsonapi/common/decorators/default" for the JSON API client.

See also:

* client/jsonapi/common/decorators/default
* client/jsonapi/review/decorators/global
* client/jsonapi/review/decorators/local

## global

Adds a list of globally available decorators only to the JsonApi client

```
client/jsonapi/review/decorators/global = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2020.10

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap global decorators
("\Aimeos\Client\JsonApi\Common\Decorator\*") around the JsonApi
client.

```
 client/jsonapi/review/decorators/global = array( 'decorator1' )
```

This would add the decorator named "decorator1" defined by
"\Aimeos\Client\JsonApi\Common\Decorator\Decorator1" only to the
"review" JsonApi client.

See also:

* client/jsonapi/common/decorators/default
* client/jsonapi/review/decorators/excludes
* client/jsonapi/review/decorators/local

## local

Adds a list of local decorators only to the JsonApi client

```
client/jsonapi/review/decorators/local = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2020.10

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap local decorators
("\Aimeos\Client\JsonApi\Review\Decorator\*") around the JsonApi
client.

```
 client/jsonapi/review/decorators/local = array( 'decorator2' )
```

This would add the decorator named "decorator2" defined by
"\Aimeos\Client\JsonApi\Review\Decorator\Decorator2" only to the
"review" JsonApi client.

See also:

* client/jsonapi/common/decorators/default
* client/jsonapi/review/decorators/excludes
* client/jsonapi/review/decorators/global

# name

Class name of the used review client implementation

```
client/jsonapi/review/name = 
```

* Default: 
* Type: string - Last part of the class name
* Since: 2017.03

Each default JSON API client can be replace by an alternative imlementation.
To use this implementation, you have to set the last part of the class
name as configuration value so the client factory knows which class it
has to instantiate.

For example, if the name of the default class is

```
 \Aimeos\Client\JsonApi\Review\Standard
```

and you want to replace it with your own version named

```
 \Aimeos\Client\JsonApi\Review\Myreview
```

then you have to set the this configuration option:

```
 client/jsonapi/review/name = Myreview
```

The value is the last part of your own class name and it's case sensitive,
so take care that the configuration value is exactly named like the last
part of the class name.

The allowed characters of the class name are A-Z, a-z and 0-9. No other
characters are possible! You should always start the last part of the class
name with an upper case character and continue only with lower case characters
or numbers. Avoid chamel case names like "MyReview"!


# template

Relative path to the review JSON API template

```
client/jsonapi/review/template = review/standard
```

* Default: review/standard
* Type: string - Relative path to the template creating the body of the JSON API
* Since: 2017.03

The template file contains the code and processing instructions
to generate the result shown in the JSON API body. The
configuration string is the path to the template file relative
to the templates directory (usually in templates/client/jsonapi).

You can overwrite the template file configuration in extensions and
provide alternative templates. These alternative templates should be
named like the default one but with the string "standard" replaced by
an unique name. You may use the name of your project for this. If
you've implemented an alternative client class as well, "standard"
should be replaced by the name of the new class.


# template-aggregate

Relative path to the review aggregate JSON API template

```
client/jsonapi/review/template-aggregate = 
```

* Default: 
* Type: string - Relative path to the template creating the list of aggregated review counts
* Since: 2020.10

The template file contains the code and processing instructions
to generate the result shown in the JSON API body. The
configuration string is the path to the template file relative
to the templates directory (usually in templates/client/jsonapi).

You can overwrite the template file configuration in extensions and
provide alternative templates. These alternative templates should be
named like the default one but with the string "standard" replaced by
an unique name. You may use the name of your project for this. If
you've implemented an alternative client class as well, "standard"
should be replaced by the name of the new class.
