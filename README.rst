Yaml and Jinja for configuration management
===========================================

In 2013 we switched from shell scripts to fabric to do configuration management.

fabric:

> Fabric is a high level Python library designed to execute shell commands remotely over SSH, yielding useful Python objects in return:

In 2014 we switched from farbric to salt-stack

I am not happy with salt. 

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
