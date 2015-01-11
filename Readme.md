#PHP-SASS: A wrapper for libsass of PHP

##Install

See INSTALL

##Features

1. Fully wrap for libsass
2. Fully support the options of libsass
3. Provide the php function to libsass, so you can call any php function as libsass's function, like this php(time) or php(count_down, 1, 2, 3)
4. Fully support all kinds of type in the sass and can translate them to php and back

##Type Conversion Rules

There is a catch here, for PHP, an array can be a list and a hash, and both.

But in Sass, there is no thing like array.

So, when convert back from sass, anything will be fine, but when converting php to sass, there is a slightly problem, how to convert mutant arrays?

So, php-sass use a simple solution here, only object maps to map, and array only maps to list. If you want to return an array as a map, just cast it to object, it's simple.

###Sass -> PHP

| Sass 		| PHP 		|
|:---------:|:---------:|
| number 	| double	|
| string 	| string	|
| color 	| hex color |
| boolean 	| boolean 	|
| null 		| null 		|
| list 		| array		|
| map 		| array		|

###PHP -> Sass

| PHP 		| Sass 				|
|:---------:|:-----------------:|
| double 	| number			|
| long 		| number			|
| string 	| string			|
| boolean 	| boolean 			|
| null 		| null 				|
| array		| list(space sep)	|
| object	| map				|

About The PHP Function in Sass
--------------------------------------------------------------------------------

The php function in sass can direcly call php's function(in global context).

Here is some example:

1. Without parameters

	php(time)

This equals to:

	time();

2. With simple parameters

	php(hello world)

This equals to:

	hello("world");

3. With multiple parameters

	php(sprintf, "%s %s", hello, world)

This equals to:

	sprintf("%s %s", "hello", "world");

4. Using map or list:

	php(var_dump, (hello: world))

This equals to:

	var_dump(array("hello" => "world"));
