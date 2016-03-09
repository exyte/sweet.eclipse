Sweet Eclipse
=============

Sweet Eclipse is a project in which the reliable Eclipse platform meets modern UI techniques to provide better user experience.

![Solarized Theme](http://exyte.github.io/sweet.eclipse/img/app1.png)
![Dark Theme](http://exyte.github.io/sweet.eclipse/img/app2.png)
![Idea Darcula Theme](http://exyte.github.io/sweet.eclipse/img/app3.png)

Check out [Sweet Eclipse website](http://exyte.github.io/sweet.eclipse/) for more information.

Build a Package Locally
-----------------------

It's *easy* to run the build locally! All you need is Maven and then you need 
to tell Maven which package(s) to build via profile. Currently we provide
only java package against Eclipse Mars.1 (4.5.1). You can build it using following 
command from the root of the Git repository:

    mvn clean verify -Psweet.package.java -Declipse.simultaneous.release.repository="http://download.eclipse.org/releases/mars/201510021000"

This build creates output in two places:

1. tar.gz/zip archives with the packages in `archive/` and
2. a p2 repository with the EPP artifacts in `archive/repository/`.

Windows users
------------- 

If you are running the build on Windows, the last build step will currently fail. 
This failure can be circumvented by skipping the last step which aggregates the 
filtered EPP artifacts from the packages into a new p2 repository. For further 
details see [bug 426416](https://bugs.eclipse.org/bugs/show_bug.cgi?id=426416).
At the moment it is advised to run the build command on Windows with `package` 
only:

    mvn clean package -Psweet.package.java

In addition to that it is not possible to create zip and tar.gz archives on 
Windows due to missing Bash scripting capabilities. On Windows, the output of the
build is the `eclipse` directory that contains the usual content from the zip
archive. This directory can be found below (e.g. RCP package) 
`packages/com.exyte.sweet.package.java.product/target/products/`.
