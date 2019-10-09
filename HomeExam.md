# Setup Instructions

## WSL Specific

Start WSL (Ubuntu) on Windows or the Docker container on Mac
Inside WSL run this command
~~~~
git config --global core.autocrlf input
~~~~

## Everyone

Click the link :
~~~~
<Add link>
~~~~
* This make a private repo for you

* Check out this repo using CLion

* Startup dialog > Checkout from source control > Git > Log into GitHub

* Paste in the GitHub link to the project that was created for you

* Click *clone*

* Say yes to opening the project

* Check that the toolchain works in Settings > Toolchain

* In Settings > CMake change the one that is there to point to your toolchain and make sure it's called 'Debug'

* __Write your name and student id in the README.md__

* *Commit and push.* This can be done inside CLion

* Build everything

* Run the tests

* __Read the README.md__

*In side the test files - there is a test_0 which is a dummy test
Comment it out or use it to write a test of your own.*

## Look at the project directory inside WSL/Docker

Look at CLion when it builds and you can see where it has your code.

### WSL

Look at the directory inside WSL

### Docker

Look at the directory inside Docker, by ssh'ing into the container

~~~~
ssh root@localhost -p 2222
~~~~
