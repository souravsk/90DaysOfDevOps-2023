# Container Image Scanning

A container image consists of an image manifest, a filesystem and an image configuration. [1](https://opencontainers.org/about/overview/)

For example, the filesystem of a container image for a Java application will have a Linux filesystem, the JVM, and the JAR/WAR file that represents our application.

If we are working with containers, an important part of our CI/CD pipeline should be the process of scanning these containers for known vulnerabilities. This can give us valuable information about the number of vulnerabilities we have inside our containers and can help us prevent deploying vulnerable applications to our production environment, and being hacked because of these vulnerabilities.

Let's take for example the [Log4Shell](https://en.wikipedia.org/wiki/Log4Shell) vulnerability that was discovered in late 2021. Without going into too much detail, having this vulnerability in your application means that an attacker can execute arbitrary code on your servers. It was made worse by the fact that this vulnerability is inside one of the most popular Java libraries - [Log4j](https://logging.apache.org/log4j/2.x/). Pretty bad!

So how can we know if we are vulnerable?

The answer is **Image Scanning**.

The image scanning process consists of looking inside the container, getting the list of installed packages (that could be Linux packages, but also Java, Go, JavaScript packages, etc.), cross-referencing the package list against a database of known vulnerabilities for each package, and in the end producing a list of vulnerabilities for the given container image.

There are many open-source and proprietary image scanners, that you can install and start scanning your container images right away, either locally of your machine or in your CI/CD pipeline. Two of the most popular ones are [Trivy](https://github.com/aquasecurity/trivy) and [Grype](https://github.com/anchore/grype). Some proprietary ones are [Snyk](https://docs.snyk.io/products/snyk-container/snyk-cli-for-container-security) (requires an account, has a free tier) and [VMware Carbon Black](https://carbonblack.vmware.com/resource/carbon-black-cloud-container-security-faq#overview) (requires an account, no free tier).

Scanning a container image is as simple as installing one of these and running:
```
$ grype ubuntu:latest
 ✔ Vulnerability DB        [updated]
 ✔ Pulled image
 ✔ Loaded image
 ✔ Parsed image
 ✔ Cataloged packages      [101 packages]
 ✔ Scanned image           [16 vulnerabilities]
NAME          INSTALLED                 FIXED-IN  TYPE  VULNERABILITY   SEVERITY
bash          5.1-6ubuntu1                        deb   CVE-2022-3715   Medium
coreutils     8.32-4.1ubuntu1                     deb   CVE-2016-2781   Low
gpgv          2.2.27-3ubuntu2.1                   deb   CVE-2022-3219   Low
libc-bin      2.35-0ubuntu3.1                     deb   CVE-2016-20013  Negligible
libc6         2.35-0ubuntu3.1                     deb   CVE-2016-20013  Negligible
libncurses6   6.3-2                               deb   CVE-2022-29458  Negligible
libncursesw6  6.3-2                               deb   CVE-2022-29458  Negligible
libpcre3      2:8.39-13ubuntu0.22.04.1            deb   CVE-2017-11164  Negligible
libsystemd0   249.11-0ubuntu3.6                   deb   CVE-2022-3821   Medium
libtinfo6     6.3-2                               deb   CVE-2022-29458  Negligible
libudev1      249.11-0ubuntu3.6                   deb   CVE-2022-3821   Medium
login         1:4.8.1-2ubuntu2                    deb   CVE-2013-4235   Low
ncurses-base  6.3-2                               deb   CVE-2022-29458  Negligible
ncurses-bin   6.3-2                               deb   CVE-2022-29458  Negligible
passwd        1:4.8.1-2ubuntu2                    deb   CVE-2013-4235   Low
zlib1g        1:1.2.11.dfsg-2ubuntu9.2            deb   CVE-2022-42800  Medium
```

With this command we scanned the `ubuntu:latest` container image and found that it has 16 vulnerabilities.

Each vulnerability has a severity, based on its [CVSS](https://nvd.nist.gov/vuln-metrics/cvss) score. Severities vary from `Low` to `Critical`.

16 vulnerabilities may seem a lot, but notice that none of them has a `Critical` severity.

We also see that the `FIXED-IN` column of the results table is empty. This means that none of the vulnerabilities is fixed in newer versions of its package.

This is expected because `ubuntu:latest` is the latest version of the official container image for Ubuntu. Usually, these images are updated regularly, so you should not expect to see many vulnerabilities in them (at least not ones with available fixes).

This might not be the case with older images, random images, not backed by big companies or your own images if you are not taking care of them.

 Sometimes, a new version of a dependency may include breaking API changes that require a change in your source code, it may include a behaviour change that leads to bugs in the way we interact with the dependency, or it might introduce bugs that we want to avoid until fixed.

Another thing worth mentioning is that this type of scanning only detects *known* vulnerabilities. That is, vulnerabilities that have been found by security researchers and that have assigned CVEs. There might be still vulnerabilities that are not known and are just lurking in your code/dependencies (Log4Shell has been in the wild since 2013, only found in 2021).

In summary, image scanning is not a silver bullet. If an image scanner tells you that you have 0 vulnerabilities in your image, that does not mean that you are 100% secure.

Also, mitigating vulnerabilities can be as simple as bumping a version of a dependency (or downgrading one), but sometimes it can be more tricky because that version bump might require a change in your code.

## CVEs

In the vulnerability table provided by our scanner we see something that starts with `CVE-`:

`bash  4.4.18-2ubuntu1.2  deb  CVE-2022-3715  Medium`

**[CVE](https://cve.mitre.org/)** stands for **C**ommon **V**ulnerability and **E**xposures.

It is a system that allows us to track vulnerabilities and be able to easily search for them.

Each time a new vulnerability is found, it is assigned a CVE by the [CNA](https://www.cve.org/ProgramOrganization/CNAs) (CVE Numbering Authority) and associated with all components that contain that vulnerability.

Once this is done, this information is propagated to the vulnerabilities databases and can be leveraged by image scanners to warn about CVEs/vulnerabilities that are present in our container.