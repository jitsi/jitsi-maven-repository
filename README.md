Jitsi Maven Repository

Bellow is a basic script that describes the basic workflow of deploying a module
and updating the Jitsi Maven Repository.

```sh
# We use the packet-logging module as an example. Change accordingly.
MODULE_NAME=jitsi-packetlogging
MODULE_HOME=$HOME/src/jitsi/jitsi/m2/$MODULE_NAME
REPO_HOME=$HOME/src/jitsi/jitsi-maven-repository

# Deploy the module.
cd $MODULE_HOME/
mvn deploy -DaltDeploymentRepository=jmrs::default::file://$REPO_HOME/snapshots

# Update the maven repository.
cd $REPO_HOME/
git pull -r origin master
git add snapshots/
git commit -m "Updates $MODULE_NAME."
git push origin master
```
