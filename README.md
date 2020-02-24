EasySperocoin-PHP
===============

A simple class for making calls to Sperocoin's API using PHP.

Getting Started
---------------
1. Include connect.php into your PHP script:

    ```php
    require_once('connect.php');
    ```
2. Initialize Sperocoin connection/object:

    ```php
    $sperocoin = new Sperocoin('username','password');
    ```

    Optionally, you can specify a host, port. Default is HTTP on localhost port 55681.

    ```php
    $sperocoin = new Sperocoin('username','password','localhost','55681');
    ```

    If you wish to make an SSL connection you can set an optional CA certificate or leave blank
    ```php
    $sperocoin->setSSL('/full/path/to/mycertificate.cert');
    ````

3. Make calls to SperoCoind as methods for your object. Examples:

    ```php
    $sperocoin->getinfo();
    
    $sperocoin->getrawtransaction('b5b7ae52bddf6a046d514ed65d5e66e9f0a86d3efa532e4db22cd8cd1f272f16',1);
    
    $sperocoin->getblock('60265ddd58b860b26c7e30f4c54ef0bf1ebdf208ed1da5ddabeebecb68fe672d');
    ```

Additional Info
---------------
* When a call fails for any reason, it will return false and put the error message in `$sperocoin->error`

* The HTTP status code can be found in $sperocoin->status and will either be a valid HTTP status code or will be 0 if cURL was unable to connect.

* The full response (not usually needed) is stored in `$sperocoin->response` while the raw JSON is stored in `$sperocoin->raw_response`
