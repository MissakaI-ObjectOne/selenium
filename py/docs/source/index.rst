======================
Selenium Client Driver
======================

Introduction
============

Python language bindings for Selenium WebDriver.

The `selenium` package is used to automate web browser interaction from Python.

+-----------+--------------------------------------------------------------------------------------+
| **Home**: | https://selenium.dev                                                                 |
+-----------+--------------------------------------------------------------------------------------+
| **Docs**: | `selenium package API <https://seleniumhq.github.io/selenium/docs/api/py/api.html>`_ |
+-----------+--------------------------------------------------------------------------------------+
| **Dev**:  | https://github.com/SeleniumHQ/Selenium                                               |
+-----------+--------------------------------------------------------------------------------------+
| **PyPI**: | https://pypi.org/project/selenium/                                                   |
+-----------+--------------------------------------------------------------------------------------+
| **IRC**:  | **#selenium** channel on LiberaChat                                                  |
+-----------+--------------------------------------------------------------------------------------+

Several browsers/drivers are supported (Firefox, Chrome, Internet Explorer), as well as the Remote protocol.

Supported Python Versions
=========================

* Python 3.7+

Installing
==========

If you have `pip <https://pip.pypa.io/>`_ on your system, you can simply install or upgrade the Python bindings::

    pip install -U selenium

Alternately, you can download the source distribution from `PyPI <https://pypi.org/project/selenium/#files>`_ (e.g. selenium-4.1.3.tar.gz), unarchive it, and run::

    python setup.py install

Note: You may want to consider using `virtualenv <http://www.virtualenv.org/>`_ to create isolated Python environments.

Drivers
=======

Selenium requires a driver to interface with the chosen browser. Firefox,
for example, requires `geckodriver <https://github.com/mozilla/geckodriver/releases>`_, which needs to be installed before the below examples can be run. Make sure it's in your `PATH`, e. g., place it in `/usr/bin` or `/usr/local/bin`.

Failure to observe this step will give you an error `selenium.common.exceptions.WebDriverException: Message: 'geckodriver' executable needs to be in PATH.`

Other supported browsers will have their own drivers available. Links to some of the more popular browser drivers follow.

+--------------+-----------------------------------------------------------------------+
| **Chrome**:  | https://chromedriver.chromium.org/downloads                           |
+--------------+-----------------------------------------------------------------------+
| **Edge**:    | https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/ |
+--------------+-----------------------------------------------------------------------+
| **Firefox**: | https://github.com/mozilla/geckodriver/releases                       |
+--------------+-----------------------------------------------------------------------+
| **Safari**:  | https://webkit.org/blog/6900/webdriver-support-in-safari-10/          |
+--------------+-----------------------------------------------------------------------+

Example 0:
==========

* open a new Firefox browser
* load the page at the given URL

.. code-block:: python

    from selenium import webdriver

    browser = webdriver.Firefox()
    browser.get('http://selenium.dev/')

Example 1:
==========

* open a new Firefox browser
* load the Yahoo homepage
* search for "seleniumhq"
* close the browser

.. code-block:: python

    from selenium import webdriver
    from selenium.webdriver.common.by import By
    from selenium.webdriver.common.keys import Keys

    browser = webdriver.Firefox()

    browser.get('http://www.yahoo.com')
    assert 'Yahoo' in browser.title

    elem = browser.find_element(By.NAME, 'p')  # Find the search box
    elem.send_keys('seleniumhq' + Keys.RETURN)

    browser.quit()

Example 2:
==========

Selenium WebDriver is often used as a basis for testing web applications.  Here is a simple example using Python's standard `unittest <http://docs.python.org/3/library/unittest.html>`_ library:

.. code-block:: python

    import unittest
    from selenium import webdriver

    class GoogleTestCase(unittest.TestCase):

        def setUp(self):
            self.browser = webdriver.Firefox()
            self.addCleanup(self.browser.quit)

        def testPageTitle(self):
            self.browser.get('http://www.google.com')
            self.assertIn('Google', self.browser.title)

    if __name__ == '__main__':
        unittest.main(verbosity=2)

Selenium Server (optional)
==========================

For normal WebDriver scripts (non-Remote), the Java server is not needed.

However, to use Selenium Webdriver Remote or the legacy Selenium API (Selenium-RC), you need to also run the Selenium server.  The server requires a Java Runtime Environment (JRE).

Download the server separately, from: https://www.selenium.dev/downloads/

Run the server from the command line::

    java -jar selenium-server-standalone-4.0.0.jar

Then run your Python client scripts.

Use The Source Luke!
====================

View source code online:

+-----------+------------------------------------------------------+
| official: | https://github.com/SeleniumHQ/selenium/tree/trunk/py |
+-----------+------------------------------------------------------+
