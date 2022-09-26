# Go Sample App using Mod

## Building

This app is specifically built with Go 1.19.0 due to a critical CVE inside of it related to the `net/http` package within Go 1.19.0.
`pack build mod-sample --buildpack paketo-buildpacks/go --sbom-output-dir sbom-content --env BP_GO_VERSION=1.19.0`

## Looking for vulnerabilities

#### Snyk on image
```
docker scan pip-sample
```
Locates OS-based vulnerabilities, but no Golang-related vulnerabilities.

#### Grype on image
```
grype pip-sample
```
Locates OS-based vulnerabilities, but no Golang-related vulnerabilities.

#### Grype on SBOM
```
grype sbom:sbom-content/build/paketo-buildpacks_go-dist/go/sbom.syft.json
```
Locates critical-severity `Go` vulnerability
