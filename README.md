# Maven Parent

Common Maven parent for **granito.io** projects.

## Releasing

### Tagging

Make sure the [Maven GPG Plugin](https://maven.apache.org/plugins/maven-gpg-plugin/)
can sign the artifacts either by priming the agent:

```shell
echo test | gpg --clearsign
```

or by using the environment variable to provide the passphrase:

```shell
read -s -p "Enter your GnuPG key passphrase: " MAVEN_GPG_PASSPHRASE
export MAVEN_GPG_PASSPHRASE
```

Use [Maven Release Plugin](https://maven.apache.org/maven-release/maven-release-plugin/)
to run a trial build and tag the code.

```shell
mvn -B release:prepare -DpushChanges=false
mvn -B release:clean
git push
git push --tags
```

### Publishing

[Publish a new release in GitHub](https://github.com/granito-source/maven-parent/releases/new)
using the newly produced tag.
