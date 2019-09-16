Yaml and Jinja for configuration management
===========================================

In 2013 we switched from shell scripts to fabric to do configuration management.

fabric:

> Fabric is a high level Python library designed to execute shell commands remotely over SSH, yielding useful Python objects in return:

In 2014 we switched from farbric to salt-stack

I am not happy with salt-stack

http://sotagtrends.com/?tags=[fabric,ansible,salt-stack]

.. image:: sotagtrend-fabric-ansible-saltstack.png
  :width: 200

I am unsure if configuration management with yaml and jinja is a good idea.

You can't debug it like ordinary code.

Salt swallows exceptions. This wasts my time. I am starting to hate it.

I want to move from salt to an other solution. 

Ansible seems common these days.

I love python.

If I compare python with yaml+jinja, then python wins.

Back to fabric?

Fabric does not have the state based feature: Do x, only if x was not done yet.

I like calling configuration management twice: First time a lot of things get done,
and on the second call I see something like "all states are fine, nothing was changed,
because everything was already the way it should be".

I have no clue.

Feedback is welcome.

http://sotagtrends.com/?tags=[fabric,salt-stack,ansible,python]


.. image:: sotagtrend-fabric-ansible-saltstack-python.png
  :width: 200


Question: https://softwarerecs.stackexchange.com/questions/57922/configuration-management-based-on-python Configuration management based on Python

One reason I don't like YAML: There are way to many ways to write mult-line strings. According to the up-votes a lot of other human beings have the same issue. Too many choices, too much confusion, no no-brainer. Don't blame the people, blame the context: https://stackoverflow.com/questions/3790454/in-yaml-how-do-i-break-a-string-over-multiple-lines
Yes, there are several ways to write a multi-line string in python. But it is very much simpler.


After thinking about this again, I know what I am missing: I am missing a stacktrace if somethings goes wrong.
In SaltStack all tasks which should get done are a long flat list (after sls files an jinja got evaluated). A single task can have two different relations to the previous task: I can be just the next item in a list, or it can be sub-task. This information gets lost. A stacktrace gives me a very good road map. I am missing this road map in Salt (and I guess (but don't know) other yaml and jinja based configuration management tools are the same).

2019-08-23 today it is a nightmare again. If you know the programming language python, then using SLS is way too complicated. At least for me. Up to now we use salt-stack. Maybe ansible is better. But even there I ask myself: why? A modern IDE like PyCharm is like flying. Overambitious people could say: Yes, lets's implement auto-completion and other fancy stuff for SLS files ..... but: Why? Why not keep it simple? With Python I can declare a module-level variable and import this variable whereever I want to. This somehow is possible with yaml+jinja, too, but it is not simple, not nice, not easy. Grrrrr

Example: I have a sls file foo/bar.sls. Since running all states takes too long, I would like to call only foo/bar.sls. This is possible. But one simple state from root/big.sls is needed from a different sls file. Up to now I have no clue how to do this in salt-stack. I could use "include" but this would include and **execute** all states from root/big.sls. That's not what I want. Compared to python: I want to call one method of a module, not every method of this module.


