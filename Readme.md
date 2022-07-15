### Problems installing python  with pyenv on Mac OS Big Sur

```bash
Python/random.c:89:19: note: did you mean 'py_getentropy'?
Python/random.c:81:1: note: 'py_getentropy' declared here
py_getentropy(unsigned char *buffer, Py_ssize_t size, int fatal)
^
Python/random.c:98:19: error: implicit declaration of function 'getentropy' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
            res = getentropy(buffer, len);
                  ^
2 errors generated.
make: *** [Python/random.o] Error 1
make: *** Waiting for unfinished jobs....
```
```bash
python-build: use readline from homebrew
python-build: use zlib from xcode sdk

BUILD FAILED (OS X 11.3 using python-build 20180424)

Inspect or clean up the working tree at /var/folders/7j/0qtpb8vs1_s34ynv0f6rrs840000gn/T/python-build.20210304114832.65954
Results logged to /var/folders/7j/0qtpb8vs1_s34ynv0f6rrs840000gn/T/python-build.20210304114832.65954.log

Last 10 log lines:
./Modules/posixmodule.c:8210:15: error: implicit declaration of function 'sendfile' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
        ret = sendfile(in, out, offset, &sbytes, &sf, flags);
              ^
./Modules/posixmodule.c:10432:5: warning: code will never be executed [-Wunreachable-code]
    Py_FatalError("abort() called from Python code didn't abort!");
    ^~~~~~~~~~~~~
1 warning and 1 error generated.
1 warning generated.
make: *** [Modules/posixmodule.o] Error 1
make: *** Waiting for unfinished jobs....
```

### IF "ERROR The Python ssl extension was not compiled. Missing the OpenSSL lib?"
```bash
python-build: use readline from homebrew
python-build: use zlib from xcode sdk
ERROR: The Python ssl extension was not compiled. Missing the OpenSSL lib?

Please consult to the Wiki page to fix the problem.
https://github.com/pyenv/pyenv/wiki/Common-build-problems


BUILD FAILED (OS X 11.4 using python-build 1.2.16-5-g7097f820)

```
### THEN
reinstall openssl

```bash
brew reinstall openssl

Error: /usr/local/opt/openssl@3 is not a valid keg


cd /usr/local/opt/
mv openssl@3 openssl@3_old
brew reinstall openssl

```
### ENDIF




### use patch install
```bash
brew install zlib
brew install sqlite
brew install bzip2
brew install libiconv
brew install libzip
source ~/.env-exporter
pyenv install --patch 2.7.11 < Python-2.7.11-macos.patch
pyenv install --patch 3.4.10 < Python-3.4.x-macos.patch
pyenv install --patch 3.6.5 < Python-3.6+macos.patch
```


### Reference documentation
https://koji-kanao.medium.com/install-python-3-7-3-6-and-3-5-on-bigsure-with-pyenv-21194becd2fe
