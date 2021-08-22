Robot
=====

Robot
-----

.. code-block::

    __init__(left_motor_port, right_motor_port, left_sensor_port=None, right_sensor_port=None, back_sensor_port=None, gyro_sensor_port=None, motor1_port=None, motor2_port=None)

A class that contains all of the functions that the ev3 should need to use. It has functionality for line followers,
gyro sensor programs, driving, and more. Also contains all of the sensor and motor objects so that all of it only needs
to be initialized once when the Robot class is initialized. Some of the methods inside of this class will only work if
you have passed in the ports for all of the sensors and motors.
        :left_motor_port: port for the left driving motor. Values: OUTPUT_A, OUTPUT_B, OUTPUT_C, OUTPUT_D
        :right_motor_port: port for the right driving motor. Values: OUTPUT_A, OUTPUT_B, OUTPUT_C, OUTPUT_D
        :left_sensor_port: port for the left color sensor. Values: INPUT_1, INPUT_2, INPUT_3, INPUT_4
        :right_sensor_port: port for the right color sensor. Values: INPUT_1, INPUT_2, INPUT_3, INPUT_4
        :back_sensor_port: port for the back color sensor. Values: INPUT_1, INPUT_2, INPUT_3, INPUT_4
        :gyro_sensor_port: port for the gyro sensor. Values: INPUT_1, INPUT_2, INPUT_3, INPUT_4
        :motor1_port: port for one of the attachment motors. Values: OUTPUT_A, OUTPUT_B, OUTPUT_C, OUTPUT_D
        :motor2_port: port for one of the attachment motors. Values: OUTPUT_A, OUTPUT_B, OUTPUT_C, OUTPUT_D

follow_until_black
------------------

.. code-block::

    follow_until_black(self, color_sensor: ColorSensor, stop_sensor: ColorSensor, speed, rli, kp, ki=0, kd=0)

Allows you to follow a line until the other color sensor hits black.
You have to use negative PID values if you are line following on the left side of a line
        :color_sensor: the color sensor object that you would like to follow the line
        :stop_sensor: the color sensor object to detect black
        :speed: speed for line following. Use a negative value to go backwards
        :rli: the rli that you would like for the robot to try to stay on. Go to https://docs.google.com/document/d/1oJ3-Bsqdp4RnKgrdCS8U93gZ9PlmqChw0xg6aUa2zJY/edit?usp=sharing to learn more.
        :kp: sharpness of corrections in the line follower.
        :ki: makes sure that your corrections keep you on a straight line. DON'T USE WITH TURNS
        :kd: keeps your turning from continuing to swing back and forth

follow_until_white
------------------

.. code-block::

    follow_until_white(self, color_sensor: ColorSensor, stop_sensor: ColorSensor, speed, rli, kp, ki=0, kd=0)

Allows you to follow a line until the other color sensor hits white.
You have to use negative PID values if you are line following on the left side of a line
        :color_sensor: the color sensor object that you would like to follow the line
        :stop_sensor: the color sensor object to detect white
        :speed: speed for line following. Use a negative value to go backwards
        :rli: the rli that you would like for the robot to try to stay on. Go to https://docs.google.com/document/d/1oJ3-Bsqdp4RnKgrdCS8U93gZ9PlmqChw0xg6aUa2zJY/edit?usp=sharing to learn more.
        :kp: sharpness of corrections in the line follower.
        :ki: makes sure that your corrections keep you on a straight line. DON'T USE WITH TURNS
        :kd: keeps your turning from continuing to swing back and forth

single_follow_distance
----------------------

.. code-block::

    single_follow_distance(self, color_sensor: ColorSensor, speed, distance, rli, kp, ki=0, kd=0)

Allows you to follow a line with 1 color sensor for a distance. You have to use negative PID values if you are line following on the left side of a line

        :color_sensor: the color sensor object that you would like to follow the line
        :speed: speed for line following. Use a negative value to go backwards
        :distance: distance to line follow for in rotations. Use a negative value to go backwards
        :rli: the rli that you would like for the robot to try to stay on. Go to https://docs.google.com/document/d/1oJ3-Bsqdp4RnKgrdCS8U93gZ9PlmqChw0xg6aUa2zJY/edit?usp=sharing to learn more
        :kp: sharpness of corrections in the line follower
        :ki: makes sure that your corrections keep you on a straight line. DON'T USE WITH TURNS
        :kd: keeps your turning from continuing to swing back and forth

double_follow_distance
----------------------

.. code-block::

    double_follow_distance(self, speed, distance, kp, ki=0, kd=0)

Allows you to follow a line with 2 color sensors for a distance

        :speed: speed for line following
        :distance: distance to line follow for in rotations
        :kp: sharpness of corrections in the line follower
        :ki: makes sure that your corrections keep you on a straight line. DON'T USE WITH TURNS
        :kd: keeps your turning from continuing to swing back and forth

gyro_straight
-------------

.. code-block::

    gyro_straight(self, speed, distance, kp, ki=0, kd=0, angle=0)

Allows you to drive in a straight line using a gyro sensor. You have to use negative PID values if going backwards.
You should also reset your gyro sensor with the command robot.gyro_sensor.reset() unless you want to follow a previous
reset.
        :speed: speed for driving. Use a negative value to go backwards
        :distance: distance to drive for in rotations. Use a negative value to go backwards
        :kp: sharpness of corrections in your driving
        :ki: makes sure that your corrections keep you on a straight line
        :kd: keeps your turning from continuing to swing back and forth
        :angle: the gyro sensor angle that you want to follow the line at

gyro_turn
---------

.. code-block::

    gyro_turn(self, angle, left_speed, right_speed, buffer=2)

Allows you to turn a specific angle using the gyro sensor. You should reset your gyro sensor with the command
robot.gyro_sensor.reset() unless you want to turn using a previous reset
        :angle: gyro angle to turn to. Use a negative value if turning counter-clockwise
        :left_speed: the speed that the left wheel should drive at during the turn
        :right_speed: the speed that the right wheel should drive at during the turn
        :buffer: the amount of buffer in degrees that it can be on either side of the angle

square_line
-----------

.. code-block::

    square_line(self, speed)

Allows the robot to square up on a black line so that the color sensors are parallel to the line

        :speed: the speed to drive at during the square up

stop_on_color
-------------

.. code-block::

    stop_on_color(self, color_name, left_speed, right_speed, single_sensor=False, sensor=None)

Allows you to have the robot drive and then stop on a certain color

        :color_name: the color to stop on. Values: No color, Black, Blue, Green, Yellow, Red, White, and Brown
        :left_speed: the speed that the left wheel should drive at
        :right_speed: the speed that the right wheel should drive at
        :single_sensor: whether it should be waiting for a specific sensor or for one of the front two
        :sensor: the sensor to wait for if single_sensor is True

