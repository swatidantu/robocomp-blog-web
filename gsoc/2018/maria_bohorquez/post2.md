# First Two Weeks

For questions or help for GSoC students, contact me at gabriellabohorquez@gmail.com or robocomp.team@gmail.com  

## Working on [ReadTheDocs](https://robocomp.readthedocs.io/en/latest/) 

- https://robocomp.readthedocs.io/en/latest/ not pointing to the correct direction as reported on [this](https://github.com/robocomp/robocomp/issues/70) issue was fixed. It needed to be changed from the ReadTheDocs dashboard settings, instead of the configuration file in the repository.

- Documentation was updated to match the improved Readme.md from the `highlyunstable` branch of the repository.

- A new email robocomp.team@gmail.com was created to receive suggestions for features and tutorials.


## Why are builds being reported as failed by Travis?

*This is a copy from the Issue I reported [here](https://github.com/robocomp/robocomp/issues/153)*.

Currently Travis is failing with this error ([build](https://travis-ci.org/robocomp/robocomp/builds/380002807?utm_source=github_status&utm_medium=notification)):

```bash
apt-get install failed
$ cat ~/apt-get-update.log
Reading package lists...
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```

The error appears to be with running the build in the Xenial distro, as explained [here](https://github.com/travis-ci/travis-ci/issues/9080). But changing Xenial to the Trusty distro damages the build, as libccd and libccd-dev are only included in Xenial ([build when tested](https://travis-ci.org/robocomp/robocomp/builds/384302033?utm_source=github_status)).

The ROS community already encountered this error previously [[1](https://github.com/ros/rosdistro/issues/16175)]. They removed the code that required libccd-dev, as it was only needed in a fcl catkin.

There was an Issue already opened about this bug in the Travis repository [[2](https://github.com/travis-ci/travis-ci/issues/9080)]. Until the Xenial image gets more stable it appears the check will fail __intermittently__.

One *possible* solution would be to manually remove the lock in the Travis script:

```bash
sudo rm /var/lib/apt/lists/lock
```

## Added Contributing and Code of Conduct files

- [Contributing.md](https://github.com/robocomp/robocomp/blob/highlyunstable/CONTRIBUTING.md) was made for reference to new contributors. It explains how to fork the repository, report an issue and tips for working on Robocomp. Inspiration was taken in part from the [Node.js](https://github.com/nodejs/node/blob/master/CONTRIBUTING.md) contributing page. 

- [CODE_OF_CONDUCT.md](https://github.com/robocomp/robocomp/blob/highlyunstable/CODE_OF_CONDUCT.md) was created, taking the [Contributor Convenant](https://www.contributor-covenant.org/) as reference. Having a Code of Conduct is important, at it formally establishes that intolerance and disrespect will be unacceptable.





