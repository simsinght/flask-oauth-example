flask-oauth-example
===================


Example code from Miguel Grinberg's "OAuth Authentication with Flask" article. http://blog.miguelgrinberg.com/post/oauth-authentication-with-flask

Forked by P. Conrad from: https://github.com/miguelgrinberg/flask-oauth-example for UCSD SPIS 2015.

# Google Example


Here are some changes that were done to make this work with Google as well as Facebook and Twitter.

In app.py, the original had this (note that these numbers are fake&mdash;each user of the OAuth API has to get their own private numbers from Facebook, Google, or Twitter, and these numbers should NOT be made public!  To be honest, these should be factored out into a configuration file that is NOT stored in github.)

```python
app.config['OAUTH_CREDENTIALS'] = {
    'facebook': {
        'id': '470154729788964',
        'secret': '010cc08bd4f51e34f3f3e684fbdea8a7'
    },
    'twitter': {
        'id': '3RzWQclolxWZIMq5LJqzRZPTl',
        'secret': 'm9TEd58DSEtRrZHpz2EjrV9AhsBRxKMo8m3kuIZj3zLwzwIimt'
    }
}
```

To add support for Google, we'd just add another item to this dictionary:

```python
app.config['OAUTH_CREDENTIALS'] = {
    'facebook': {
        'id': '470154729788964',
        'secret': '010cc08bd4f51e34f3f3e684fbdea8a7'
    },
    'twitter': {
        'id': '3RzWQclolxWZIMq5LJqzRZPTl',
        'secret': 'm9TEd58DSEtRrZHpz2EjrV9AhsBRxKMo8m3kuIZj3zLwzwIimt'
    },
     'google': {
        'id': 'fu23kv8dIMq5LJqzRZP3Rz9Tl',
        'secret': 'ZHpz2EjrtRrIZj3zLwV9AhsBRxKMo8m3kum9TEd58DSEzwIimt'
    }
}
```

In addition, if you want to do Google instead of Facebook or Twitter, you'll need to some code similar to this code for Twitter:

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
