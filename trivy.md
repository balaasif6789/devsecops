Trivy detects two types of security issues:

Vulnerabilities (known vulnerabilities (CVEs), OS package and software dependencies in use (SBOM)
Misconfigurations (IaC misconfigurations, Sensitive information and secrets)
Trivy can scan four different artifacts:

Container Images
Filesystem and Rootfs
Git Repositories
Kubernetes

rivy
Now that we have a docker image in place, we can continue with Trivy.

If you just type trivy at the prompt, you will see the help page.

Scanner for vulnerabilities in container images, file systems, and Git repositories, as well as for configuration issues and hard-coded secrets
Usage:
  trivy [global flags] command [flags] target
  trivy [command]
Examples:
  # Scan a container image
  $ trivy image python:3.4-alpine
# Scan a container image from a tar archive
  $ trivy image --input ruby-3.1.tar
# Scan local filesystem
  $ trivy fs .
# Run in server mode
  $ trivy server
Available Commands:
  aws         scan aws account
  config      Scan config files for misconfigurations
  filesystem  Scan local filesystem
  help        Help about any command
  image       Scan a container image
  kubernetes  scan kubernetes cluster
  module      Manage modules
  plugin      Manage plugins
  repository  Scan a remote repository
  rootfs      Scan rootfs
  sbom        Scan SBOM for vulnerabilities
  server      Server mode
  version     Print the version
Scan a container image
Let’s try Trivy on the docker image we just built.

trivy image 7190ca863cca
The output should look something like this:

2022-09-18T19:50:51.157+0200    INFO    Vulnerability scanning is enabled
2022-09-18T19:50:51.158+0200    INFO    Secret scanning is enabled
2022-09-18T19:50:51.158+0200    INFO    If your scanning is slow, please try '--security-checks vuln' to disable secret scanning
2022-09-18T19:50:51.158+0200    INFO    Please see also https://aquasecurity.github.io/trivy/v0.32/docs/secret/scanning/#recommendation for faster secret detection
2022-09-18T19:50:53.669+0200    INFO    Detected OS: alpine
2022-09-18T19:50:53.669+0200    INFO    Detecting Alpine vulnerabilities...
2022-09-18T19:50:53.676+0200    INFO    Number of language-specific files: 1
2022-09-18T19:50:53.676+0200    INFO    Detecting python-pkg vulnerabilities...
7190ca863cca (alpine 3.16.2)
Total: 0 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 0)
Scan a filesystem
Scan a filesystem (such as a host machine, a virtual machine image, or an unpacked container image filesystem).

trivy fs --security-checks vuln,secret,config ./
The --security-checks can be configured depending on what you want Trivy to detect. Default is vuln and secret, but above we added config as well.

--security-checks strings   comma-separated list of what security issues to detect (vuln,config,secret,license) (default [vuln,secret]
Ok, now Trivy found something

2022-09-18T19:53:51.860+0200    INFO    Vulnerability scanning is enabled
2022-09-18T19:53:51.860+0200    INFO    Misconfiguration scanning is enabled
2022-09-18T19:53:51.860+0200    INFO    Secret scanning is enabled
2022-09-18T19:53:51.860+0200    INFO    If your scanning is slow, please try '--security-checks vuln' to disable secret scanning
2022-09-18T19:53:51.860+0200    INFO    Please see also https://aquasecurity.github.io/trivy/v0.32/docs/secret/scanning/#recommendation for faster secret detection
2022-09-18T19:53:52.199+0200    INFO    Number of language-specific files: 1
2022-09-18T19:53:52.199+0200    INFO    Detecting pip vulnerabilities...
2022-09-18T19:53:52.202+0200    INFO    Detected config files: 1
Dockerfile (dockerfile)
Tests: 22 (SUCCESSES: 21, FAILURES: 1, EXCEPTIONS: 0)
Failures: 1 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 1, CRITICAL: 0)
HIGH: Specify at least 1 USER command in Dockerfile with non-root user as argument
════════════════════════════════════════════════════════════════════
Running containers with 'root' user can lead to a container escape situation. It is a best practice to run containers as non-root users, which can be done by adding a 'USER' statement to the Dockerfile.
See https://avd.aquasec.com/misconfig/ds002
Trivy found a HIGH severity. It gives you a description of the severity and link to aquasec vulnerability database to read how you can fix the problem. That’s pretty great.

You can also tell Trivy to only look for issues that contains the severity HIGH.

trivy fs --security-checks vuln,secret,config  --severity HIGH ./
Scan a Git repository
To scan a remote git repository

trivy repo https://github.com/knqyf263/trivy-ci-test



https://aquasecurity.github.io/trivy/v0.29.2/docs/vulnerability/scanning/
