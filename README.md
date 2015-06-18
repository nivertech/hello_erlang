cowboy test
===========


http://learnyousomeerlang.com/building-otp-applications

http://erlware.github.io/relx/

Explains both Rebar and Relx:
- https://howistart.org/posts/erlang/1

relx.org

http://blog.troutwine.us/2013/09/13/trivial_otp_releases.html

--------------------------------------------------------------------------------

Relx talk at EUC2013
- http://www.erlang-factory.com/conference/ErlangUserConference2013/speakers/EricMerritt
- slides: http://www.slideshare.net/ericbmerritt/euc-202
- pdf:    http://www.erlang-factory.com/upload/presentations/829/EUC2013-Talk.pdf
- video:  https://vimeo.com/70859112

--------------------------------------------------------------------------------


Create release:


``` bash
$ relx
```

Create self-container `.tar.gz` released:

``` bash
$ relx release tar
```