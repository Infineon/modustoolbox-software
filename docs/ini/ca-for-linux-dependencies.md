# CA for Linux: Dependencies

On Linux, the CA relies on the following libraries that are linked directly into the CA. Some libraries are not required for the implementation of IoT Network Intelligence(INI)

| Function | Libraries we have integrated with | Required for INI | Notes
| :---------: | :--------------------------------------: | :-----------------: | :--------: |
C library | libc | | |
SSL library  | libssl | | Version must be >= 1.0.2h. (Earlier versions do not support the public certificate that the Cirrent cloud uses.)
Crypto library | libcrypto
Thread library | libpthread 
HTTP client library | libcurl 
Realtime extensions | librt
