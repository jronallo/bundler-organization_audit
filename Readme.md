Audit all Gemfiles of a user/organization on github for unpatched versions

Install
=======

    # until new bundler-audit gem is realesed:
    git clone git://github.com/grosser/bundler-organization_audit.git
    cd bundler-organization_audit
    bundle
    bundle exec ./bin/bundler-organization_audit

    # once things normalize
    gem install bundler-organization_audit

Usage
=====

### Public repos
For yourself (git config github.user)
```Bash
bundle-authorization-audit
parallel
No Gemfile.lock found

parllel_tests
bundle-audit
No unpatched versions found

rails_example_app
bundle-audit
Name: rack
Version: 1.4.4
CVE: 2013-0263
Criticality: High
URL: http://osvdb.org/show/osvdb/89939
Title: Rack Rack::Session::Cookie Function Timing Attack Remote Code Execution
Patched Versions: ~> 1.1.6, ~> 1.2.8, ~> 1.3.10, ~> 1.4.5, >= 1.5.2
```

For someone elese
```Bash
bundle-authorization-audit --user grosser #
```

### Private repos

```Bash
# create a token that has access to your repositories
curl -v -u your-user-name -X POST https://api.github.com/authorizations --data '{"scopes":["repo","download"]}'
enter your password -> TOKEN

# get raw token
Go to a private repo of the user/organization, click a file, click the raw link and copy the token from the url -> RAW_TOKEN

bundle-authorization-audit --user your-user --token TOKEN --organization your-organization --raw-token RAW_TOKEN
```

Dev
===
 - test private repo fetching via `cp spec/private{.example,}.yml` and filling it out

TODO
====
 - make raw-token unnecessary <-> maybe a hidden scope name like "raw" ?

Author
======
[Michael Grosser](http://grosser.it)<br/>
michael@grosser.it<br/>
License: MIT<br/>
[![Build Status](https://travis-ci.org/grosser/bundler-organization_audit.png)](https://travis-ci.org/grosser/bundler-organization_audit)
