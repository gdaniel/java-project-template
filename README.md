# Java Project Template
A template to quickly start new Java projects.



## Content

- A minimal `pom.xml`
  - Environment: Java 17
  - *Compile* dependencies: SLF4J
  - *Test* dependencies: Junit Jupiter, AssertJ, Log4j2 binding for SLF4J 
- A `build.yml` file with a basic Github Action configuration to compile your code and upload coverage results to [CodeCov](https://app.codecov.io/)
- A `nginx.conf` file to quickly get started with your nginx configuration if you want to upload resources related to your project



## Configure the Java project and build

1. Edit `pom.xml` and set the `artifactId` and `name`.
2. Configure your repository in [CodeCov](https://app.codecov.io/): you probably need to enable it, and copy the upload token
3. Create a new repository secret: `CODECOV_TOKEN` and set its value with your upload token
4. Write some code (and some tests!) and push your work

At this point the Github Action should compile and test your code, and you should be able to see your coverage data in CodeCov.



## Deploy resources on nginx

1. Create a new `A` DNS record pointing to your server
2. Edit `nginx.conf` and replace `server_name` with the name you specified in your DNS configuration
3. Create a directory in `/var/www/html` to store your static content, and edit `nginx.conf` 's `root` to point to this new directory
4. Upload `nginx.conf` to your server (`/etc/nginx/sites-available`) and **give it an appropriate name**. Then enable the site with the following command: `ln -s /etc/nginx/sites-available/my-app.conf /etc/nginx/sites-enabled/`.
5. (*Recommended*) Run [certbot](https://certbot.eff.org/instructions) to get HTTPS certificates for your subdomain
6. Create the following repository secrets
   1. `CD_HOST`: the host for your resources (e.g. `myvsp.ovh.net`)
   2. `CD_USERNAME`: the user to log as in your server (e.g. `bob`)
   3. `CD_PASSWORD`: the password of the user you specified
7. Uncomment the steps `Generate Javadoc` and `Upload Javadoc` in `.github/workflow/build.yml`
   1. Set the  `remote` path to point to the directory you created in *3*
8. (*Optional*) Delete `nginx.conf` from your app directory, you don't need it anymore, it is on your server now