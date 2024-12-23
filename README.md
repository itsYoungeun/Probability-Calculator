## Build a Probability Calculator Project

Suppose there is a hat containing 5 blue balls, 4 red balls, and 2 green balls. What is the probability that a random draw of 4 balls will contain at least 1 red ball and 2 green balls? While it would be possible to calculate the probability using advanced mathematics, an easier way is to write a program to perform a large number of experiments to estimate an approximate probability.

For this project, you will write a program to determine the approximate probability of drawing certain balls randomly from a hat.

First, create a <mark>Hat</mark> class in <mark>main.py</mark>. The class should take a variable number of arguments that specify the number of balls of each color that are in the hat. For example, a class object could be created in any of these ways:

#### Example Code
```
hat1 = Hat(yellow=3, blue=2, green=6)
hat2 = Hat(red=5, orange=4)
hat3 = Hat(red=5, orange=4, black=1, blue=0, pink=2, striped=9)
```

A hat will always be created with at least one ball. The arguments passed into the hat object upon creation should be converted to a <mark>contents</mark> instance variable. <mark>contents</mark> should be a list of strings containing one item for each ball in the hat. Each item in the list should be a color name representing a single ball of that color. For example, if your hat is <mark>{'red': 2, 'blue': 1}</mark>, <mark>contents</mark> should be <mark>['red', 'red', 'blue']</mark>.

The <mark>Hat</mark> class should have a <mark>draw</mark> method that accepts an argument indicating the number of balls to draw from the hat. This method should remove balls at random from <mark>contents</mark> and return those balls as a list of strings. The balls should not go back into the hat during the draw, similar to an urn experiment without replacement. If the number of balls to draw exceeds the available quantity, return all the balls.

Next, create an <mark>experiment</mark> function in <mark>main.py</mark> (not inside the <mark>Hat</mark> class). This function should accept the following arguments:

- <mark>hat</mark>: A hat object containing balls that should be copied inside the function.
- <Mark>expected_balls</mark>: An object indicating the exact group of balls to attempt to draw from the hat for the experiment. For example, to determine the probability of drawing 2 blue balls and 1 red ball from the hat, set <mark>expected_balls</mark> to <mark>{'blue':2, 'red':1}</mark>.
- <mark>num_balls_drawn</mark>: The number of balls to draw out of the hat in each experiment.
- <mark>num_experiments</mark>: The number of experiments to perform. (The more experiments performed, the more accurate the approximate probability will be.)

The <mark>experiment</mark> function should return a probability.

For example, if you want to determine the probability of getting at least two red balls and one green ball when you draw five balls from a hat containing six black, four red, and three green. To do this, you will perform <mark>N</mark> experiments, count how many times <mark>M</mark> you get at least two red balls and one green ball, and estimate the probability as <mark>M/N</mark>. Each experiment consists of starting with a hat containing the specified balls, drawing several balls, and checking if you got the balls you were attempting to draw.

Here is how you would call the <mark>experiment</mark> function based on the example above with 2000 experiments:

#### Example Code
```
hat = Hat(black=6, red=4, green=3)
probability = experiment(hat=hat,
                  expected_balls={'red':2,'green':1},
                  num_balls_drawn=5,
                  num_experiments=2000)
```

The output would be something like this:

#### Example Code
```
0.356
```

Since this is based on random draws, the probability will be slightly different each time the code is run.

*Hint: Consider using the modules that are already imported at the top. Do not initialize random seed within the file.*