# Java Project Template
A template to quickly start new Java projects. Contains a minimal `pom.xml` with Java 17 and Junit `5.8.2`. Also contains a `build.yml` file with a basic Github Action configuration to compile your code and upload coverage results to [CodeCov](https://app.codecov.io/).

## Usage
1. Edit `pom.xml` and set the `artifactId` and `name`.
2. Configure your repository in [CodeCov](https://app.codecov.io/): you probably need to enable it, and copy the upload token
3. Create a new repository secret: `CODECOV_TOKEN` and set its value with your upload token
4. Write some code (and some tests!) and push your work

At this point the Github Action should compile and test your code, and you should be able to see your coverage data in CodeCov.
