# 99 Bottles of OOP
## https://www.sandimetz.com/99bottles

## Before starting
Had to learn some Ruby syntax. The class variable @@ as a static instance variable got me at first. Ruby is a nice language, I like that it isn't white space delimited like Python.

During the 30 minutes of coding the 99 Bottles of Beer song I paused the timer a few times to check syntax. String formatting took me a while to figure out. I think that's a reasonable compromise because I barely remembered any Ruby before starting.

The improvements I want to make to my code before reading the book are
1. Plural vs singular verse builder - use the same phrase/verse for all of them down to 1.
2. My verses method is a little gross with the .chomp("\n") at the end. Not terrible, I just couldn't figure out how to fencepost my loop correctly in Ruby.
3. It's not very object oriented. Hmmm. Don't want to make it OO for no reason.

## 1. Rediscovering Simplicity
Out of the 4 solutions *Shameless Green* is by far my favorite. It's quite close to what I came up with when I did the 30 minutes exercise at the beginning of the book.

Mostly for the same reasons as Sandi, it's simple to read and understand and with the code structured in a sane way I can see places to improve it.

Not sure if I like any of the code metrics. Happy to be convinced and looking forward to see how they are used.

## 2. Test Driving Shameless Green
> Now that the first test passes, you must decide what to test next. This next test should do the simplest, most useful thing that proves your existing code to be incorrect. 

> “As the tests get more specific, the code gets more generic.”

