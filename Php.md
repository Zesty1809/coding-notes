Working dates: 8/01/25

# Contents
1. [[#What is PHP?]]
2. [[#PHP tags]]
3. [[#Escaping from HTML]]
4. [[#Instruction separation]]

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