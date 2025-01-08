Working dates: 8/01/25

# Contents
- Basic syntax
	1. What is PHP?
	2. PHP tags
	3. Escaping from HTML
	4. Instruction separation
	5. Comments
- Types
	1. Introduction


# Basic syntax
# What is PHP?
PHP (recursive acronym for PHP: Hypertext Preprocessor) is a widely-used open source general-purpose scripting language that is especially suited for web development and can be embedded into HTML. 
Example:
```php
<!DOCTYPE html>
<html>
	<head>   
		<title>Example</title>   
	</head>   
<body>      
<?php   echo "Hi, I'm a PHP script!";   ?>      </body>   
</html>
```

# PHP tags
When PHP parses a file, it looks for opening and closing tags, which are \<?php and ?> which tell php to start and stop interpreting the code between them. Parsing in this manner allows PHP to be embedded in all sorts of different documents, as everything outside of a pair of opening and closing tags is ignored by the PHP parser.

PHP includes a short echo tag \<?= which is a short-hand to the more verbose \<?php echo.
Example:
```php
<?php echo 'if you want to serve PHP code in XHTML or XML documents, use these tags'; ?>

You can use the short echo tag to <?= 'print this string' ?>.
    It's equivalent to <?php echo 'print this string' ?>.

<? echo 'this code is within short tags, but will only work '.
            'if short_open_tag is enabled'; ?>
```

If a file contains only PHP code, it is preferable to omit the PHP closing tag at the end of the file. This prevents accidental whitespace or new lines being added after the PHP closing tag, which may cause unwanted effects because PHP will start output buffering when there is no intention from the programmer to send any output at that point in the script.

```php
`<?php   echo "Hello world";

// ... more code

echo "Last statement";      

// the script ends here with no PHP closing tag`
```

# Escaping from HTML
Everything outside of a pair of opening and closing tags is ignored by the PHP parser which allows PHP files to have mixed content. This allows PHP to be embedded to HTML documents, for example to create templates.
```php
<p>This is going to be ignored by PHP and displayed by the browser.</p>   
<?php echo 'While this is going to be parsed.'; ?>   
<p>This will also be ignored by PHP and displayed by the browser.</p>
```
This works as expected, because when the PHP interpreter hits the ?> closing tags, it simply starts outputting whatever it finds (except for the immediately following newline) until it hits another opening tag unless in the middle of a conditional statement in which case the interpreter will determine the outcome of the conditional before making a decision of what to skip over.
Example: Advanced escaping using conditions
```php
<?php if ($expression == true): ?>
This will show if the expression is true.   
<?php else: ?>
Otherwise this will show.   
<?php endif; ?>
```
In this example PHP will skip the blocks where the conditions is not met, even though they are outside of the PHP open/close tags; PHP skips them according to the condition since the PHP interpreter will jump over blocks contained within a condition that is not met.
For outputting large blocks of text, dropping out of PHP parsing mode is generally more efficient than sending all of the text through echo or print.

Note: If PHP is embeded within XML or XHTML the normal PHP \<?php ?> must be used to remain compliant with the standards.

# Instruction separation
As in C or Perl, PHP requires instructions to be terminated with a semicolon at the end of each statement. The closing tag of a block of PHP code automatically implies a semicolon; you do not need to have a semicolon terminating the last line of PHP block. The closing tag for the block will include the immediately trailing newline if one is present.
Example: Example showing the closing tag encompassing the trailing newline
```php
<?php echo "Some text"; ?>
No newline   
<?= "But newline now" ?>
```
The above example will output:
```output
Some textNo newline
But newline now
```
Examples of entering and exiting the PHP parser:
```php
<?php   echo 'This is a test';   ?>
<?php echo 'This is a test' ?>      
<?php echo 'We omitted the last closing tag';
```

# Comments
PHP supports 'C', 'C++' and Unix shell-style (Perl style) comments. For example:
```php
<?php   
echo 'This is a test'; // This is a one-line c++ style comment   
	/* This is a multi line comment
		yet another line of comment */
	echo 'This is yet another test';
	echo 'One Final Test'; # This is a one-line shell-style comment  
?>
```
The "one-line" comment styles only comment to the end of the line or the current block of PHP code, whichever comes first. This means that HTML code after // ... ?> will be printed: ?> breaks out of PHP mode and returns to HTML mode, and // or # cannot influence that.
```php
<h1>This is an <?php # echo 'simple';?> example</h1>
<p>The header above will say 'This is an example'.</p>
```
'C' style comments end at the first */  encountered. Make sure you don't nest 'C' style comments. It is easy to make this mistake if you are trying to comment out a large block of code.
```php
<?php   
/*   
	echo 'This is a test'; /* This comment will cause a problem 
*/   
*/   
?>
```


# Types
# Introduction
Every single expression in PHP has one of the following built-in types depending on its value:
- null
- bool
- int
- float (floating-point number)
- string
- array
- object
- callable
- resource

PHP is dynamically typed language, which means that by default there is no need to specify the type of a variable, as this will be determined at runtime. However, it is possible to statically type some aspect of the language via the use of type declarations. 

Types restrict the kind of operations that can be performed on them. However, if an expression/variable is used in an operation which its type does not support, PHP will attempt to type juggle the value into a type that supports the operation. this process depends on the context in which the value is used.

Note: It is possible to force an expression to be evaluated to a certain type by using a type cast. A variable can also be type cast in-place by using the settype() function on it.

To check the value and type of an expression, use the var_dump() function. To retrieve the type of an expression, use get_debug_type() function. However, to check if an expression is of certain type use the is_type functions instead.
```php
<?php   
$a_bool = true; // a bool   
$a_str = "foo"; // a string   
$a_str2 = 'foo'; // a string   
$an_int = 12; // an int      
echo get_debug_type($a_bool), "\n";   
echo get_debug_type($a_str), "\n";      

// If this is an integer, increment it by four   
if (is_int($an_int)) {   
$an_int += 4;   
}  
var_dump($an_int);      

// If $a_bool is a string, print it out   
if (is_string($a_bool)) {   
echo "String: $a_bool";   
}   
?>
```
Output of the above example in PHP 8:
```output
bool
string
int(16)
```