[Blog post on refactoring transformations](https://8thlight.com/blog/uncle-bob/2013/05/27/TheTransformationPriorityPremise.html)

Refactorings don't change behavior. That's established.
Transformations do change behavior?
According to Robert Martin they do. They move code from a specific form to  a generic one. Simpler transformations have priority. That is, simpler ones are preferred to complex/involved.

Resist DRYing out code until the correct abstractions are known. It's okay to tolerate duplication while looking for the correct abstraction.

> express the unambiguous abstractions but avoid grasping for the not-quite visible ones. 

> Duplication is useful when it supplies independent, specific examples of a general concept that you don’t yet understand.

> The problem ... is that it does not isolate a new, independent example, but instead, it duplicates one that you’ve already identified. 

A good example of intention vs implementation is the song() method is the intention. The caller wants the song. The verses(99, 0) method is the implementation. Keeping song() around provides a simple API for the most common use.

Tests need to be de-coupled from the code they are testing. Song for instance can either assert against something like verses(99, 0) or a hard coded string of the entire song. If it assert against the result of verses(99, 0) then if that method changes the song test can fail. If you assert against the hard coded string then the test will only fail when the literal output doesn't match. Much better.


## 3. Unearthing Concepts

> Conditionals breed

I like this saying. It is true that 1 conditional becomes 2, becomes 7 nested if-else.

### SOLID "O"
> The "open" principle says that you should not conflate the process of moving code around, of refactoring, with the act of adding new features. You should instead separate these two operations. When faced with a new requirement, first rearrange the existing code such that it’s open to the new feature, and once that’s complete, then add the new code.

Our Bottles class isn't open because it doesn't contain the right abstractions to add the functionality by only adding code. It requires refactoring first.

Restating above - with a caveat for tests
1. If your tests get in the way, this is **if they start to fail when you are doing true refactoring** and only changing the implementation/structure of the code, **improve the tests**
2. First I refactor or modify the code so I can implement the change by only adding code.
3. Add that code

>Flocking Rules
>1.  Select the things that are most alike.
>2.  Find the smallest difference between them.
>3.  Make the simplest change that will remove that difference.

Horizontal & Vertical refactoring
Horizontal - keep working on the same (hopefully small) bit of refactoring until it is finished.
Vertical - getting distracted and working on something else you notice while doing the first change? I'm not certain what this is yet.

### Naming things
Naming abstractions (correctly) is the key. Don't always name them after the current implementation.
```ruby
def bottles_beer(verse_number):
  # Method body
end

def drinking_container(number):
  # Method
end
```

> The general rule is that the name of a thing should be one level of abstraction higher than the thing itself.

**Use the language of the domain.** Drinking container vs unit/number

All of this is to make small, reversible changes and allow code abstractions to appear. **We are looking for the differences between similar code. Not the similarities.**

### Discipline and refactoring
This sounds like a broken record. Making one line or one spiritually one line changes requries a lot of discipline and changing of behaviour after professionally coding to "get things done" for years. I'm used to making changes in groups. 

These days I think making changes in a group is actually a slower way to work if I can get fast enough at smart, targeted, refactorings.

## 4. Practicing Horizontal Refactoring

My areas that look similar - I haven't read the following section yet.
1. The final verse in case 1, and default, can be abstracted.
2. The 3rd verse is different in those two cases.
3. The bottles of beer on the wall verse is pretty similar across all of them.

Naming the abstraction correctly is important!
Take 5 to 10 minutes with a thesaurus to come up with a name.

If you need to return the false branch of a conditional when refactoring you can you a simple parameter default. If you need to return true first the default must do that for you.

### SOLID "I" Liskov SubStitution Principle

Doing the refactoring where we use the same quantity method and do capitalization after the fact is a good example of making a small change now and not trying to create the whole abstraction all at once.

```Ruby
"No more bottles of beer on the wall, "
"#{quantity(number).capitalize()} bottles of beer on the wall, "
"#{number} #{container(number)} of beer on the wall, "
```

When calling quantity(number).to_s.capitalize(), the caller has to know the quantity(number) method doesn't always return something that can be capitalized. Making the return of quantity() consistent will eliminate this.

Between recievers and senders:
- Statically typed languages have an explicit contract
- Dynamically typed languages have an implicit contract

Only take the differences in the strings at first. Watch out for similar commas.

If you get red tests after refactoring, learn to back up to the last point of all green and then move forward with simpler steps. Don't push forward working under red tests.

## 5. Separating Responsibilities

Identifying code smells
1. Practice describing the characteristics of the code.

For the code at the start of chapter 5
1. Amount to drink and type of container is two separate methods.
2. container, quantity, action, pronoun, successor - all take the same parameter, number, and have the same shape
3. Every method except song and verses can be private. Should be private?
4. I would spit the class into Verse and Song

Methods: container, successor, pronoum, action
* all have the same shape, simple branched conditional
* take 1 parameter, number
* all of them could be private methods, are implementation details to me
* would break the class into Verse and Song classes, Song will contain Verses(start, end) as well
* the methods only care about the argument passed, not the class as a whole
* **from the book** - these are all the flocked methods

Class: Bottles
* no instance or class variables

### Squint test
Useful for checking the shape of code, super simple. I like it. I need to make sure I use an IDE or text editor with syntax highlighting and auto-formatting as much as possible.

Do not use the same parameter name or variable name to represent two different concepts, or have a single concept hidden by multiple different names. I didn't realize the difference between verse number and bottle number.

> Having multiple methods that take the same argument is a code smell. It’s important however, to recognize that here the term "same" means same concept, not identical name.

Most of my answers to the questions are the same as the book, I'll take that as a sign I'm learning.

Is it not OO enough to depend on only the argument? That makes testing very simple. I don't like the idea of depending on instance or class variables to remove an argument.

A more OO mindset
* Conditional that select the right object to create == okay
* Conditional that supplies behavior == bad

Ideally we want to pass a "smarter number" object to that method and all it does is call a method on that object. Sort of forwarding the message (method call). Using the method to disambiguate.

> Primitive Obsession as the dominant code smell. Built-in data classes like String, Integer, Array, and Hash are examples of "primitives." Primitive Obsession is when you use one of these data classes to represent a concept in your domain.

Make a distinction between domain classes and data classes.

Class names can be more concrete, method names need to be more abstract.
Golden rule of 1 level higher than what they do?
