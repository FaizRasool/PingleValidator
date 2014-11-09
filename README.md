Nextor Validator
===============

Nextor Validator class provide the validation for the user input on the server side. 

Basic usage
------------
```php
//include the validation class
require_once("library/Nextorvalidate.php"); 

//initialize the class
$val = new validation;

/*** use POST as the source ***/
$val->addSource($_POST);

/*** add a form field rule ***/
/*** addRule('name', 'type', required, min, max, trim, regex)***/
$val->addRule('name', 'string', true, 5, 255, true)
->addRule('email', 'email', true, 1, 255, true)
->addRule('website', 'url', false, 1, 255, true)
->addRule('age', 'numeric', true, 1, 100, true)
->addRule('salary', 'float', false, 1, 99999999, true)
->addRule('date', 'regex', true, 10, 10, true,"#^(((?:0?[1-9]|1[012])|(?:0?[1-9]|[12][0-9]|3[01])|([a-zA-Z]+))([.,]?[-.\\\/\s]))?(((?:0?[1-9]|1[012])|(?:0?[1-9]|[12][0-9]|3[01])|([a-zA-Z]+))([.,]?[-.\\\/\s]))?((?:20|19)[0-9]{2})$#");
/*** run the validation rules ***/
$val->run();
/*** if there are errors show them ***/
if(sizeof($val->errors) > 0)
{
print_r($val->errors);
}
else
{
$_POST=$val->sanitized;
}
```

### Validation Methods
----------------------
1. string
2. email
3. url
4. numeric
5. float
6. regex
7. ipv4
8. ipv6
9. bool
