# Guideline T.T. project v0.0.3

This guideline is an agreement for developing.

## Getting Started

1. NO copy-paste. One cat die if you do it!
2. NO dead-code. It's confusing for other developers.
```javascript
// let string = "JavaScript syntax highlighting";
// alert(string);
let string = "Javascript is a powerful language";
console.log(string);
```
So, Will we show it in console or alert? What is the really text? Why is comment the before one?

## Writting code

### Indentation
The standar for these projects are: 
**4 lines, a space after curly brackets.**
```java
public class User {
    static void main(String args[]){
        if() {
            ...
        } else {
            this.method();
        }
    }
}
```
### IDEs
JetBrains suite is a powerful and useful option.
### Documentation in code
```java
/**
 * This is a comment for javadoc
 * <tag> <info>
 */
```
Use the follow table to learn the comments allow.

| Tag         	| Description                                                                                                       	| Example                                              	
|-------------	|-------------------------------------------------------------------------------------------------------------------	|------------------------------------------------------	
| @author     	| Developer name, and GitHub email                                                                                  	| @author Alfonso Ríos <malforime@gmail.com>           	
| @deprecated 	| It indicates that the method or class is obsolete (own of previous versions) and that its use is not recommended. 	| @deprecated It's recommended use <other_in_place_of> 	
| @param      	| Defines a parameter of a method, is required for all parameters of the method.                                    	| @param user: Object instance of User class           	
| @return      	| Informs of what the method returns, it does not apply to constructors or "void" methods.                            	| @return isActive: Boolean flag if the user is active
| @version     	| The current version of the project v.MAJOR.MINOR.PATCH                            	                                | @version v0.0.2   Add gulp task for minify
           	
## Deployment rules

* All the business logic (unit tests) are passing 100%
* The happy path process is running with all cases
* The code is build and minify
* Only the master branch is productive

## Unit test

We are using TDD (Test Driven Development) and try to implement SOLID principles.

### SOLID

References: [SOLID for Java](http://blog.gauffin.org/2012/05/solid-principles-with-real-world-examples/)

#### Single Responsibility Principle

Example: [SRP Example for Java](http://blog.gauffin.org/2011/07/single-responsibility-prinicple/)

Single responsibility states that every class should only have one reason to change. A typical example is an user management class. When you for instance create a new user you’ll most likely send an welcome email. That’s two reasons to change: To do something with the account management and to change the emailing procedure. A better way would be to generate some kind of event from the account management class which is subscribed by a UserEmailService that does the actual email handling.

#### Open/Closed principle

Open/Closed principle says that a class should be open for extension but closed for modification. Which means that you can add new features through inheritance but should not change the existing classes (other than bug fixes).

#### Liskovs Substitution Principle

Liskovs Substitution Principle states that any method that takes class X as a parameter must be able to work with any subclasses of X.

#### Interface Segregation Principle

ISP states that interfaces that have become “fat” (like god classes) should be split into several interfaces. Large interfaces makes it harder to extend smaller parts of the system.

#### Dependency Inversion Principle

The principle which is easiest to understand. DIP states that you should let the caller create the dependencies instead of letting the class itself create the dependencies. Hence inverting the dependency control (from letting the class control them to letting the caller control them).


### Test Driven Development

References: [TDD for Java](https://technologyconversations.com/2013/12/24/test-driven-development-tdd-best-practices-using-java-examples-2/)

1. Write the test
```java
@Test
public final void whenSemicolonDelimiterIsSpecifiedThenItIsUsedToSeparateNumbers() {
    Assert.assertEquals(3+6+15, StringCalculator.add("//;n3;6;15"));
    Assert.assertEquals(0, StringCalculator.add(""));
    Assert.assertEquals(3, StringCalculator.add("3"));
    Assert.assertEquals(3+6, StringCalculator.add("3,6"));
    Assert.assertEquals(3+6+15+18+46+33, StringCalculator.add("3,6,15,18,46,33"));
    Assert.assertEquals(3+6+15, StringCalculator.add("3,6n15"));
    Assert.assertEquals(3+6+15, StringCalculator.add("//;n3;6;15"));
    Assert.assertEquals(3+1000+6, StringCalculator.add("3,1000,1001,6,1234"));
}
```
2. Run the test (there is no implementation code, test does not pass)
3. Write just enough implementation code to make the test pass
```java
public class StringCalculator {

    public static int add(final String numbers) {
        String delimiter = ",|\n";
        String numbersWithoutDelimiter = numbers;
        if (numbers.startsWith("//")) {
            int delimiterIndex = numbers.indexOf("//") + 2;
            delimiter = numbers.substring(delimiterIndex, delimiterIndex + 1);
            numbersWithoutDelimiter = numbers.substring(numbers.indexOf("\n") + 1);
        }
        return add(numbersWithoutDelimiter, delimiter);
    }

    private static int add(final String numbers, final String delimiter) {
        int returnValue = 0;
        String[] numbersArray = numbers.split(delimiter);
        List<Integer> negativeNumbers = new ArrayList<Integer>();
        for (String number : numbersArray) {
            if (!number.trim().isEmpty()) {
                int numberInt = Integer.parseInt(number.trim());
                if (numberInt < 0) {
                    negativeNumbers.add(numberInt);
                } else if (numberInt <= 1000) {
                    returnValue += numberInt;
                }
            }
        }
        if (negativeNumbers.size() > 0) {
            throw new RuntimeException("Negatives not allowed: " + negativeNumbers.toString());
        }
        return returnValue;
    }

}
```
4. Run all tests (tests pass)
5. Refactor
6. Repeat

## Versioning

* We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags).
* We use [CommitsKarmaStandar](http://karma-runner.github.io/1.0/dev/git-commit-msg.html) For naming branches and messages commits.

### Git process

1. Get the repository or clone it: `git clone/remote add <remote> <url>`
2. Sync the remotes and branches: `git fetch <remote> <banch>`
3. Get the major -> minor -> patch changes: `git pull <remote> <branch>`
4. Create a branch naming with a purpose: `git checkout -b "chore-add-jenkins"`
5. Do whatever you need to do.
6. Make the version upgrade with changes in CHANGELOG.md file.
7. Stage only the files you need to update: `git add <files>`
8. Packaging and hashing the changes: `git commit -m "message"`
9. Get the actual changes in principal (master commonly) branch: `git pull <remote> <branch>`
10. Up the changes to your branch seconday: `git push <remote> <branch>`
11. Create a release tag: `git tag -a MAJOR.MINOR.PATCH -m "Message"`
12. Up the tag created: `git push --tags`
13. Pull/Merge request for the principal branch in remote repository.

## Authors

* **Alfonso Ríos** - [Guideline for good developing practices](https://github.com/alfonsorios96/tt-practices)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* The goal in a project is the quality. This is my mission.
