!SLIDE transition=scrollLeft

!SLIDE transition=scrollLeft
# David Tchepak #
## davesquared.net ##
## @davetchepak ##

!SLIDE bullets incremental transition=scrollLeft
# TDD and OOO #

* (Over-enthusiastic OO)

!SLIDE center transition=scrollLeft
![JP](JeanPaulBoodhoo.jpg)

!SLIDE center transition=scrollLeft
![Argh](head_asplode.jpg)

_(src: http://www.city-data.com/forum/science-technology/331224-theoritical-quantum-mechanics-2.html)_

!SLIDE bullets transition=scrollLeft

* TDD for problem decomposition and design

!SLIDE bullets transition=scrollLeft

* Taking things too far as a learning experience

!SLIDE bullets transition=scrollLeft
#String Calculator Kata
* "" → 0
* "1" → 1
* "1,2,3" → 6
* Extra requirement: custom delimiter
* "//;\n5;6;7" → 18

!SLIDE bullets transition=scrollLeft
#Why the dodgy example?
* Lends itself perfectly to traditional TDD
* Highlights the differences in OOO style.
* Can fit into ~30 minutes.

!SLIDE bullets incremental transition=scrollLeft
#The sane approach
* Build up an implementation one test at a time
* Feed a bunch of test data through our method
* Publish kata on intraweb
* ...
* Profit?!!?!

!SLIDE code small transition=scrollLeft

    @@@ csharp
    [Test] 
    public void Takes_empty_string_and_returns_zero() {
        Assert.That(calculator.Add(""), Is.EqualTo(0));
    }
    [Test] 
    public void Takes_a_single_number_and_returns_it() {
        Assert.That(calculator.Add("2"), Is.EqualTo(2));
    }
    [Test] 
    public void Takes_two_numbers_delimited_by_commas_and_returns_the_sum() {
        Assert.That(calculator.Add("1,2"), Is.EqualTo(3));
    }
    [Test] 
    public void Takes_multiple_numbers_separated_by_commas_and_returns_the_sum() {
        Assert.That(calculator.Add("1,2,3,4,5,6,7,8,9"), Is.EqualTo(45));
    }

!SLIDE code small transition=scrollLeft

    @@@ csharp
    public int Add(string expression) {
        if (expression == "") return 0;
        var delimiters = DefaultDelimiters;
        if (HasCustomDelimiterSpecified(expression)) {
            delimiters = new[] {GetCustomDelimiter(expression)};
            expression = GetExpressionWithoutCustomDelimiterSpecification(expression);
        }
        return expression
            .Split(delimiters, StringSplitOptions.None)
            .Sum(x => int.Parse(x));
    }

!SLIDE center transition=scrollLeft
# This approach certified:
![Not insane](not_insane.jpg)
_(src: http://www.cafepress.com/+not_insane_stamp_mousepad,132701845)_

!SLIDE bullets center transition=scrollLeft
# We will not be using the sane approach

!SLIDE bullets transition=scrollLeft
# Take OO principles...
* (SOLID, LoD, encapsulation, GRASP ...)

!SLIDE center transition=scrollLeft
#...and turn them up to 11
![Up to 11](spinaltap-11.jpg)

!SLIDE bullets center transition=scrollLeft
# Over-enthusiastic SRP

* Object can do a trivial bit work 
* XOR 
* coordinate collaborators

_Not both_

!SLIDE bullets incremental transition=scrollLeft
# A different take on TDD
* Use the tests to help decompose the problem into smaller problems.
* Push the smaller problems into dependencies

!SLIDE bullets incremental transition=scrollLeft
# Scenario-based TDD
* Given a _context_
* And a _subject_ being tested
* _Because_ something happens to the _subject_
* We can _assert_ facts about a scenario

!SLIDE code small transition=scrollLeft

    @@@ csharp
    public class When_adding_two_numbers: ConcernFor<Adder> {
        [Test] 
        public void Result_is_the_sum_of_the_numbers() {...}
        
        protected override Because() {
            //We told the subject to add two numbers
            result = Subject.Add(firstNumber, secondNumber);
        }
        protected override Context() {
            //Setup the scenario
            firstNumber = 2;
            secondNumber = 3;
            expectedSum = 5;
        }
    }

!SLIDE bullets incremental transition=scrollLeft
# Not a base class; a framework for thinking

!SLIDE bullets incremental transition=scrollLeft
# _scenario name_ 
* → Responsibility plus context 

!SLIDE bullets incremental transition=scrollLeft
# _test name and assertion_ 
* → How should the SUT react?

!SLIDE bullets incremental transition=scrollLeft
# Why? 
* → _Because()_

!SLIDE bullets incremental transition=scrollLeft
# _context_
* → Sub-responsibilities
* → Push into dependencies
* → Drive out our OO design

!SLIDE bullets center transition=scrollLeft
# WARNING!
* Ridiculousness ahead.

!SLIDE transition=scrollLeft
#Let's go!#

!SLIDE transition=scrollLeft
#And we're back

!SLIDE bullets transition=scrollLeft
#Hey anonymous dude!
* That's an hour of my life I'll never get back.
* Thanks for nothing!

!SLIDE bullets transition=scrollLeft
#WAIT!!!
* Some of this is _actually_ useful for real problems!

!SLIDE bullets incremental transition=scrollLeft
# This looks SOLID...
* Classes have ONE responsibility (SRP)
* Extended behaviour (change number parsing) without major mods to classes (OCP)
* Small, focused interfaces (ISP)
* Class depend on abstractions, top-down (DIP)

!SLIDE bullets incremental transition=scrollLeft
# Flexible tests and maintainable code
* Refactor via tweaking contexts
* Trivial implementations
* Small objects and abstractions → can change big bits of behaviour 

!SLIDE bullets incremental transition=scrollLeft
# How did this happen?
* Over-enthusiastic SRP
* Focused on behaviour and problem decomposition, not data and implementation

!SLIDE bullets transition=scrollLeft
# Adding a dash of pragmatism
* Switching styles as required
* Defactoring

!SLIDE bullets incremental center transition=scrollLeft
#Take aways (fries with that?)

!SLIDE bullets incremental transition=scrollLeft
# Use TDD to help OO design
* Know and push the limits of OO (et al.)
* Tests can provide mental framework for thinking about OO
* Decompose problems → objects/classes
* Responsibility assignment
* Test logic over data; drive design over implementation

!SLIDE bullets center transition=scrollLeft
#THANKS!
* Post with code and links will be up shortly at http://davesquared.net

