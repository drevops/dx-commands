# DX [![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?button_hashtag=DX&text=Cross-language+commands+for+unified+developer+experience+%28%23DX%29.&url=https://integratedexperts.github.io/dx&via=integratedexperts&hashtags=developerexperience,programming)

Cross-language commands for unified developer experience (DX).    

## Why
Would it be great if any project could be built with a single command 
independently of language or a framework it is written in?

What about running tests with a single command?

How about not needing to remember countless options and arguments for commands
when doing day-to-day development tasks across several projects?
 
Well, this project has very ambitious goal to maintain and promote a unified 
vocabulary of commands that do the same thing in every project. it may be 
considered a "contract" ("interface" in OOP terms, but for humans) between 
developers working on the projects.

For example, `build` command would do anything required to build the project 
and make it available for a developer to work on; `clean` command would remove
any build artifacts; `info` would display project information in a user-friendly 
way. 

## What's next?
Depending on your language or a framework, you may create your own 
implementation of the [.ahoy.yml](https://github.com/integratedexperts/dx/blob/master/.ahoy.yml) file.

Check it out locally and run `ahoy build` to see how it works (you need to have 
Ahoy installed):

```
$ ahoy build
==> Building project
Would run pre-flight checks.
Would remove containers and all build files.
Would build and start Docker containers.
Would install project and all dependencies
Would install a site.
==> Build complete
Would find problems with current project setup.
Would print project information
```

## Existing implementations
- [DrevOps](https://drevops.com) implements these commands for Drupal development (PHP).
- Implement for your language or framework and be listed here!  

## Similar and partial implementations (that would be nice to unify)
- GovCMS (PHP, Drupal, [https://github.com/govCMS/govCMS/blob/7.x-3.x/.ahoy.yml](https://github.com/govCMS/govCMS/blob/7.x-3.x/.ahoy.yml))
- SDP (PHP, Drupal, [https://github.com/dpc-sdp/dev-tools/blob/master/.ahoy.yml](https://github.com/dpc-sdp/dev-tools/blob/master/.ahoy.yml))

## Commands

## `build`
- Single project start command.
- Calls other commands as required to do what is necessary in order to have 
  project ready to be worked on.
- Guarantees idempotent file state on rerun.

## `info`
- Display project information in user-friendly way
- Does not perform any actions such as login, cleanup etc.

## `install`
- Install project and all dependencies.

## `install-site` (for web-based projects)
- Perform application-level operations to guarantee consistent application state.
- May perform brand-new site installation or using existing site.

## `lint`
- Lint code
- May contain granular sub-commands to lint back-end and front-end code 
  separately (`lint-be` and `lint-fe`).

## `test-unit`
- Run unit tests
- Agnostic to framework
- Must run all tests if no arguments provided. 

## `test-bdd`
- Run behavioural tests
- Must run all tests if no arguments provided.

## `up`, `down`, `start`, `stop`, `logs` (for Docker-based projects) 
- `up` will build Docker images if they do not exist and will start containers.
- `down` will stop and remove containers.
- `start` will start existing or create new containers from previously built 
   images and will fail if images are not built.
- `stop` will stop containers, but will not remove any volumes.
- `logs` will show logs for all or selected services.

## `clean`
- Bring project to default state
- Remove installed dependencies  

## `update`
- Update ahoy configuration itself
- Possible to update some platform files

## `doctor`
- Identify any problems with the stack
- Offer resolution suggestions
- Run before build in pre-flight mode

## Command wrapper
[Ahoy](https://ahoy-cli.readthedocs.io/en/latest/) provides clean and simple way 
to create and maintain unified commands within a single YAML file. 

[.ahoy.yml](https://github.com/integratedexperts/dx/blob/master/.ahoy.yml) file 
in this repository is an example of the command configuration file.  

### Ahoy config
- Contain as less custom code as possible: rely on scripts or binaries that can 
  be ran without ahoy.
- Do not include environment variables into ahoy config - they should be only 
  listed in `.env` files.
- Support reading environment variables from `.env` and `.env.local` files.
- Fail ahoy command if at least one sub-command fails.
- Commands should accept parameters and options as original binaries would do 
  (i.e., `ahoy test-bdd path/to/test/file`).  
  
## Extending command list
Some projects may require specific commands that are not a part from the list 
above. You may easily extend your command list, provided that you do not break
existing command semantic described above.     

Ahoy allows to [extend](https://github.com/ahoy-cli/ahoy/wiki#importing-commands-from-other-ahoy-files)
command list in a separate command files without modifying main `.ahoy.yml` file.

## Feedback and contribution
Please feel free to provide feedback or propose to add more commands to 
the proposed list by [opening a new issue](https://github.com/integratedexperts/dx/issues/new).
