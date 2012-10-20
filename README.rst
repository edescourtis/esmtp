=======================================
esmtp - A simple SMTP client for Erlang
=======================================

This fork of esmtp will not try to maintain the same API as the original project.

esmtp is a simple OTP application providing a way to send emails (and
attachments) from erlang systems.


New Features
============

 - add XOAuth authentication gmail.
 - add mail headers "Subject" and "To".

TODO
====

support for utf-8.

Configuration
=============

The esmtp application is configured with OTP application configuration
env variables.

smarthost
  This is a tuple giving the hostname and port of the smtp server to
  send mail via. This will usually be a local smtp server on port 25.
default_from
  This is the default From address to use on outgoing mail if a From
  address is not supplied.
login
  The SMTP AUTH credentials to use. Either 'no_login' when not using
  SMTP AUTH (default) or {Username::string(),Password::string()}.


Example
-------

system.config::

  [{esmtp, [{smarthost, {"localhost", 25}}
           ,{default_from, "Erlang/OTP <erlang@localhost>"}]}].

gmail.config::

  [{esmtp, [{smarthost, {"smtp.gmail.com", 465}}
           ,{login, {"youraddress@gmail.com","yourpassword"}}
           ,{default_from, "Erlang pretending to be <youraddress@gmail.com>"}]}].

