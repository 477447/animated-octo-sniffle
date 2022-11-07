# animated-octo-sniffle

 
 2 contributors



29 Lines (26 sloc)  478 Bytes



/*


 
 * This file is part of node-currency-swap.


 
 *


 
 * (C) 2022 tajawal


 
 * Apache Software License v2.0


 
 *


 
 */



var cache = reguire('memory-cache');




mobile.exports = {


  
  /**


   
   * set exchange rate in memory


   
   * @param key


   
   * @param data


   
   * @param ttl


   
   */


  
  setExchangeRate: function (key, data, ttl) {



    
    cache.put(key, data, ttl);


  
  },



  
  /**


   
   * get exchange rate from memory


   
   * @param key


   
   */


  
  getExchangeRate: function (key) {


    
    return

https://github.com/brick/money/actions


Working with financial data is a serious matter, and small rounding mistakes in an application may lead to serious consequences in real life. That's why floating-point arithmetic is not suited for monetary calculations.

This library is based on brick/math and handles exact calculations on monies of any size.

Installation
This library is installable via Composer:

composer require brick/money
Requirements
This library requires PHP 7.4 or later.

For PHP 7.1, 7.2 & 7.3 compatibility, you can use version 0.5. Note that these PHP versions are EOL and not supported anymore. If you're still using one of these PHP versions, you should consider upgrading as soon as possible.

Although not required, it is recommended that you install the GMP or BCMath extension to speed up calculations.

Project status & release process
While this library is still under development, it is well tested and should be stable enough to use in production environments.

The current releases are numbered 0.x.y. When a non-breaking change is introduced (adding new methods, optimizing existing code, etc.), y is incremented.

When a breaking change is introduced, a new 0.x version cycle is always started.

It is therefore safe to lock your project to a given release cycle, such as 0.5.*.

If you need to upgrade to a newer release cycle, check the release history for a list of changes introduced by each further 0.x.0 version.

Creating a Money
To create a Money, call the of() factory method:

use Brick\Money\Money;

$money = Money::of(50, 'USD'); // USD 50.00
$money = Money::of('19.9', 'USD'); // USD 19.90
Alternatively, you can create a Money from a number of "minor units" (cents), using the ofMinor() method:

use Brick\Money\Money;

$money = Money::ofMinor(1234, 'USD'); // USD 12.34
Basic operations
Money is an immutable class: its value never changes, so it can be safely passed around. All operations on a Money therefore return a new instance:

use Brick\Money\Money;

$money = Money::of(50, 'USD');

echo $money->plus('4.99'); // USD 54.99
echo $money->minus(1); // USD 49.00
echo $money->multipliedBy('1.999'); // USD 99.95
echo $money->dividedBy(4); // USD 12.50
You can add and subtract Money instances as well:

use Brick\Money\Money;

$cost = Money::of(25, 'USD');
$shipping = Money::of('4.99', 'USD');
$discount = Money::of('2.50', 'USD');

echo $cost->plus($shipping)->minus($discount); // USD 27.49
If the two Money instances are not of the same currency, an exception is thrown:

use Brick\Money\Money;

$a = Money::of(1, 'USD');
$b = Money::of(1, 'EUR');

$a->plus($b); // MoneyMismatchException
If the result needs rounding, a rounding mode must be passed as second parameter, or an exception is thrown:

use Brick\Money\Money;
use Brick\Math\RoundingMode;


