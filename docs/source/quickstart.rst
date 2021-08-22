Quickstart
============

Installation
--------------------
You can install EV3 Code Library by first going to this link:

https://github.com/lucas00alvarado/ev3-code-library

Then you should copy all of the code in robot.py and then go back to your project and
paste it into a new file called robot.py.

Imports
-------
Then you should create a main.py, or whatever you want to call the file where
you are coding your robot and add this line at the top:

.. code-block::

    from robot import Robot

Initialize Robot Class
----------------------
The final step to set up the Robot class is to initialize it with:

.. code-block::

    robot = Robot()
However, you have to initialize the class with the ports that you have put your motors
in. An example would be something like this:

.. code-block::

    robot = Robot("OUTPUT_A", "OUTPUT_B", "INPUT_1", "INPUT_2", "INPUT_3", "INPUT_4", "OUTPUT_C", "OUTPUT_D")
To learn more about initializing the Robot class and the functions that it contains,
go to the :doc:`Robot Documentation <robot>`.