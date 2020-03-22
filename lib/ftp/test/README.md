# FTP Tests

## FTP Property Based Tests

There are two ways to run the property based tests for the `ftp` application.

**Notes**

Before starting the test, please set:

1. `ERL_TOP` to the root of the OTP.
2. `PATH=$ERL_TOP:bin/$PATH`.

### Property Suite

```bash
ct_run -suite ftp_property_test_SUITE -config ftp.config
```

The file `ftp.config` can change how many tests are run by the
property based software.

### Erlang Shell

```bash
cd property_test
erl
1> ftp:start().
2> c(ftp_simple_client_server, [{d, 'PROPER'}]).
3> proper:quickcheck(ftp_simple_client_server:prop_ftp()).
```
