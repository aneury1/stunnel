# stunnel FIPS install notes


### Unix HOWTO
* Only dynamic linking of the FIPS-enabled OpenSSL is currently supported,
  i.e. FIPS-enabled OpenSSL has to be configured with "shared" parameter.
* FIPS mode is autodetected if possible.  It can be forced with:
    ./configure --enable-fips
  or disable with:
    ./configure --disable-fips

### WIN32 HOWTO
* On 32-bit Windows install one of the following compilers:
  - MSVC 8.0 (VS 2005) Standard or Professional Edition
  - MSVC 9.0 (VS 2008) any edition including Express Edition
* On 64-bit Windows install one of the following compilers:
  - MSVC 8.0 (VS 2005) Standard or Professional Edition
  - MSVC 9.0 (VS 2008) Standard or Professional Edition
* Build FIPS-compliant OpenSSL DLLS according to:
  https://www.openssl.org/docs/fips/UserGuide-2.0.pdf
* Build stunnel normally with MSVC or Mingw.
  Mingw build requires DLL stubs.  Stubs can be built with:
  dlltool --def ms/libeay32.def --output-lib libcrypto.a
  dlltool --def ms/ssleay32.def --output-lib libssl.a
