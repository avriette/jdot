jdot
===

Jane's degree-of-trust metric for evaluating twitter personas, or how to create
an unfortunately homophilic but safer group of twitter associates (followers or
otherwise).

methods
===

* intersection of followers-of and followed-by of arbitrary accounts
* intersection of following groups (e.g., advocacy) to assign a higher or
  lower "score"

* inspection of recent N tweets for unwanted content
* inspection of recent N tweets for RT of users within certain groups
  (advocacy...) to assess higher/lower "score".

* follower-of or followed-by people blocked by issuing user

* caching in riak to alleviate the api limits
  - a daemon that went and polled the records in riak at slightly less than
    the api threshold to keep 'known users' up-to-date so that decisions on
    new users (users who have not been queried before) do not result in lots
    of new requests and decisions can be returned quickly.
  - if datas are stored in riak or other persistent datastore, a real-time
    'dashboard' report of the jdot-per-user could be easily displayed, and
    trends could be mapped.

why
===

certain groups of people have been suggesting that they "infiltrate" e.g.,
advocacy groups (primarily social justice activists, feminists, and so forth)
by creating new accounts and following people involved in these movements and
gaining the trust of the people therein. the purpose of this effort is to
subsequently have access to their tweets if accounts become blocked, or if the
primary account of the 'movement infiltrator' becomes blocked by means such as
randi harper's auto-blocker.

credit
===

obviously randi's
[`ggautoblocker`](https://github.com/freebsdgirl/ggautoblocker) lays important
foundational work here, with respect to determining the trustworthiness of
various people "by the company they keep." the problem addressed by jdot is the
inflexibility of `ggautoblocker` &mdash; it focuses on one community &mdash; and
it does not take any other factors into account.

so if one's goal is to determine the trustworthiness of a given account on
twitter but they are not members of large, targeted communities, they are left
without much of a way to evaluate new followers and people in their mentions.

`jdot` aims to create a modular means for evaluating trust (a term used very
loosely in this documentation & software) of a given user *relative to the user
issuing the query* rather than relative to groups they may or may not be members
of (such as advocacy, feminism, et cetera).

disclaimer
===

all systems can be gamed. this is why we call it gaming a system. this is only a
tool.

&copy; [@avriette](https://github.com/avriette) / jane avriette / [jane@cpan.org](mailto:jane@cpan.org)
