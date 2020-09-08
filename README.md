# Heroku buildpack: Erlang

This is yet another Heroku buildpack for Erlang apps. It uses [Rebar](https://github.com/rebar/rebar) or [Rebar3](https://github.com/rebar/rebar3).

Which build tool to use is automatically detected.  Rebar is currently the default.  If either `rebar3` or `rebar.lock` are present, Rebar3 will be used. 

### Configure your Heroku or Dokku

    $ echo 'BUILDPACK_URL=https://github.com/arnfred/heroku-buildpack-erlang.git' > .env

### Select an Erlang version

The script was originally intendend for selecting an erlang version by adding a dotfile called `.preferred_otp_version`. However, it goes on to fetch this version from an svn server with only two files available [0], so I've hardcoded the version instead. In the future it might make sense to change over to the approach by [1] where ERTS is compiled on deploy, but that's a bit time consuming.

Currently supported OTP versions:

* OTP-20.1

[0]: https://github.com/arnfred/heroku-buildpack-erlang/blob/master/bin/compile#L123
[1]: https://github.com/yycking/heroku-buildpack-erlang/commit/1c4704f777e9f2ddba3af0c08d76ca81a2dfb428

### Select Rebar3 profile

To select the rebar3 profile version for your app:

    $ echo prod > .preferred_rebar_profile
