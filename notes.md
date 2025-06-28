The `fftwtools` package is an issue because it needs an fft library to be
installed for us on Linux, and this library is not easy to get on a server
where I need it. Let's see what we can do.

The string `fftw` only shows up in a few places, but all occur in the
`mcse_multi` function which seems important.

```
$ find . -type f -exec grep -H fftw {} \; | less -S

R/mcse_multi.R:  w <- Re(fftw_r2c(w))
R/mcse_multi.R:    FF <- mvfftw_r2c (FF)
R/mcse_multi.R:    FF <- mvfftw_c2r(FF) / (2* n )
R/mcse_multi.R:    FF <- fftw_r2c (FF)
R/mcse_multi.R:    FF <- fftw_c2r(FF) / (2* n )
```

