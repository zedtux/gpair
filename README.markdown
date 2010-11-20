# Gpair - Pair programming tool for git #

gpair is a bash script that will help you to manage different identities for your commits with git (bazaar will be added soon).

## Installation ##

To install gpair, simply run:

    $ bash < <( curl http://depot.zedroot.org/gpair-install )

or do it manually:

    $ mkdir "$HOME/.gpair"
    $ cd "$HOME/.gpair"
    $ git clone git://github.com/zedtux/gpair.git .
    $ chmod +x "$PWD/install" && exec "$PWD/install"

## Usage ##

First thing to do is to define who you are:

    $ gpair whoami "Louis M. Wooten"

Now, you are ready to register your colleagues:

    $ gpair new-colleague greg="Grégoire Clanton"

And profiles:

    $ gpair new-profile durham
    This wizard will help you to create the new profile durham.
    
    Your email address will be used when working alone as the git author email address,
    and also used to define the git author email address domain name when working with someone else.
    For example:
    Given your email address is alain@example.com, when you will work alone the git author email address
    will be alain@example.com. But if you are working with greg, the git author email address will
    be dev+greg+alain@example.com
    
    What is your email address for this profile? (i.e: alain@example.com)
    louis.wooten@durhamtownhouse.com
    
    The given email address is made of several words.
    The git author email address will not be like you'll expect when working with a colleague.
    If you are working with greg, it will be dev+greg+louis.wooten@durhamtownhouse.com.
    To fix that, you should provide me now an alias.
    For example, you should use louis to set the git author email address to dev+greg+louis@durhamtownhouse.com
    
    Which alias would you like for this profile? (default: louis)
    
    
    Result:
      When working alone the git author email address will be louis.wooten@durhamtownhouse.com
      When working with greg the git author email address will be dev+greg+louis@durhamtownhouse.com
      
    Is this correct? [Yn]
    
    Your new profile has been registered with the alias durham.
    To use it: `gpair alone for durham` or `gpair with greg for durham`.

To get more help:

    $ gpair help

And to see some usage examples:

    $ gpair usage

## A day with gpair ##

    In order to work for different projects, companies, or at home
    As a developer
    I want to use gpair to change vcs configuration.
    Given my name is "Louis M. Wooten"
    And the following profiles exist:
      | alias  | email address                    |
      | github | louis.wooten@hmail.com           |
      | durham | louis.wooten@durhamtownhouse.com |
      | home   | louis.wooten@wooten.com          |
    And the following colleague exists:
      | alias | greg             |
      | name  | Grégoire Clanton |

#### Morning ####

Before to start to work, I'm going to update a file in a Github repository:

    $ gpair alone for github

Then I will commit my changed file with:

* git author name: Louis M. Wooten
* git author email: louis.wooten@hmail.com
* git committer name: Louis M. Wooten
* git committer email: louis.wooten@hmail.com

##### Working time start #####

My colleague Grégoire Clanton joined me and we start to work together on a new feature for the project of our company DurhamTownhouse:

    $  gpair with greg for durham

Now, my vcs configuration have changed to:

* git author name: Louis M. Wooten and Grégoire Clanton
* git author email: dev+greg+louis@durhamtownhouse.com
* git committer name: Louis M. Wooten
* git committer email: louis.wooten@durhamtownhouse.com

#### Afternoon ####

After a lot of work in the morning, I'm working alone on a bugfix:

    $ gpair alone for durham

My vcs configuration have changed to:

* git author name: Louis M. Wooten
* git author email: louis.wooten@durhamtownhouse.com
* git committer name: Louis M. Wooten
* git committer email: louis.wooten@durhamtownhouse.com

#### Evening ####

Finally I'm now at home, and I'm making some funny stuff into my personal git repository hosted on my own server:

    $ gpair alone for home

VCS configuration have changed to:

* git author name: Louis M. Wooten
* git author email: louis.wooten@wooten.com
* git committer name: Louis M. Wooten
* git committer email: louis.wooten@wooten.com

## Todo ##

* Implement use of .gpairrc files into project's folder to set automatically the gpair configuration
* Do not override the git configuration file (.git/config) from the project's folder if exists
* Implement email address format definition per profile (Change the default one 'dev+...+...@.....' to something else)
* Edit, delete profile or colleague.

## License

gpair is licensed under the GPLv3 License.