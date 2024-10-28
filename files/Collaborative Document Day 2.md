![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document day 2

2024-10-23 Good practices in research software development 2024-10-22-ds-cr

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

----------------------------------------------------------------------------

This is the Document for today: https://edu.nl/yebdm

Collaborative Document day 1: https://edu.nl/y8rc9



##  🫱🏽‍🫲🏻 Code of Conduct

Participants are expected to follow these guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism. 
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.
 
## ⚖️ License

All content is publicly available under the Creative Commons Attribution License: [creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

## 🙋Getting help

To ask a question, just raise your hand.

If you need help from a helper, place a pink post-it note on your laptop lid. A helper will come to assist you as soon as possible.

## 🖥 Workshop website

[Link](https://esciencecenter-digital-skills.github.io/2024-10-22-ds-cr)


🛠 Setup

We will assume everyone can access the command line on their laptop and managed to follow these [**setup instructions**](https://esciencecenter-digital-skills.github.io/2024-10-22-ds-cr).

Please put a pink post-it note on you laptop lid, if you need a bit more help with the setup.

## 👩‍🏫👩‍💻🎓 Instructors

Olga Lyashevska, Sander van Rijn


## 🧑‍🙋 Helpers

Carlos Murilo Romero Rocha, Luisa Orozco, Claire Donnelly

## 🗓️ Agenda
* 09:30	Welcome and icebreaker
* 09:45	Writing modular code
* 10:30	Coffee break
* 10:45	Writing modular code
* 11:30	Coffee break
* 11:45	Documentation
* 12:30	Lunch Break
* 13:30	Introduction to testing
* 14:15	Coffee break
* 14:30	Introduction to Continuous Integration
* 15:15	Coffee break
* 15:30	Introduction to Continuous Integration
* 16:15	Wrap-up 
* 16:30	Drinks

## 🏢 Location logistics
* Coffee
* Toilets
* Wifi
* Emergency exit

## 🎓 Certificate of attendance
If you attend the full workshop you can request a certificate of attendance by emailing to training@esciencecenter.nl.
Please request your certificate within 8 months after the workshop, as we will delete all personal identifyable information after this period.

## Role call


## Start
- Icebreaker
- Feedback yesterday
- Questions

## ❄️ Icebreaker

Pick an animal that starts with the first letter of your name and tell us why it's totally you. For example, I'm [Name], and I pick an Octopus because I like to think I'm good at multitasking... though most days, I'm just juggling all eight arms trying to keep it together!


## 🔧 Exercises

### Modularity (20 min)

Carefully review the following code snippet:

```python
def convert_temperature(temperature, unit):
    if unit == "F":
        # Convert Fahrenheit to Celsius
        celsius = (temperature - 32) * (5 / 9)
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = celsius + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                fahrenheit = (celsius * (9 / 5)) + 32
                if fahrenheit < -459.67:
                    # Invalid temperature, below absolute zero
                    return "Invalid temperature"
                else:
                    return celsius, kelvin
    elif unit == "C":
        # Convert Celsius to Fahrenheit
        fahrenheit = (temperature * (9 / 5)) + 32
        if fahrenheit < -459.67:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = temperature + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return fahrenheit, kelvin
    elif unit == "K":
        # Convert Kelvin to Celsius
        celsius = temperature - 273.15
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Fahrenheit
            fahrenheit = (celsius * (9 / 5)) + 32
            if fahrenheit < -459.67:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return celsius, fahrenheit
    else:
        return "Invalid unit"
```




#### Possible Solution...

```python
def celsius_to_fahrenheit(celsius):
    """
    Converts a temperature from Celsius to Fahrenheit.

    Args:
        celsius (float): The temperature in Celsius.

    Returns:
        float: The temperature in Fahrenheit.
    """
    return (celsius * (9 / 5)) + 32


def fahrenheit_to_celsius(fahrenheit):
    """
    Converts a temperature from Fahrenheit to Celsius.

    Args:
        fahrenheit (float): The temperature in Fahrenheit.

    Returns:
        float: The temperature in Celsius.
    """
    return (fahrenheit - 32) * (5 / 9)


def celsius_to_kelvin(celsius):
    """
    Converts a temperature from Celsius to Kelvin.

    Args:
        celsius (float): The temperature in Celsius.

    Returns:
        float: The temperature in Kelvin.
    """
    return celsius + 273.15


def kelvin_to_celsius(kelvin):
    """
    Converts a temperature from Kelvin to Celsius.

    Args:
        kelvin (float): The temperature in Kelvin.

    Returns:
        float: The temperature in Celsius.
    """
    return kelvin - 273.15


def check_temperature_validity(temperature, unit):
    """
    Checks if a temperature is valid for a given unit.

    Args:
        temperature (float): The temperature to check.
        unit (str): The unit of the temperature. Must be "C", "F", or "K".

    Returns:
        bool: True if the temperature is valid, False otherwise.
    """
    abs_zero = {"C": -273.15, "F": -459.67, "K": 0}
    if temperature < abs_zero[unit]:
        return False
    return True


def check_unit_validity(unit):
    """
    Checks if a unit is valid.

    Args:
        unit (str): The unit to check. Must be "C", "F", or "K".

    Returns:
        bool: True if the unit is valid, False otherwise.
    """
    if not unit in ["C", "F", "K"]:
        return False
    return True


def convert_temperature(temperature, unit):
    """
    Converts a temperature from one unit to another.

    Args:
        temperature (float): The temperature to convert.
        unit (str): The unit of the temperature. Must be "C", "F", or "K".

    Returns:
        tuple: A tuple containing the converted temperature in Celsius and Kelvin units.

    Raises:
        ValueError: If the unit is not "C", "F", or "K".
        ValueError: If the temperature is below absolute zero for the given unit.

    Examples:
        >>> convert_temperature(32, "F")
        (0.0, 273.15)
        >>> convert_temperature(0, "C")
        (32.0, 273.15)
        >>> convert_temperature(273.15, "K")
        (0.0, -459.67)
    """
    if not check_unit_validity(unit):
        raise ValueError("Invalid unit")
    if not check_temperature_validity(temperature, unit):
        raise ValueError("Invalid temperature")
    if unit == "F":
        celsius = fahrenheit_to_celsius(temperature)
        kelvin = celsius_to_kelvin(celsius)
        return celsius, kelvin
    if unit == "C":
        fahrenheit = celsius_to_fahrenheit(temperature)
        kelvin = celsius_to_kelvin(temperature)
        return fahrenheit, kelvin
    if unit == "K":
        celsius = kelvin_to_celsius(temperature)
        fahrenheit = celsius_to_fahrenheit(celsius)
        return celsius, fahrenheit

if __name__ == "__main__":
    print(convert_temperature(0, "C"))
    print(convert_temperature(0, "F"))
    print(convert_temperature(0, "K"))
    print(convert_temperature(-500, "K"))
    print(convert_temperature(-500, "C"))
    print(convert_temperature(-500, "F"))
    print(convert_temperature(-500, "B"))
```

### Exercise: Think of good and bad examples
Write down your thoughts in the collaborative documents.
Respond with emojis :+1: :scream_cat: to your colleagues' answers.
- Think of projects of which you like the documentation. What do you like about them?

- Think of projects for which you don’t like the documentation. What don’t you like about them? Are you missing anything?

**NB: You can choose a mature library with lots of users for this exercise, but try to also think of less mature projects you had to collaborate on, or papers you had to reproduce.**


### Exercise README: Draft or improve a README for one of your recent projects (in breakout rooms)

Try to draft a brief README or review a README which you have written for one of your projects.

You can work individually, but you could also discuss whether anything can be improved on your neighbour's README file(s).

Think about the user (which can be a future you) of your project, what does this user need to know to use or contribute to the project? And how do you make your project attractive to use or contribute to?

(Optional): Try the https://hemingwayapp.com/ to analyse your README file and make your writing bold and clear.


### Test-Driven Development: FizzBuzz Function (15 min)

The function `fizz_buzz()` takes an integer argument and returns it, BUT:

- Fails on zero or negative numbers.
- Instead returns "Fizz" on multiples of 3.
- Instead returns "Buzz" on multiples of 5.
- Instead returns "FizzBuzz" on multiples of 3 and 5.

Create an empty function `fizz_buzz()` and go through the conditions listed above, one by one:

1. Write a test for the condition.
2. Edit the `fizz_buzz()` function until the test passes.

Then discuss together the different solutions.

Useful pytest documentation: https://docs.pytest.org/en/stable/reference/reference.html


**Solution**
```python
import pytest

def fizz_buzz(input):
    if input <= 0:
        raise ValueError('Negative or zero input not allowed')
    if input % 3 == 0 and input % 5 == 0:
        return 'FizzBuzz'
    if input % 3 == 0:
        return 'Fizz'
    if input % 5 == 0:
        return 'Buzz'
    return input

def test_fizz_buzz():
    with pytest.raises(ValueError):
        fizz_buzz(0)
    with pytest.raises(ValueError):
        fizz_buzz(-2)
    assert fizz_buzz(1) == 1
    assert fizz_buzz(3) == 'Fizz'
    assert fizz_buzz(4) == 4
    assert fizz_buzz(5) == 'Buzz'
    assert fizz_buzz(6) == 'Fizz'
    assert fizz_buzz(10) == 'Buzz'
    assert fizz_buzz(15) == 'FizzBuzz'
```

### Full-cycle collaborative workflow

~~[Collaborative CI Exercise](https://coderefinery.github.io/testing/full-cycle-ci/#exercise-a-full-cycle-collaborative-workflow)~~  (Old version)

[Collaborative CI Exercise](https://esciencecenter-digital-skills.github.io/good-practices-lesson/4-ci.html)


## 🧠 Collaborative Notes

Welcome to the 2<sup>nd</sup> day of the workshop! Today will be a great day!

### Developing modular code

#### What is modularity?
- Building software from smaller pieces. 
- We build individual parts of code that are self-contained and independent, deals with one specific task. From these components we can build complex behaviour. Small cohesive untis usually work better than one complex big thing!
- Modularity makes your code ease to understand, change, and maintain.

#### What are these elements ?
- functions
- classes
- modules
- packages
- libraries

#### Why writing modular code ?
This makes your code easier to:
- understand
- test
- maintain
- debug
- reuse
- less complex (concept of`separation of concerns`)

**Remember**: in separating you project into self-contained and cohesive units you increase its capabilities and its power!

#### What is a good module?
- A good module performs a limited, clearly definied task. It has a proper name and is readable.
- Readability is not the same as being as short as possible! By just using a function with a clear name, you make things more readable.
- A good module is 'pure', it does not have a state. This means it does not interact with the outside world except input and output. It has no side-effects.
**example**: <u>a stateful function changes its environment and interacts with external resources. This is something we always want to avoid in our code.</u>

- **impure function**: does not always give the same results. For example, it modifies the input/output quantities or append things everytime you call it, having therefore *side effects*.

- **pure function**: always gives the same result!
    
#### Indentifying opportunities for modularity?
- focus on readability: modular code is more readable. It is read more frequently than it is writen.
- "Code smell" is a polite way to say readability "stinks", but code will be read. If code is easily readable, it is understandable for you (later) and others and can be more easily extended in the future. 
- https://refactoring.guru/refactoring/smells

#### Indentify future functions
- Don't Repeat Yourself (DRY): You should not be repeating code. Anything that is repeated should be in a function instead.
- Candidates for a function can be identified by their actions (`plot`, `read`, `get`, `put`...). The naming of functions often goes by their action. Functions should be named to make the action obvious. If you see nested code, e.g. loops within loops, that is often a hint the code can be rewritten in a better way.

We will cover tests later, but each module should have a test. Tests help you identify places code can be improved. 

**Remember:**
- <u>If the test is very complex and difficult to make, it may be an good indicator that code can be improved!</u>

- <u>If you cannot test something at all, this may be an indication that the function probably can be re-written in a better way!</u>


### Documentation

Documentation is not only for others but also for yourself (for example in the future).

#### What kinds of documentation do we have?
- Web sites like in https://pages.github.com/
- Docstrings in functions (in-code documentations)
- README files
- Tutorials
- API documentation: autogenerated from your code, e.g., `doxygen`, `sphinx`

#### README files
this is the first thing a user or collaborator sees. What should be there? 
- Something covering parts or files of the project. 
- Author and contact info. Installation guide. 
- The overall purpose of the project and context. 
- Citation, licence, usage. 
- Some things can be in a readme or in additional files, but readme is a good entry point e.g. changelog, license.

##### In-code documentation

This refers to proper placement of `comments` and `docstrings`. This makes your code readable to your collaborators/co-developers.
- There can be many reasons to not write much in terms of comments. *Comments should never be used to replace version control or improper variables/function naming*.
- Docstrings are special kinds of comments. They can be used to describe the functionality of a module/function and also to generate documentation.

###### **In-code documentation: key points**
- Explicitly describing naming already provides a good docs
- Comments should describe why for your code, not the what.


##### Example on how to generate a `sphinx` documentation.

This is generally contained within a `doc` folder in your GitHub repository.

To start with, make a directory `doc`:
```bash
mkdir doc/
cd doc/
```
Run `sphinx` and follow the instructions
```bash
sphinx-quickstart
```
Edit the `index.rst` file
```bash
nano index.rst
```
Add
```bash
nano some_feature.md
```
Edit the `conf.py` file
```bash
nano conf.py
```
Add
```bash
extensions = ["myst_parser"]
```
Generate the documentation
```bash
sphinx-build . _build
```
To visualize the documentation, we can open the generated`index.html` into your browser or deploy it using [GitHub Pages](https://pages.github.com/).


### Testing

Mistakes are unavoidable!

#### Why do we need test ?
- Prevent functionality by detecting error early in the project and facilitate reproducibility
- Help users. With this, they can easily verify correct installation
- Help developers to refactor your code in the future

#### Test types
- Unit test: test only small units of your software, e.g., a function
- Integration test: test unit interaction, e.g., check the proper interaction between two modules
- .... other types of testing aiming at checking the integration of the software as a whole or that eventual new changes made do not affect other existing parts of the software

#### Test frameworks
- Python: pytest
- Java: Junit
- ...

#### How much testing is enough?
test metrics:
- lines of code
- test coverage: checks to which extent your software is being coverted by your tests.

#### Pytest
The most recommended way to test your `python` code:
- collects and runs all test functions starting with `test_`

Example of pytest for unit tests
```bash
pip install pytest
mkdir pytest-example
cd pytest-example
```
Make a file `example.py` and with `nano example.py` write the follow code:
```bash
def add(a, b)
    return a + b

def test_add()
    assert add(2,3) == 5
    assert add('space', 'ship') == 'spaceship'
```
Check the version of `pytest`
```bash
pytest --version
```
Run the test
```bash
pytest example.py
```

<u>Impure functions</u>: functions that contain one or more side effects. It mutates data outside of its lexical scope and does not predictably produce the same output for the same input; see also the definition of `stateful function` above

**Remember**
When testing:
- Use `pure` functions whenever possible.
- If testing is hard, this means that your code needs to be more modular.
- You do not have to strive for 100% test coverage.
- Testing removes the dread of refactoring.


#### Test Driven Development (TDD)

*Write first the test, and then add just enough code to make the test pass*


### Continuous Integration

#### What is continuous integration ?
Automating the integration of code changes from multiple contributors

#### What is it good for ?
- <u>Automated testing (run tests automaticaly on your GitHub repo every time you make a commit)</u>
- Linting (checks whether your code follows some code format convention)
- Security analyses
- Send messages
- Build and compiling
- Deploying (PyPi, Kubernetes, GitHub Pages)

### CI providers
- GitHub Actions
- GitLab CI
- Azure Pipelines
- Jenkins
- ...

#### Advantages of CI
- This good practice is a time-investiment with returns
- CI saves time and keeps your project clean
- You are able to check errors/mistakes early on your project

## ❓ Questions
- When do we use classes or functions while writing modular code? +1 (if the question is when to use classes and when to use functions)
- At what point do you go from testing an approach to a fully designed algorithm? I usually write “junky/chaotic” code to test an idea for 1-2 days, and the next iteration I add functions etc, then the next iteration of my analysis I make it more library (like). In a research context, often you also don’t fully know the purpose/goal of your code beforehand, and there’s some searching in regard to what you want to do.
    - In addition. How to handle documentation for code that wasn’t implemented? Only mention this in the code as an explanatory comment? E.g. we’re not doing XYZ because we tried that and it didn’t work.
- What are good practices in creating a separate test.py document and running on an entire repository/collection of .py files?
- In the continuous integration part, the action is not picked up after forking and cloning the repository, so I do not know what to fix
- How do I attain an intuition for how to structure my files? E.g., how many functions should I keep in one file before splitting it up into multiple? Should I keep my tests in a seperate file or with the respective functions being tested? Etc.
- Why is a workflow "queued"?
- In my research group, we’ve talked about a “lab journal” for coding, in which you put all kinds of thoughts and rationale about what the code is doing. This would be a separate place to keep those thoughts (e.g. today i had this problem, i solved it this way, or iv'e tried approaches XYZ to get my desired analysis result, and X worked best, YZ were abandoned). Do you think this is smart, or should all thoughts about the code be contained within version tracking, documentation and comments?

## :ear: Feedback (Morning)

### What went well?
- I realy like the exercies on modularity of the code, great way to get to know the topic. +3
- I really liked how the documentation topic built on top of the modular code section. In particular, it really helped me to see how we can use modularity of the code to replace inline documentation. The current structure of the course makes this very clear and I think it is a real strength of this workshop.
- Documentation part was a very useful explanation of many things that I had seen in practice but never had a formal explanation of. I would happily attend a separate Sphinx course if that's too much to tackle in this one
- Lots of small nuggets of wisdom shared in modularity section
- Documentation is useful and would love to see a small demonstration how we can use sphinx +1
- Documentation section with examples was very useful.
- The content was very useful. I think every code developer should take such a course before they start.
- Everything especially how to make a good doc.
- Doc section good as is, I wouldn't add an exercise here as it's quite intuitive and an exercise would take a lot of time. Nice that we know now where to follow up with Sphinx etc.
- Keeping track of time very well
- It fitted right my experience level
- I liked the exercise for modular coding
- I liked today a load, as it went more in the things "around" coding and how to manage your project well.

### What can be improved?
- The speed was a bit slow/content too easy 
    - Addition 2nd person: I liked the contents, as i was unfamiliar with formal training in this, but could have gone a bit faster i think.
- Easily accessible examples in this document of the documentation you're talking about
- I would like to have exercises with documention (e.g. using Sphinx or something similar of a small part)
- I would benefit from a hands-on example of Sphinx, but understand if there is not time for it
- Modularity section was a bit slow but still very useful. Would welcome more exercises!
- One excercise using Sphinx would have made the documentation part a bit more interactive.
- Sometimes the slides were not readable
- For me, it would be nice to go also a bit further regarding project management. Discuss not the technicalities of things, but go more into how to handle all kinds of challenges around coding, e.g. how do you decide scope, determine goals, when do you put things in what modular parts in what libraries/repositories, and when do you go from writing "crappy" test code to full-fledged documented code with unit testing etc. (Maybe share some resources about this?)


## Post-workshop survey
https://www.surveymonkey.com/r/VNB988D

## :ear: Feedback (Afternoon)
### What went well?
* Loved the content! Speed was good 
* Great explanations and tutoring (in general)
* I really liked the collaborative CI excercise!
* Now testing and CI seem like much more achievable goals

assist and guidance.
* Loved the last CI exercise because it puts lots together from yesterday and today 
* Good range of topics and excellent exercises
* Top quality teaching!

### What can be improved?
* Show a more complex example when using a separate testing file for a certain repository
* In the continuous integration exercise the forking makes the automated tests not run automatically (only after push)
* Wished there was more time to go more in depth about these topics (as opposed to the rest of all topics covered), especially writing tests for larger parts of code 
* As above, this could also be a three day course easily. Testing is life.  +1
* Day 1 can perhaps be compressed into 1 morning, and day 2 spread out a bit more, expanding on these topics. +1

## 📚 Resources

- [esciencecenter Python template](https://github.com/NLeSC/python-template)
- [type hinting cheatsheet](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)
- [Docstrings examples](https://coderefinery.github.io/documentation/in-code-documentation/#what-are-docstrings-and-how-can-they-be-useful)
- [Sphinx](https://www.sphinx-doc.org/en/master/) example:
    - [Example Repository](https://github.com/esciencecenter-digital-skills/coderefinery-documentation-example-project/tree/main)
    - [Example Documentation](https://temperature-analysis-of-excel-files.readthedocs.io/en/latest/index.html)
    - [Sphinx tutorial](https://www.sphinx-doc.org/en/master/tutorial/getting-started.html)
- [MkDocs](https://www.mkdocs.org) (Sphinx alternative)
- [Our other workshops](https://www.esciencecenter.nl/training-materials/)
    - Specifically of interest might be our "Intermediate research software development" workshop. See [schedule](https://www.esciencecenter.nl/digital-skills/) or sign up for our [(training) newsletter](https://esciencecenter.us8.list-manage.com/subscribe?u=a0a563ca342f1949246a9f92f&id=31bfc2303d)
- [How to work with us](https://www.esciencecenter.nl/collaborate-with-us/)
- Test coverage in Python: [Coverage](https://coverage.readthedocs.io/en/7.6.4/) ([Pytest plugin](https://pypi.org/project/pytest-cov/))
- [Raising errors with pytest](https://docs.pytest.org/en/stable/how-to/assert.html#assertraises)
- [Slides](https://esciencecenter-digital-skills.github.io/digital-skills-slides/)
- Property based testing in Python using [Hypothesis](https://hypothesis.readthedocs.io/en/latest/)
