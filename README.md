This repository provides simple build execution images to build Android Apps for CI pipelines. Tested with GitLab CE 15.7.2 and newer using GitLab Runner 15.4.0 and newer. Tag names are created using SDK Version and Build-Tools-Version ("SDK"-"Build-Tools-Version"-"JAVA Version", e.g.: 33-32.0.0-j17). Missing Java Version indicates Java 11.

In a GitLab CI pipeline this image can be used to execute gradle tasks.

Usually execution rights should be ensured after checking out the repository. In the before_script I usually run "chmod +x ./gradlew". To execute a gradle task in a build stage simply use "./gradlew" from within the project repository. "./gradlew -Pci --console=plain :app:assembleRelease --parallel".

These images assume the gradle-Version was set by a gradle-wrapper in the repository prior to execution.

Docker Hub: https://hub.docker.com/r/davidmcd1/android-build
