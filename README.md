# PHP Credit Card Validator


Validates popular debit and credit cards numbers against regular expressions and Luhn algorithm.
Also validates the CVC and the expiration date.

Since original project seems to be abandoned, this fork is made to support other existing repos with compatible namespaces such as rap2hpoutre/laravel-credit-card-validator which also appears to be abondoned. I forked it to selay/laravel-credit-card-validator

# Requirements
PHP 7.0+. 

Require the package in `composer.json`

```json
"require": {
    "selay/php-credit-card-validator": "4.*"
},
```
## Usage

### Validate a card number knowing the type:

```php
$card = CreditCard::validCreditCard('5500005555555559', CreditCard::TYPE_MASTERCARD);
print_r($card);
```

Output:

```
Array
(
    [valid] => 1
    [number] => 5500005555555559
    [type] => mastercard
)
```

### Validate a card number against several types:

```php
$card = CreditCard::validCreditCard('5500005555555559', [CreditCard::TYPE_VISA, CreditCard::TYPE_MASTERCARD]);
print_r($card);
```

Output:

```
Array
(
    [valid] => 1
    [number] => 5500005555555559
    [type] => mastercard
)
```

### Validate a card number and return the type:

```php
$card = CreditCard::validCreditCard('371449635398431');
print_r($card);
```

Output:

```
Array
(
    [valid] => 1
    [number] => 371449635398431
    [type] => amex
)
```

### Validate the CVC

```php
$validCvc = CreditCard::validCvc('234', CreditCard::TYPE_VISA);
var_dump($validCvc);
```

Output:

```
bool(true)
```

### Validate the expiration date

```php
$validDate = CreditCard::validDate('2013', '07'); // past date
var_dump($validDate);
```

Output:

```
bool(false)
```

## Tests

Execute the following command to run the unit tests:

    vendor/bin/phpunit
