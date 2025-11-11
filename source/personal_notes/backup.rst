####################
Data Backup Strategy
####################

**********
3-2-1 rule
**********

- 3 copies :
    1. Original data
    2. External "cold stored" HDD copy
    3. Cloud stored copy

- 2 different types of storage media/device :
    1. Device on which the original data is stored
    2. Cloud storage (maybe Amazon Glacier)

- 1 copy off-site :
    1. The cloud stored copy


*****************
Checksum manifest
*****************

Create a checksum manifest to verify data integrity.

.. code-block:: bash

    sha256sum filename


**********
Encryption
**********

Encrypt the drives using VeraCrypt for security.
Store the encryption key somewhere safe.
