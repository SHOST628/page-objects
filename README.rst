Page Objects for Python
=======================

Page Objects are a testing pattern for websites. Page Objects model a page on
your site to provide accessors and methods for interacting with this page,
both to reduce boilerplate and provide a single place for element locators.

This project is an implementation of this pattern for Python using Selenium
webdriver. It is agnostic to test harnesses and designed to help you build up
libraries of code to test your sites.


.. image:: https://travis-ci.org/eeaston/page-objects.svg?branch=master
    :target: https://travis-ci.org/eeaston/page-objects

说明：
    原项目已经不再维护，我阅读了原项目代码，虽然只有100多行，但设计非常精妙。可惜缺少元素的等待，这将有助于定位元素的稳定性，所以，在原有项目的基础上增加的该功能。


Documentation
-------------

https://page-objects.readthedocs.org


Quick Example
-------------

    >>> from page_objects import PageObject, PageElement
    >>> from selenium import webdriver
    >>>
    >>> class LoginPage(PageObject):
            username = PageElement(id_='username')
            password = PageElement(name='password')
            login = PageElement(css='input[type="submit"]')
    >>>
    >>> driver = webdriver.PhantomJS()
    >>> driver.root_uri = "http://example.com"
    >>> page = LoginPage(driver)
    >>> page.get("/login")
    >>> page.username = 'secret'
    >>> page.password = 'squirrel'
    >>> assert page.username.text == 'secret'
    >>> page.login.click()

Time Out Example
-------------
    >>> from page_objects import PageObject, PageElement
    >>> from selenium import webdriver
    >>>
    >>> class BaiduPage(PageObject):
            search_input = PageElement(id_='kw', time_out=10)
            search_button = PageElement(id_='su', time_out=10)


Installation
------------

```
$ git clone https://github.com/defnngj/page-objects
$ cd page-objects
$ python setup.py install

```


Project History
---------------

This was originally part of the pkglib project at http://github.com/ahlmss/pkglib,
it has been forked to retain history.
