
======================================
the scope and purpose of ``normalize``
======================================

What's in a name?
-----------------

It is called "normalize", because what you do with it is akin to the
first normal form of relational database modelling.

"**What's the first normal form?**", I hear the sane among you ask.

This is the simplest and most straightforward level which defines what
are normally called "records" (or *rows*).

A record is a defined collection of properties/attributes (*columns*),
where you know roughly what to expect in each property/attribute, and
can access them by some kind of descriptor (i.e., the attribute name).

So, this is why I chose ``Record`` as the name for the base class, but
python already has a name for its attributes, so those are simply
``Property``.

What's wrong with ``collections.namedtuple``?
---------------------------------------------

The main answer is type information, which enables more
meta-programming.

You can (but don't have to) declare what type to expect inside each
property that you declare.  This capability, along with *property
traits*, leads to the ability to, for instance, interpret a data
structure and match it against expected types.  This process is
similar to validation, but it turns out that validation as well as a
number of common operations performed on data structures are all types
of *visitor* functions.

Now, to be fair, a lot of this is already possible in Python.  Python
already ships with a good amount of metaclass framework built in.  The
``type()`` keyword is great.  However, certain classes of visitor
functions want to be able to get this from classes without an actual
instance to inspect.

So, what is ``normalize``, really?
----------------------------------

It's a general purpose declarative class builder and meta-programming
framework, which just happens to ship with JSON marshalling.

Meta-programming frameworks might not be needed for every problem, but
they crop up all over the place: validation libraries, database
mappings & ORM's, API definitions and implementations, etc.
It would be nice if they could all use the same definition and
mappings could be built out separately.

To enable this, this library's guiding principle is that base class
and metaclasses should be as clean as possible.
No ``to_json`` on all objects unless you specifically inherit from
the ``JsonRecord`` class, for instance.

But the ``to_json`` function which it does ship with uses the
visitor/meta-programming API, such that it can even work on classes
that don't inherit ``JsonRecord``.

What about higher normalization forms?  3NF etc?
------------------------------------------------

While there is some notion of primary keys in the module, mainly for
the purposes of recognizing objects in collections for comparison,
higher levels of normalization are an exercise left to the
implementer.
