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


``` bash
$ cd hello_erlang
$ rebar get-deps
==> hello_erlang (get-deps)
Pulling cowboy from {git,"git@github.com:ninenines/cowboy.git",{tag,"1.0.1"}}
Cloning into 'cowboy'...
==> cowboy (get-deps)
Pulling cowlib from {git,"git://github.com/ninenines/cowlib.git","1.0.0"}
Cloning into 'cowlib'...
Pulling ranch from {git,"git://github.com/ninenines/ranch.git","1.0.0"}
Cloning into 'ranch'...
==> cowlib (get-deps)
==> ranch (get-deps)
...

$ rebar clean compile
==> hello_erlang (clean)
==> cowlib (compile)
Compiled src/cow_date.erl
...

$ rebar shell
==> hello_erlang (shell)
Erlang/OTP 17 [erts-6.4] [source] [64-bit] [smp:4:4] [async-threads:10] [hipe] [kernel-poll:false]

Eshell V6.4  (abort with ^G)
1> 
1> application:which_applications().
[{crypto,"CRYPTO","3.5"},
 {stdlib,"ERTS  CXC 138 10","2.4"},
 {kernel,"ERTS  CXC 138 10","3.2"}]
2> application:start(cowboy).
{error,{not_started,ranch}}
3> application:start(ranch). 
ok
4> application:start(cowboy).
{error,{not_started,cowlib}}
5> application:start(cowlib).
ok
6> application:start(cowboy).
ok
7> application:start(hello_erlang).
ok
8> 
```

Now open `http://localhost:8080` in a web browser or do curl:

``` bash
$ curl http://localhost:8080
Hello Erlang!
$
```

------------------------------------------------------------------------------------------


Create release:


``` bash
$ ./relx
===> Starting relx build process ...
===> Resolving OTP Applications from directories:
          /home/zvi/ws/ERLANG_COURSE/hello_erlang/ebin
          /home/zvi/ws/ERLANG_COURSE/hello_erlang/deps
          /usr/local/lib/erlang/lib
===> Resolved hello_erlang_release-1
===> Including Erts from /usr/local/lib/erlang
===> release successfully created!
```

Create self-container `.tar.gz` released:

``` bash
$ ./relx release tar
```

