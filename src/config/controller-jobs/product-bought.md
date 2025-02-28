
# decorators
## excludes

Excludes decorators added by the "common" option from the product bought job controller

```
controller/jobs/product/bought/decorators/excludes = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2014.03

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to remove a decorator added via
"controller/jobs/common/decorators/default" before they are wrapped
around the job controller.

```
 controller/jobs/product/bought/decorators/excludes = array( 'decorator1' )
```

This would remove the decorator named "decorator1" from the list of
common decorators ("\Aimeos\Controller\Jobs\Common\Decorator\*") added via
"controller/jobs/common/decorators/default" to the job controller.

See also:

* controller/jobs/common/decorators/default
* controller/jobs/product/bought/decorators/global
* controller/jobs/product/bought/decorators/local

## global

Adds a list of globally available decorators only to the product bought job controller

```
controller/jobs/product/bought/decorators/global = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2014.03

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap global decorators
("\Aimeos\Controller\Jobs\Common\Decorator\*") around the job controller.

```
 controller/jobs/product/bought/decorators/global = array( 'decorator1' )
```

This would add the decorator named "decorator1" defined by
"\Aimeos\Controller\Jobs\Common\Decorator\Decorator1" only to the job controller.

See also:

* controller/jobs/common/decorators/default
* controller/jobs/product/bought/decorators/excludes
* controller/jobs/product/bought/decorators/local

## local

Adds a list of local decorators only to the product bought job controller

```
controller/jobs/product/bought/decorators/local = 
```

* Default: 
* Type: array - List of decorator names
* Since: 2014.03

Decorators extend the functionality of a class by adding new aspects
(e.g. log what is currently done), executing the methods of the underlying
class only in certain conditions (e.g. only for logged in users) or
modify what is returned to the caller.

This option allows you to wrap local decorators
("\Aimeos\Controller\Jobs\Product\Bought\Decorator\*") around the job
controller.

```
 controller/jobs/product/bought/decorators/local = array( 'decorator2' )
```

This would add the decorator named "decorator2" defined by
"\Aimeos\Controller\Jobs\Product\Bought\Decorator\Decorator2"
only to the job controller.

See also:

* controller/jobs/common/decorators/default
* controller/jobs/product/bought/decorators/excludes
* controller/jobs/product/bought/decorators/global

# limit-days

Only use orders placed in the past within the configured number of days for calculating bought together products

```
controller/jobs/product/bought/limit-days = 360
```

* Default: 360
* Type: integer - Number of days
* Since: 2014.09

This option limits the orders that are evaluated for calculating the
bought together products. Only ordered products that were bought by
customers within the configured number of days are used.

Limiting the orders taken into account to the last ones increases the
quality of suggestions if customer interests shifts to new products.
If you only have a few orders per month, you can also increase this
value to several years to get enough suggestions. Please keep in mind
that the more orders are evaluated, the longer the it takes to
calculate the product combinations.

See also:

* controller/jobs/product/bought/max-items
* controller/jobs/product/bought/min-support
* controller/jobs/product/bought/min-confidence
* controller/jobs/product/bought/size

# max-items

Maximum number of suggested items per product

```
controller/jobs/product/bought/max-items = 5
```

* Default: 5
* Type: integer - Number of suggested products
* Since: 2014.09

Each product can contain zero or more suggested products based on
the used algorithm. The maximum number of items limits the quantity
of products that are associated as suggestions to one product.
Usually, you don't need more products than shown in the product
detail view as suggested products.

See also:

* controller/jobs/product/bought/min-support
* controller/jobs/product/bought/min-confidence
* controller/jobs/product/bought/limit-days
* controller/jobs/product/bought/size

# min-confidence

Minimum confidence value for high quality suggestions

```
controller/jobs/product/bought/min-confidence = 0.66
```

* Default: 0.66
* Type: float - Minimum confidence value from 0 to 1
* Since: 2014.09

The confidence value is used to remove low quality suggestions. Using
a confidence value of 0.95 would only suggest product combinations
that are almost always bought together. Contrary, a value of 0.1 would
yield a lot of combinations that are bought together only in very rare
cases.

To get good product suggestions, the value should be at least above
0.5 and the higher the value, the better the suggestions. You can
either increase the default value to get better suggestions or lower
the value to get more suggestions per product if you have only a few
ones in total.

See also:

* controller/jobs/product/bought/max-items
* controller/jobs/product/bought/min-support
* controller/jobs/product/bought/limit-days
* controller/jobs/product/bought/size

# min-support

Minimum support value to sort out all irrelevant combinations

```
controller/jobs/product/bought/min-support = 0.02
```

* Default: 0.02
* Type: float - Minimum support value from 0 to 1
* Since: 2014.09

A minimum support value of 0.02 requires the combination of two
products to be in at least 2% of all orders to be considered relevant
enough as product suggestion.

You can tune this value for your needs, e.g. if you sell several
thousands different products and you have only a few suggestions for
all products, a lower value might work better for you. The other way
round, if you sell less than thousand different products, you may
have a lot of product suggestions of low quality. In this case it's
better to increase this value, e.g. to 0.05 or higher.

Caution: Decreasing the support to lower values than 0.01 exponentially
increases the time for generating the suggestions. If your database
contains a lot of orders, the time to complete the job may rise from
hours to days!

See also:

* controller/jobs/product/bought/max-items
* controller/jobs/product/bought/min-confidence
* controller/jobs/product/bought/limit-days
* controller/jobs/product/bought/size

# name

Class name of the used product suggestions scheduler controller implementation

```
controller/jobs/product/bought/name = 
```

* Default: 
* Type: string - Last part of the class name
* Since: 2014.03

Each default job controller can be replace by an alternative imlementation.
To use this implementation, you have to set the last part of the class
name as configuration value so the controller factory knows which class it
has to instantiate.

For example, if the name of the default class is

```
 \Aimeos\Controller\Jobs\Product\Bought\Standard
```

and you want to replace it with your own version named

```
 \Aimeos\Controller\Jobs\Product\Bought\Myalgorithm
```

then you have to set the this configuration option:

```
 controller/jobs/product/bought/name = Myalgorithm
```

The value is the last part of your own class name and it's case sensitive,
so take care that the configuration value is exactly named like the last
part of the class name.

The allowed characters of the class name are A-Z, a-z and 0-9. No other
characters are possible! You should always start the last part of the class
name with an upper case character and continue only with lower case characters
or numbers. Avoid chamel case names like "MyOptimizer"!


# size

Number of items processed at once

```
controller/jobs/product/bought/size = 100
```

* Default: 100
* Type: integer - Number of items processed at once
* Since: 2023.01

The items which are bought together are processed in batches to reduce
the time needed for associating all items. Higher numbers can improve
the speed while requiring more memory.

See also:

* controller/jobs/product/bought/max-items
* controller/jobs/product/bought/min-support
* controller/jobs/product/bought/min-confidence
* controller/jobs/product/bought/limit-days