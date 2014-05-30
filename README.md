grails-spring-security-oauth-weibo [![Build Status](https://api.travis-ci.org/donbeave/grails-spring-security-oauth-weibo.png?branch=master)](https://travis-ci.org/donbeave/grails-spring-security-oauth-weibo)
==================================

Weibo extension for [Grails Spring Security OAuth][spring-security-oauth-plugin] plugin

Installation
------------

Add the following plugin definition to your BuildConfig:
```groovy
// ...
plugins {
  // ...
  compile ':spring-security-oauth:2.0.2'
  compile ':spring-security-oauth-weibo:0.1'
  // ...
}
```

Usage
-----

Add to your Config:
```groovy
oauth {
  // ...
  providers {
    // ...
    weibo {
      api = org.scribe.builder.api.SinaWeiboApi20
      key = 'oauth_weibo_key'
      secret = 'oauth_weibo_secret'
      successUri = '/oauth/weibo/success'
      failureUri = '/oauth/weibo/error'
      callback = "${baseURL}/oauth/weibo/callback"
      scope = 'all'
    }
    // ...
  }
}
```

In your view you can use the taglib exposed from this plugin and from OAuth plugin to create links and to know if the user is authenticated with a given provider:
```xml
<oauth:connect provider="weibo" id="weibo-connect-link">Weibo</oauth:connect>

Logged with weibo?
<s2o:ifLoggedInWith provider="weibo">yes</s2o:ifLoggedInWith>
<s2o:ifNotLoggedInWith provider="weibo">no</s2o:ifNotLoggedInWith>
```

Copyright and license
---------------------

Copyright 2013-2014 Alexey Zhokhov under the [Apache License, Version 2.0](LICENSE). Supported by [Polusharie][polusharie].

[polusharie]: http://www.polusharie.com
[spring-security-oauth-plugin]: https://github.com/enr/grails-spring-security-oauth
