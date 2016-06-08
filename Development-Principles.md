### The 3 Keys of Development

1. Did I create a useful feature? [[Design Principles]]
2. Did I break any existing features? [Correct Code](#correct-code)
3. Is the codebase fast and easy to work with? [Clean Code](#clean-code)

### Correct Code

#### Bugs

- Bugs are more expensive to fix the later they are found in the cycle.  Finding a bug in production is more expensive than staging, than test, than local, than design.  Therefore, it's worth spending a little extra time reviewing your design to make sure you've thought of all the edge cases.  Therefore, it's worth spending a little extra time filling out your unit tests.  Therefore, it's worth spending a little extra time doing spot checks after your code has moved up the environment chain.

#### Self-testing Code

- A self-testing code suite means that with one click you can find out if your codebase is "correct" or not.
- Tests have a cost associated with them.  Sometimes this comes about because of poorly designed or written tests that are fragile (breaks when an encapsulated implementation detail is changed).  Sometimes the code or framework just doesn't lend itself to clean and easy tests.
- Each line of code has an associated risk of breakage, which needs to be taken into consideration when deciding when to write tests.
- 100% line coverage (or even branch coverage) does not mean that your application is perfect.  There are always edge cases you've never imagined.  There are always usability or feature issues that can't be formally quantified.

#### Unit Tests

- Unit tests are meant to evoke a certain style of coding (loosely coupled dependencies with clear interfaces) as well as give you confidence when refactoring code that is behind such an interface.  Think of it as a human-written version of a compile-time check.  Unit tests are not meant to catch your bugs, though they might happen to catch some, so you should not rely on unit tests to prove that your code works perfectly.  It only proves that your interface works perfectly according to the spec as defined in the unit tests.
- Unit tests, since they work in isolation, are lightning fast to run.  This allows for a faster feedback loop when errors are made.  In fact, you can even base your development loop purely on the feedback from the tests, which is where we get TDD from.

### Clean Code

#### Complexity

- How to think about "easy" vs "simple" vs "complex" [http://www.infoq.com/presentations/Simple-Made-Easy
](http://www.infoq.com/presentations/Simple-Made-Easy)Some nice analogies to think about:
    - Unit testing as guardrails while driving.
    - Complexity as juggling balls.
    - Crochet yarn vs legos.

#### Readability

- Code is meant to be read by humans.  Machines are super-fast these days, so the primary bottleneck has now become how easy it is for someone to read your code and understand it.  Many times, that person is going to be "future you".
- Get rid of code that isn't used.  It's confusing to try to figure out the impact of a function when it isn't used.  This is doubly true for non-compiled languages that can't calculate when code is used or isn't.
- Do not try to be "clever" when writing code.

#### Commenting

- Comment your code when it's not immediately obvious **what** is going on or **why** something is done.  When reading through old code, if you come upon an insight that is not immediately obvious, add a comment to save the next person who comes along the effort of having to figure it out again.

#### Technical Debt

- Technical debt will always pile up, if only because your code that was perfectly architected 6 months ago is no longer perfect for today's new requirements.  It is also incorrect to try to predict the future and build predicted future changes into your code, because you'll end up guessing wrong most of the time and just create extra work for yourself.  Instead, you should aim for good OO principles and not be afraid to change old code.  Having good unit test coverage helps take away your fear of changing the code.

#### Procedural vs Object-Oriented

- When writing procedural code vs object-oriented code, the tradeoff becomes quickness of understanding vs ease of change.  Procedural code lays out all of the variables you're interacting with in one contiguous chunk, making it perfectly clear what the code does.  However, if you need to make changes to this procedure, you are at risk of breaking everything else that happens in the procedure.  Object-oriented code has many many small objects that are talking to each other.  You only know of the object and its interface and need to dig into each object's definition to see what's actually going on.  However, this also means that you can change anything that you want behind the interface, and as long as the resulting code matches the pre-existing interface, nothing should break.

#### Inheritance vs Composition

- Inheritance is the simplest and most obvious way to organize structures.  However, if you apply inheritance incorrectly, you end up with a worse problem than you began with.  For example, "square extends rectangle" is seemingly correct at first glance but is actually an incorrect application of inheritance.  Composition on the other hand is about adding in a bunch of pluggable objects or behaviors.  This is obviously more complex and requires hooking up each of these components, but then doesn't carry the inherit risk of defining a hierarchy incorrectly.
- Use inheritance for **is-a** relationships.  Use duck types for **behaves-like-a** relationships.  Use composition for **has-a** relationships.

 
