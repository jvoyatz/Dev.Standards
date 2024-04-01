## Intro
Reviewing the code that other developers have written should be considered as an important <br>
part of someone's daily work. There are many reasons for reviewing code applied to the code base:

* New joiners need to get feedback so as to know whether the new code or the changed is consisent
and follows the patterns of the existing code base.

* Devs with less experience need to get feedback as well about the quality of the code that is written.
* Code reviews give someone the capability to share knowledge. It is easier and quicker to explain something on existing code.
* All persons that are working on the certain project ought to have the chance to know about the upcoming interests.


That means that we should consider code reviews as a process and it works better if you have a certain structure for this.
Applying a string procedure while reviewing code, by making constant checks, detailed analysis and paying the required attention, 
give a team the ability to keep high quality code and avoid introducing (future) bugs.

In the end, we all like write beautiful sophisticated code.

To begin with, what to check in code reviews:

## Description

Always start the review of a code by taking a look on the description. This 
will help you to get the big idea of the PR and have a better overview of the changes to be done.
A proper PR description should:
* give a reason about the changes
* provide a JIRA link
* contain meaningful commits
* direct the reviewer of what to expect

## Commits
Being able to quickly understand and familiriazed yourself by taking a look at the commits forming
the PR is essentially as well. Though, this is another discussion, but you can take a look [here](https://www.conventionalcommits.org/en/v1.0.0/#specification) about Conventional commits.


## Size of Changes

After being familiarized with the requested changes, the next thing that someone should check is the size of changes. 
This is crucial because as the size of changes grows, then the time needed to spend for reviewing the code grows significantly.
Consequently, it is more likely not to observe or bypass code with mistakes.


Until this point, you might have gained a good overview of what is going next.

## Static Analysis 
Firstly, you could use some static analysis tools, which gives the ability to automate 
some time-consuming tasks, such as analyze the new code and find flaws or code smells.

Some of them:
* [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html),
* [Checkstyle](https://checkstyle.sourceforge.io/),
* [FindBugs](https://findbugs.sourceforge.net/),
* [PMD](https://pmd.github.io/),
* lint tools, such as **[ktlint](https://github.com/JLLeitschuh/ktlint-gradle?tab=readme-ov-file)** can identify language specific problems,
* **[Detekt](https://github.com/detekt/detekt)** identifies code smells, it also prevents user to introduce new issues in the codebase,
* **[Konsist](https://github.com/LemonAppDev/konsist)** guards the consistency of Kotlin project and can enforce architectural rules as well
* Jacoco for test coverage,


## Manual Analysis

You should always pay attention to topics such as

* Compiler Warnings
  * those warnings appear in order to inform you that something wrong could happen
* Suppresions
* TODOs
  * makes the reviewer to think that something is missing or it is not yet done. 
* Immutability issues (always check Compose metrics)
* Nullability (avoid using assertion (!!))
* Use separated classes for DTOs and Domain models
  * changing your domain models, does not necessarily affect your repository classes
* error handling
  * always check that a wrong state is not swallowed
  * prefer wrapping your responses on state classes over throwing exceptions
* classes and functions visibility
  * prefer private or internal instead of setting them public
* documentation


On top of the above topics, it is also essential to
* check the complexity of the code
  * class or methods size, parameters count
* detect whether the code is understandable
* consistency
  * package structure
  * testing?
  * naming conventions
  * introduction of new 3rd party libs
  * new cod should follows the guidelines of the existing codebase
* performance
* maintability
  
 As for testing:
 * in case new code is introduced, then ensure that at least tests covering the basic happy and error paths are written
 * or in case something changed in an existing flow, ensure that there is a test written 
 * avoid to accept tests that are disabled
 * using libraries like Jacoco, can help us identify which blocks of code have been tested
 * prefer real tests over mocked ones
   * a dev need to read before using a mock library
   * mocking makes the tests flaky
   * can introduce false positives
   * using fake implementations is often easier and simple to use

Note that the static analysis tools referred in the previous section, can be used to help with the topics written above.


## Final Word

Tba


sources: 
[Code Review 101](https://betterprogramming.pub/code-reviews-really-503e1ea62f45)
[How to Make Good and Valuable Code Reviews](https://medium.com/@inzuael/how-to-make-good-and-valuable-code-reviews-6cf128f4b383)