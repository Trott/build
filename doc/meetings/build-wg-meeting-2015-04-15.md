# io.js Build WG Meeting 2015-05-14

## Links

**Public YouTube feed**: http://www.youtube.com/watch?v=8dxkM9vHmrY

## Minutes

### Present

* Johan Bergström (@jbergstroem)
* Rod Vagg (@rvagg)

### Build Respources

This is documented here: https://github.com/nodejs/build/issues/77

* Most are Linux machines running on DigitalOcean + Jenkins + iojs.org
* RackSpace does all the Windows stuff (7 servers)
* Voxer does all the FreeBSD (2 servers) and Mac stuff (2 Mac Mini)
* Joyent does SmartOS testing (2 zones)
  * Currently no Solaris or SmartOS build (test only)
* Scaleway (Online Labs) ARMv7 builds (5 servers)
* Lenaro ARMv8 builds (1 server)
* NodeSource RaspberryPies ARMv6 + ARMv7 (2 + 1 machines)

### Automation

* Started to do some automation on GitHub Pull Requests
* Some more scripted setups are comming for for Raspberry Pi

### Activity summary

* How do we provide high scalability for iojs.org?
* When should old nighlies be deleted?
* iojs.org should have Google Analytics tracking

### Leggacy builds

* The lowest GCC version we can build on CentOS 5
* ARMv7 builds does not work on the Raspberry Pi since it build on Ubuntu 14.04
* Debian Weezy with GCC 4.8 should work for most
* Another option is the fully static flag for the io.js configure which bundles
  some of the GCC with the binary. Will result in a larger binary size.

### Test Timeouts

* Some cases with SmartOS, FreeBSD, and Windows where tests times out
* Collaborators should have access to the test machines to debug
* Mittigating by grouing into os-centrig teams
* It should be easier for people to reproduce failing tests
* Too few core developers care enough about the Windows stuff
* Can give more access to build / test machines – but only the required people
  should have access to the release machines
* Provide local VMs which is used by the the Jenkins bots to reproduce test
  failures

**Action Items:**

* @rvagg: Look at the Windows disk image situation on RackSpace
* @jbergstroem: Document how to get access to test-hardware. This could be a
  part of the collaborators guide on io.js

### Improved Testing

* NodeJS started making some tests as flakey?
* Should we pull in libuv tests?
* Should we pull in v8 tests?

**Action Items:**

* @rvagg: Continue to work with automation of Pull Request and feedback

### Configure Scripts

* Build WG to take on ownership of the io.js configure scripts in core

**Action Items:**

* @ravagg: To document this in the Build WG Governance document

### Shared libraries permutation

* io.js / node.js builds on shared representation of the bundled libraries
* Tests does not take into concideration running on newer shared libraries
* Build WG should uphold the quality of the shared libraries
* Maybe split testing between automtated Pull Request feedback and master build
  testing which can take more permutations of shared libraries and maybe also
  performance testing
* Care more about about internalization, and shared libraries libuv, openssl,
  http parser, zlib
* Have a build slave with all the different libarries as shared libraries

### Alpine Linunx and Docker

* Docker subgroup has been talking about making releases with Alpine Linux
* Tangent trust between the Build and the Docker WGs since Docker WG is
  representing the Build WG
