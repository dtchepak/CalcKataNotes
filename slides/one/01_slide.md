!SLIDE transition=scrollLeft

!SLIDE transition=scrollLeft
# David Tchepak #
## davesquared.net ##
## @davetchepak ##

!SLIDE transition=scrollLeft
# ? #

!SLIDE bullets incremental transition=scrollLeft
# TDD and OOO #

* (Over-enthusiastic OO)

!SLIDE center transition=scrollLeft
![JP](JeanPaulBoodhoo.jpg)

!SLIDE center transition=scrollLeft
![Argh](head_asplode.jpg)

_(src: http://www.city-data.com/forum/science-technology/331224-theoritical-quantum-mechanics-2.html)_

!SLIDE bullets transition=scrollLeft
# Take OO principles...

* SOLID 
* GRASP
* low coupling
* DI

!SLIDE center transition=scrollLeft
#...and turn them up to 11
![Up to 11](spinaltap-11.jpg)

!SLIDE bullets center transition=scrollLeft
# Over-enthusiastic SRP

* Object can do work 
* XOR 
* coordinate collaborators

_Not both_

!SLIDE code transition=scrollLeft
#String Calculator Kata

    @@@ csharp
    "" --> 0
    "1,2,3" --> 6
    "1\n2,3,4" --> 10
    //Extra requirement:
    "//;\n5;6;7" --> 18

!SLIDE bullets center transition=scrollLeft
#Why the dodgy example?

* Lends itself perfectly to traditional TDD
* Highlights the differences in OOO style.
* Can fit in ~30 minutes

!SLIDE transition=scrollLeft
#Let's go!#
