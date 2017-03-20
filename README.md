sa-gogs
=======
[![Build Status](https://travis-ci.org/softasap/sa-gogs.svg?branch=master)](https://travis-ci.org/softasap/sa-gogs)


Gogs - A painless self-hosted Git service.


Example of use: check box-example

Simple:

```YAML


...

roles:

     - {
         role: "sa-gogs"
       }

```


Advanced:

```YAML


```


```YAML


     - {
         role: "sa-gogs"
       }

```


Usage with ansible galaxy workflow
----------------------------------

If you installed the sa-gogs role using the command


`
   ansible-galaxy install softasap.sa-gogs
`

the role will be available in the folder library/softasap.sa-gogs
Please adjust the path accordingly.

```YAML

     - {
         role: "softasap.sa-gogs"
       }

```



Copyright and license
---------------------


Code licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) or the [MIT License] (http://opensource.org/licenses/MIT).

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)
