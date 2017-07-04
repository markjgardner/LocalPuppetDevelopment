# Test project for Puppet CI/CD
I'm using this project as PoC to prove out a model for CI/CD developing puppet.

## Develop
During development, developers will use local VMs (vagrant + docker) to validate their changes. Puppet environments will not be managed by git repository branches (see notes in [Release](#release). Once the feature development is complete, changes can be submitted to the master branch via a pull request.

## Build
During the build phase the puppet code will be:
* linted
* compiled (syntax validated)
* unit tested (rspec)

## Release
During the release phase the puppet code will be pushed to the puppet master. Each environment in the release definition will push the code to a different pre-defined environment on the puppet master. Release phases will traverse the following environments and execute the following activities in each:

  ### Test
  * integration testing

  ### Prod
  * smoke testing

## Run
Once promoted to the production environment, the puppet code will be managed by the PE master and a separate hiera backend (not in the git repo).

# How to use this repo
Start the puppet master by running ```docker-compose up```.  
Once the puppet master is up and available you can launch your test agent by running ```vagrant up``` from another console.  
Vagrant will launch a vm pre-loaded with the PE agent and provision it using the master running in docker.  