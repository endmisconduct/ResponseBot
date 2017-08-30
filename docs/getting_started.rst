Getting Started
===============

Introduction
------------
A framework to quickly develop listen-and-answer twitter bots. You can define multiple actions to be executed every time a tweet arrives.

Installation
------------
.. code-block:: bash

   $ pip install responsebot

Quick start
-----------
Authenticate
~~~~~~~~~~~~

Create a :code:`.responsebot` file in your project root with your Twitter API credentials (which can be obtained after you created a Twitter application `here <https://apps.twitter.com/>`_).

.. code-block:: ini

   [auth]
   consumer_key = <consumer_key>
   consumer_secret = <consumer_secret>
   token_key = <token_key>
   token_secret = <token_secret>

Create a handler
~~~~~~~~~~~~~~~~

.. code-block:: python

   from responsebot.handlers import BaseTweetHandler, register_handler


   @register_handler
   class MyTweetHandler(BaseTweetHandler):
       def get_filter(self):
           return TweetFilter(track=['Donald Trump'], follow=['<your personal Twitter id>'])

       def on_tweet(self, tweet):
           print('Received tweet: %s from %s' % (tweet.text, tweet.user.screen_name))

Execute
~~~~~~~

.. code-block:: bash

   $ start_responsebot --handlers-package <python path to your package/module>

Test
~~~~

The bot should now receive tweets containing 'Donald Trump' or tweets posted by you. You should see ResponseBot outputs

.. code-block:: bash

   Received tweet: <your tweet content> from <your sender tweet account>

Handler
-------
For a list of methods you can define in your custom handlers, see `handler reference <reference/responsebot.handlers.base.html>`_.

Reply to tweets
---------------
You can reply to received tweets, see more in the `tutorial's client section <tutorial.html#client>`_
