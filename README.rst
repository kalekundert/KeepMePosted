KeepMePosted Documentation
==========================
This module provides an object-oriented event handling framework.  In this 
framework, events are registered by classes and then broadcasted by individual 
objects.  Listening for events from specific objects is made easy.

Installation
------------
KeepMePosted can be installed from PyPI::

    $ pip install kemepo

You can also download the source code directly from GitHub.  The code is made 
available under the MIT license.  If you find the code useful and want to make 
improvements, feel free to make pull requests::

    $ git clone https://github.com/kalekundert/KeepMePosted.git kemepo

Simple Example
--------------
The most important parts of this framework are the Dispatcher class and the 
event() decorator.  Dispatcher is a base class for objects that want to 
broadcast events and the event decorator is used to register events.

>>> from kemepo import Dispatcher, event
>>> class Button (Dispatcher):
        @event
        def on_press(self):
            print('Calling internal handler')

The method decorated by event() is taken to be the "internal handler", distinct 
from any "external observers" that may be attached using connect() later on.  
When an event is triggered using handle(), the internal handler is called 
before the external observers.  

>>> button = Button()
>>> button.connect(on_press=lambda: print('Calling external observer.'))
>>> button.handle('on_press')
Calling internal handler.
Calling external observer.

Complete Documentation
----------------------
The complete documentation for this module is hosted by ReadTheDocs_.

.. _ReadTheDocs: http://keepmeposted.readthedocs.org/en/latest/

