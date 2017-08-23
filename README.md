check_openpgpkey
================

Nagios/Icinga plugin for checking OPENPGPKEY (TYPE61) records.

Those records are defined in [RFC7929](https://tools.ietf.org/html/rfc7929), as
a new way to lookup and retrieve PGP keys.

This plugin check for the existance of a record for the given user and can
perform various other checks like expiration date.


Usage
=====

    -h, --help            show this help message and exit
    --id ID, -I ID        Hostname to check.
    --remaining-days REMAINING_DAYS
                          Minimum remaining days before expiry.
                          Format: INTEGER[,INTEGER]. 1st is days for warning,
                          2nd is critical.
    --no-dnssec           Continue even if DNS replies aren't DNSSEC authenticated.
    --resolver RESOLVER   Use a custom resolver.
    --timeout TIMEOUT     Network timeone in sec. Default: 10
    --version             show program's version number and exit


Examples
--------

   * `check_openpgpkey nemunaire@nemunai.re`
   * `check_openpgpkey -I 0x842807A84573CC96 nemunaire@nemunai.re`
   * `check_openpgpkey -R 60 -I 0x842807A84573CC96 nemunaire@nemunai.re`


Requirements
============

   * Python >= 3.3
   * [dnspython](http://www.dnspython.org/)
   * `gpg` binary
   * DNSSEC capable resolver (or use `--no-dnssec` but be aware of the security implications)
