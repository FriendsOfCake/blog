CRUD v4, Crud View and Search for Cake 3.0
==========================================

.. contents::
	:local:

Intro
-----

Some of you may know of `CRUD for CakePHP 2.x <https://github.com/FriendsOfCake/crud>`_,
the Friends Of Cake plugin to keep your controllers dry and create APIs fast and easy.

Over the last few months I've spend many hours porting the project to
CakePHP 3.x, improving the internal APIs and code coverage in the progress.

I'm starting to feel confident about the code base, so I think it's about time
to show it off to the world, as a alpha release.

The result so far has been very positive. The internal API cleanups have made
the code much more modular and even easier to extend in the future.

I invite you to check out the `code <https://github.com/FriendsOfCake/crud/tree/cake3>`_
and the `documentation <http://crud.readthedocs.org/en/latest>`_  - give it a spin with
the demo app.

Additionally I've created two new FriendsOfCake projects, **CRUD View** and **Search**.
Detailed information on each can be found the blog post below.

Plugin: CRUD View
-----------------

As part of the refactoring, I've rebooted the effort to make a CRUD-view project,
providing the CRUD user with a full blow admin interface when using CRUD.

The code can be found over at GitHub `FriendsOfCake/crud-view <https://github.com/friendsofcake/crud-view/tree/master>`_

CRUD view is somewhat working, but it still lacks a lot of features, documentation, tests etc.

What it does now, is more than the basic scaffolding that has been removed in CakePHP 3.0,
but the goal for the project is an flexible admin interface, build right into your
application by simply loading the Crud and Crud View plugins.

Index
^^^^^

This page contains the normal paginated list of records, and the list of tables
in the menu to the left.

It additionally features some filtering options, powered by the
`FriendsOfCake/search plugin <https://github.com/friendsofcake/search>`_

(Click on the image for larger version)

.. image:: /_static/images/05/03/posts-index-thumb.png
	:alt: posts index
	:target: /_static/images/05/03/posts-index-small.png

Index with Search
^^^^^^^^^^^^^^^^^

This page contains the normal paginated list of records, and the list of tables
in the menu to the left.

It additionally features some filtering options, powered by the
`FriendsOfCake/search plugin <https://github.com/friendsofcake/search>`_

In this case, it's filtering on the Post name as seen in the filtering form
and the URL.

(Click on the image for larger version)

.. image:: /_static/images/05/03/posts-index-search-thumb.png
	:alt: posts index search
	:target: /_static/images/05/03/posts-index-search-small.png

Add new post form
^^^^^^^^^^^^^^^^^

The default form layout when it's empty.

Note the custom checkbox and date selector

(Click on the image for larger version)

.. image:: /_static/images/05/03/posts-add-thumb.png
	:alt: posts add
	:target: /_static/images/05/03/posts-add-small.png

Add new post form (with widgets)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The default form layout when it's empty.

Note the custom checkbox and date selector, which has been expanded.

(Click on the image for larger version)

.. image:: /_static/images/05/03/posts-add-widgets-thumb.png
	:alt: posts add
	:target: /_static/images/05/03/posts-add-widgets-small.png

View post
^^^^^^^^^

Viewing a single post, with it's related data

(Click on the image for larger version)

.. image:: /_static/images/05/03/posts-view-thumb.png
	:alt: posts add
	:target: /_static/images/05/03/posts-view-small.png

Plugin: Search
--------------

While this is not a CRUD specific plugin, it's used in the CRUD-view project for
filtering, and will eventually be the backend for the **LookupAction**.

The project is in it's infancy, and can be found at `FriendsOfCake/search <https://github.com/FriendsOfCake/search>`_

The project is inspired by the cakedc/search plugin, but with a cleaner OO interface,
as well as a more flexible Cake 3 style class hierarchy for constructing filtering
on the fly.

Demo app
--------

A Cake 3 demo app with everything setup can be found at GitHub `jippi/demo-app <https://github.com/jippi/demo-app>`_

Simply follow the install instructions in the README

The future
----------

With the public release of both Crud v4, Crud View and Search, I hope that FriendsOfCake
can help play a positive role in the upcoming CakePHP 3 ecosystem.

I feel like CRUD v4 is mostly stable, and will more or less follow the release cycle
of CakePHP 3, keeping up with new features and fixes.

CRUD View is still a very young project, and I'm not at all a designer or frontend
guy, so having someone from the community step up and help there would be amazing.

