flask-oauth-example
===================


Example code from Miguel Grinberg's "OAuth Authentication with Flask" article. http://blog.miguelgrinberg.com/post/oauth-authentication-with-flask

Forked by P. Conrad from: https://github.com/miguelgrinberg/flask-oauth-example for UCSD SPIS 2015.

# Google Example

If you want to do Google instead of Facebook or Twitter, you'll need some code similar to this code for Twitter:

```
class TwitterSignIn(OAuthSignIn):
    def __init__(self):
        super(TwitterSignIn, self).__init__('twitter')
        self.service = OAuth1Service(
            name='twitter',
            consumer_key=self.consumer_id,
            consumer_secret=self.consumer_secret,
            request_token_url='https://api.twitter.com/oauth/request_token',
            authorize_url='https://api.twitter.com/oauth/authorize',
            access_token_url='https://api.twitter.com/oauth/access_token',
            base_url='https://api.twitter.com/1.1/'
        )
```

Code for Google should look like this, and can be added right after the Twitter code:

(TODO: FINISH THIS)

```
class GoogleSignIn(OAuthSignIn):
    def __init__(self):
        super(GoogleSignIn, self).__init__('google')
        self.service = OAuth1Service(
            name='google',
            consumer_key=self.consumer_id,
            consumer_secret=self.consumer_secret,
            request_token_url='TODO-FILL-THIS-IN',
            authorize_url='TODO-FILL-THIS-IN'',
            access_token_url='TODO-FILL-THIS-IN'',
            base_url='TODO-FILL-THIS-IN''
        )
```
