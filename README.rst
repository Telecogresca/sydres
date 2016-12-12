Sydres - Redsys Client
----------------------

.. image:: https://travis-ci.org/Telecogresca/sydres.svg?branch=master
    :target: https://travis-ci.org/Telecogresca/sydres


ATTENTION
---------

This started as a fork of:

https://bitbucket.org/zikzakmedia/python-redsys

The focus is adding Python 3 support and some related minor improvements.

Credit to the original author, Zikzakmedia which can be found in the Bitbucket
URL. Special thanks to that project, and also to all the people who have made 
this project possible.

If you intend to use Python 2.x, better check the original project.

Redsys client
~~~~~~~~~~~~~

This software is used in order to perform credit card payments to the Redsys
service.

To use this mechanism you need first to have Redsys configured for your "store".

Requirements
------------

* Python 3.x

Installation
------------

Through pip:

.. code-block:: python

    pip install sydres

or easy_install:

.. code-block:: python

    easy_install sydres
    
or, from source, install it through:

.. code-block:: python

    python ./setup.py install

Quick Start
-----------

.. code-block:: python

    from sydres import Client

    SANDBOX = True
    REDSYS_MERCHANT_URL = 'http://www.zikzakmedia.com'
    REDSYS_MERCHANT_NAME = "Zikzakmedia SL"
    REDSYS_MERCHANT_CODE = '000000000'
    REDSYS_SECRET_KEY = '123456'
    REDSYS_TERMINAL = u'1'
    REDSYS_CURRENCY = u'978'
    REDSYS_TRANS_TYPE = u'0'

    values = {
            'DS_MERCHANT_AMOUNT': 10.0,
            'DS_MERCHANT_CURRENCY': 978,
            'DS_MERCHANT_ORDER': 'SO001',
            'DS_MERCHANT_PRODUCTDESCRIPTION': 'ZZSaas services',
            'DS_MERCHANT_TITULAR': REDSYS_MERCHANT_NAME,
            'DS_MERCHANT_MERCHANTCODE': REDSYS_MERCHANT_CODE,
            'DS_MERCHANT_MERCHANTURL': REDSYS_MERCHANT_URL,
            'DS_MERCHANT_URLOK': 'http://localhost:5000/redsys/confirm',
            'DS_MERCHANT_URLKO': 'http://localhost:5000/redsys/cancel',
            'DS_MERCHANT_MERCHANTNAME': REDSYS_MERCHANT_NAME,
            'DS_MERCHANT_TERMINAL': REDSYS_TERMINAL,
            'DS_MERCHANT_TRANSACTIONTYPE': REDSYS_TRANS_TYPE,
        }

    redsyspayment = Client(business_code=REDSYS_MERCHANT_CODE, secret_key=REDSYS_SECRET_KEY, sandbox=SANDBOX)
    redsys_form = redsyspayment.redsys_generate_request(values)