Search is still very young, and I'm continuously talking with `lorenzo <https://github.com/lorenzo>`_
on how it can fit best as possible into the new Cake 3 ORM, and the style of Cake3.

The grand plan for the FriendOfCake association on github is to provide a solid
and common foundation for building CakePHP apps, allowing developers like your self
to focus on the most important, your application, not boiler plate code or repetitive
code tasks.

If you want to discuss the project and how it can be used, feel free to contact me
on Twitter `@jippi <https://twitter.com/jippi>`_ or come by the Friends Of Cake IRC
channel on FreeNode: **#FriendsOfCake**.

You should also follow `@FriendsOfCake <https://twitter.com/FriendsOfCake>`_ on twitter.


Crud v4 Changelog
-----------------

I've outlined some of the changes that has happened below.

While a lot of the internals of CRUD has changed with version 4 of CRUD, most, if
not all of the public API remains unchanged, making for a fairly smooth upgrade
path from CakePHP 2.x to CakePHP 3.x in the future if you use CRUD.

- The `documentation`_ has been completely
  rewritten, and expanded greatly. It's now based on the same sphinx setup as the CakePHP book.
  `The new documentation can be found here <http://crud.readthedocs.org/en/latest/>`_

- The code is now fully psr-4 compliant, like CakePHP 3, and assume it will be
  installed using Composer

- CRUD v4 now have same PHP version requirements as CakePHP 3: PHP 5.4 or newer.

- Most of the `CRUD Action <http://crud.readthedocs.org/en/latest/actions.html>`_ code
  has been extracted into `traits <https://github.com/FriendsOfCake/crud/tree/cake3/Traits>`_,
  so you easily can compose your own actions without having an direct
  inheritance hierarchy to the build in CRUD actions.

- Added a new CRUD action - `Lookup <https://github.com/FriendsOfCake/crud/blob/cake3/Action/LookupAction.php>`_
  which is useful for things like auto-complete widgets or anything that need
  a **find('list')** like output.

- Configuration has been streamlined, and now uses the **InstanceConfigTrait**
  included in CakePHP 3 - which was extracted from CRUD 3 in the first place.

- The old **CrudBaseObject** has been replaced with a new `ProxyTrait <https://github.com/FriendsOfCake/crud/blob/cake3/Core/ProxyTrait.php>`_.

- CRUD Actions and Listeners no longer depend on the CrudComponent to be loaded up
  front. All they need is a Controller instance, which allow for even
  more per action isolation of CRUD - and allow you to only use it where needed.

  .. code-block:: phpinline

  	public function add() {
    	   return (new \Crud\Action\AddAction($this, ['viewVar' => 'blog']))->handle();
  	}

  If the CRUD Component is needed, it will be lazy loaded the first time it's accessed
  from within the **ProxyTrait**.

- The Crud Event Subject will now be the same for the full duration of the CRUD
  request process, rather than a new one for each CRUD event emitted.
  This allow for better visibility into what events got emitted and handled during
  the request, and in what order.

- Triggering events using **_trigger()** will now return a **\\Cake\\Event\\Event**
  instead of the CRUD subject.

- Tests has been (mostly) rewritten to be full integration tests rather that
  unit tests, offering much more code coverage and less mocking, making for
  easier refactoring and addition of features in the future.

- Terms in the code has been updated to match Cake 3, e.g. model is now either
  an Entity (one row) or a Table (a collection of rows).

- The documentation is now inside the same branch as the code, it can be found
  in the **docs/** folder

- A whole lot of code has been deleted, since Cake 3 is much smarter and consistent
  when it comes to accessing the database.

- A new `CrudTestTrait <https://github.com/FriendsOfCake/crud/blob/cake3/TestSuite/Traits/CrudTestTrait.php>`_
  trait has been added to aid in testing CRUD actions and listeners, both in the
  CRUD core, but also in your own actions.

- Index Crud Action now responds to all HTTP verbs, not just GET or POST - this
  allow for easier "search-by-POST" use cases.

- View Crud Action now responds to all HTTP verbs, not just GET - this
  allow for easier usage in edge cases where you need to post to $self for some reason.

- Delete Crud Action now responds to all HTTP verbs, not just POST or DELTE - this
  allow for easier ways to delete resources.

.. author:: Christian "Jippi" Winther
.. categories:: CRUD
.. tags:: CRUD, CakePHP-3, FoC
.. comments::
