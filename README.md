This is work in progress to add two features:
 - allowing multiple audiences to be defined for oauth scenarios where different resources using different flows
   requires using multiple audiences. In our case, the `client_id` for any Single Page 
   Apps is actually set as the audience. The problem is that since we can only set one audience this means none of our services can 
   can communicate as authenticated service-to-service since the single page app will have a different audience.   
   This issue can be reference [here](https://github.com/jpadilla/pyjwt/issues/205)

 - allowing JSON web Keys to be used with rs256 (which has already been completed by the awesome @mark-adams) but has not yet been 
   merged into master as they're waiting for version 2. The PR for this issue can found [here](https://github.com/jpadilla/pyjwt/pull/202)
   > A note on this - we have successfully built from this branch `add-jwk-for-hmac-rsa` and are able to use the json web key (jwk) 
     to verify the signatures of the JWTs. 



# PyJWT

[![travis-status-image]][travis]
[![appveyor-status-image]][appveyor]
[![pypi-version-image]][pypi]
[![coveralls-status-image]][coveralls]
[![docs-status-image]][docs]

A Python implementation of [RFC 7519][jwt-spec].
Original implementation was written by [@progrium][progrium].

## Installing

```
$ pip install PyJWT
```

## Usage

```python
>>> import jwt
>>> encoded = jwt.encode({'some': 'payload'}, 'secret', algorithm='HS256')
'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzb21lIjoicGF5bG9hZCJ9.4twFt5NiznN84AWoo1d7KO1T_yoc0Z6XOpOVswacPZg'

>>> jwt.decode(encoded, 'secret', algorithms=['HS256'])
{'some': 'payload'}
```

## Tests

You can run tests from the project root after cloning with:

```
$ python setup.py test
```

[travis-status-image]: https://secure.travis-ci.org/jpadilla/pyjwt.svg?branch=master
[travis]: http://travis-ci.org/jpadilla/pyjwt?branch=master
[appveyor-status-image]: https://ci.appveyor.com/api/projects/status/h8nt70aqtwhht39t?svg=true
[appveyor]: https://ci.appveyor.com/project/jpadilla/pyjwt
[pypi-version-image]: https://img.shields.io/pypi/v/pyjwt.svg
[pypi]: https://pypi.python.org/pypi/pyjwt
[coveralls-status-image]: https://coveralls.io/repos/jpadilla/pyjwt/badge.svg?branch=master
[coveralls]: https://coveralls.io/r/jpadilla/pyjwt?branch=master
[docs-status-image]: https://readthedocs.org/projects/pyjwt/badge/?version=latest
[docs]: http://pyjwt.readthedocs.org
[jwt-spec]: https://tools.ietf.org/html/rfc7519
[progrium]: https://github.com/progrium
