Using counters hierarchically
-----------------------------
You can organize counters into hierarchies by giving them dot-separated names, e.g. ``button_clicks.homepage``. Incrementing a counter lower in a hierarchy increments all of the counters upward in the hierarchy chain. 

For example, you want to log errors that your app generates, so you create hierarchical counters for each module and function within that module. In this example, you create the following set of counters::

    errors
    errors.module
    errors.module.function

Incrementing ``errors.module.function`` by 1 increments all three counters by 1. A hierarchy can be a useful way of easily tracking actions in your app at both a cumulative and granular level.
