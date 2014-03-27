
An introduction to using ``normalize``
======================================

Basic Records and Properties
----------------------------

``normalize`` is built around two core concepts: records, and
properties.

To start, declare a class, based off ``Record``, and its properties:

  ::

      class Star(Record):
          hip_id = Property(isa=int, required=True)
          name = Property(isa=str)
          other_names = Property(json_name="otherNames")

Once you have done this, you can create instances in a hopefully
unsurprising way:

  ::

      

Basic Records and Properties
----------------------------

