# attribute-encryption
Allows you to define what attributes in your eloquent model which should be encrypted and decrypted.

## Installing

Install using Composer `composer require larapack/attribute-encryption 1.*`.

## Usage

First add the traits `Manipulateable` and `Encryptable` to your Eloquent Model.
```
<?php

namespace App;

use Larapack/AttributeManipulating/Manipulateable;
use Larapack/AttributeEncryption/Encryptable;

class User
{
  use Manipulateable;
  use Encryptable;
  
  /**
   * @var array List of attribute names which should be encrypted
   */ 
  protected $encrypt = ['password']; // set the attribute names you which to encrypt/decrypt
  
  //...
}
```

Now whenever you set the attribute `password` it will now be encrypted and whenever you get the attribute it will be decrypted.

Test:
```
$user = new App\User;
$user->password = 'secret';
echo $user->getOriginalAttribute('password'); // Here you will see the encrypted password
dump($user); // Here you will see the encrypted password
echo $user->password; // Here you will see the decrypted password
```
