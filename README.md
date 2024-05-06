# DX [![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?button_hashtag=DX&text=Cross-language+commands+for+unified+developer+experience+%28%23DX%29.&url=https://integratedexperts.github.io/dx&via=integratedexperts&hashtags=developerexperience,programming)

Cross-language commands for unified developer experience.

The DX initiative aims to standardize development commands across various
programming languages and framework, ensuring uniform commands for everyday
tasks.

It establishes a "contract" for developers, ensuring that commands like `build`,
`reset`, and `info` consistently perform the same functions in every project.

## Commands

| Command     | Short description                                                    |
|-------------|----------------------------------------------------------------------|
| `build`     | Build or rebuild the project                                         |
| `assemble`  | Assemble a codebase using project code and all required dependencies | 
| `provision` | Provision application within assembled codebase                      |
| `info`      | Display project information                                          |
| `lint`      | Check coding standards for violations                                |
| `lint-fix`  | Fix violations in coding standards                                   |
| `test`      | Run tests                                                            |
| `reset`     | Reset project to the default state                                   |
| `start`     | Start development environment                                        | 
| `stop`      | Stop development environment                                         |
| `logs`      | Show logs                                                            |
| `doctor`    | Identify issues and offer resolutions for a stack                    |
| `update`    | Update project files and tooling                                     |

## Command wrapper

The commands are usually implemented as a command wrapper using a shell script,
package configuration (e.g., `package.json` or `composer.json`), or a task
runner
[Makefile](https://www.gnu.org/software/make/), [Ahoy](https://ahoy-cli.readthedocs.io/en/latest/),
or [Task](https://github.com/go-task/task).

## Example

The example implementation of the commands is available in the 
[.ahoy.yml](https://github.com/drevops/dx/blob/master/.ahoy.yml) file.

Check it out locally and run `ahoy build` to see how it works (you need to have
[Ahoy](https://ahoy-cli.readthedocs.io/en/latest/) installed):

```bash
$ ahoy build
[INFO] Building project
Would run pre-flight checks.
>> All containers and build files will be removed. Proceed? [y/N] y
Would remove containers and all build files.
Would build and start Docker containers.
Would assemble project and all dependencies.
Would run provision operations.
Would find problems with current project setup.
Would print project information
[INFO] Build complete
```

## Existing implementations

- [DrevOps Scaffold](https://github.com/drevops/scaffold) implements these
  commands for Drupal consumer site development
- [Drupal extension scaffold](https://github.com/AlexSkrypnyk/drupal_extension_scaffold) implements these commands for Drupal
  extensions development
- [Scaffold](https://github.com/AlexSkrypnyk/scaffold) implements these commands for Shell, PHP, and Node.js projects.

## Similar and partial implementations

- [GovCMS (PHP, Drupal)](https://github.com/govCMS/GovCMS/blob/3.x-develop/.ahoy.yml)
- [SDP (PHP, Drupal)](https://github.com/dpc-sdp/dev-tools/blob/master/.ahoy.yml)

## Feedback and contribution

Please feel free to provide feedback or propose to add more commands to
the proposed list by [opening a new issue](https://github.com/drevops/dx/issues/new).
