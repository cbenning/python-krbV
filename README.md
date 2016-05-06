Copyright (C) 2001-2006 Red Hat, Inc.
Licensed under the LGPL.

This is a fork of the python-krbV module 'maintained' by Redhat. I have enabled password-based authentication for an experiment. This code is not to be used in production.

The code exposes the "krb5_get_init_creds_password" from the C library, as "init_creds_password" in the python module

To build:
 
```
./autogen.sh
```

```
make
```

To Install:

Note: I do not recommend you install this using the usual mechanism as it seems to be broken. 

Instead, I copy the .so file to the dist-packages folder to test, then immediately delete it.

Example:
```
sudo cp .libs/krbVmodule.so /usr/local/lib/python2.7/dist-packages/
```

How to use:
```python
import krbV

ctx = krbV.default_context()
principal = krbV.Principal(name="myprincipal",context=ctx)
ccache = krbV.CCache(name=ccache_file, context=ctx, primary_principal=principal)
ccache.init(principal)
ccache.init_creds_password(principal=principal,password="mypassword")
```

