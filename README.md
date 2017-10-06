# Guideline T.T. project v0.0.2

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

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds


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

* Hat tip to anyone who's code was used
* Inspiration
* etc
