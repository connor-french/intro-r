Pre-workshop Installation Instructions
================

## Install/Update R & RStudio

Contents borrowed and modified from [UVA’s Data Science Essentials in R
series](https://uvastatlab.github.io/phdplus/intror.html)

### Before the first session

To participate in the R workshop, please bring a laptop with R and
RStudio installed. We recommend that you have the latest version of R
(3.6.1). You need to have RStudio installed, but it is less crucial that
you are using the most recent version (1.2.5001).

Do you already have R and RStudio installed?

  - No - follow the instructions for “I do not have R installed”  
  - Yes - follow the instructions for “I have R installed”

### “I do not have R installed”

You should install R and RStudio.

#### Installing R

##### Windows:

1.  Go to <https://cloud.r-project.org/bin/windows/base/>
2.  Click the “Download R 3.6.1 for Windows” link. ![Screenshot of
    Windows
    download](https://github.com/connor-french/intro-r/blob/master/images/installr.jpg)
3.  When the file finishes downloading, double-click to install. You
    should be able to click “Next” to all dialogs to finish the
    installation.

##### Mac:

1.  Go to <https://cloud.r-project.org/bin/macosx/>
2.  Click the link “R-3.6.1.pkg” ![Screenshot of MacOSX
    download](https://github.com/connor-french/intro-r/blob/master/images/rmac.png)
3.  When the file finishes downloading, double-click to install. You
    should be able to click “Next” to all dialogs to finish the
    installation.

Note: For MacOSX users, you might have to install XQuartz before you are
able to run the application. You can follow the instructions on the R
download page to the XQuartz download page. You should be able to click
“Continue” to all dialogs to finish the installation. ![Screenshot of
XQuartz
download](https://github.com/connor-french/intro-r/blob/master/images/rmacX0.png)
![Screenshot of XQuartz install
dialog](https://github.com/connor-french/intro-r/blob/master/images/rmacX1.png)

##### Linux:

For any adventurous Linux users in our group follow [this
guide](https://github.com/duckmayr/install-update-r-on-linux) to
install/upgrade to the most recent version of R on Ubuntu (18.04) or
Mint (19).

#### Installing RStudio

1.  Go to [the RStudio download
    page](https://www.rstudio.com/products/rstudio/download/#download).
2.  Under “Installers for Supported Platforms” select the appropriate
    installer for your operating system ![Screenshot of Windows RStudio
    page](https://github.com/connor-french/intro-r/blob/master/images/rstudio2windows.png)
    ![Screenshot of MacOSX RStudio
    page](https://github.com/connor-french/intro-r/blob/master/images/rstudio.png)
3.  When the file finishes downloading, double-click to install. You
    should be able to click “Next” to all dialogs to finish the
    installation. ![Screenshot of Windows RStudio dialog
    page](https://github.com/connor-french/intro-r/blob/master/images/rstudio1.png)

Note: MacOSX users can drop the RStudio application into their
application folder directly. ![Screenshot of MacOSX dropping RStudio
into application
folder](https://github.com/connor-french/intro-r/blob/master/images/rstudio2.png)

### “I have R installed”

The workshops run more smoothly when everyone is using the same version
of R. Please update R if necessary (and less crucially, RStudio).

#### Verify R version

Open RStudio. At the top of the Console you will see session info. The
first line tells you which version of R you are using. If RStudio is
already open and you’re deep in a session, type `R.version.string` in
the console and enter to print out the R version.

Do you have R version 3.6.1 installed?

  - No - follow the instructions for “Updating R”
  - Yes - Great\!

#### Updating R/RStudio

##### Windows

To update R on Windows, try using the package `installr` (only for
Windows).

1.  Install and load installr:

<!-- end list -->

``` r
install.packages("installr")
library(installr)
```

2.  Call `updateR()` function. This will start the updating process of
    your R installation by: “finding the latest R version, downloading
    it, running the installer, deleting the installation file, copy and
    updating old packages to the new R installation.”  
3.  From within RStudio, go to Help \> Check for Updates to install
    newer version of RStudio (if available, optional).

Note: If this function does not work, you will have to download the
latest R directly from <https://cloud.r-project.org/bin/windows/base/>.
Prior to installing the newest version, it is recommended that you
uninstall the current version and then follow the instructions for
“Installing R.”

##### Mac

On Mac, you can simply download and install the newest version of R.
When you restart RStudio, it will use the updated version of R.

1.  Go to <https://cloud.r-project.org/bin/macosx/>  
2.  Click the link “R-3.6.1.pkg”  
3.  When the file finishes downloading, double-click to install. You
    should be able to click “Next” to all dialogs to finish the
    installation.  
4.  From within RStudio, go to Help \> Check for Updates to install
    newer version of RStudio (if available, optional).  
5.  To update packages, go to Tools \> Check for Package Updates. If
    updates are available, select All and click Install Updates.

##### Linux:

Again, for any adventurous Linux users in our group follow [this
guide](https://github.com/duckmayr/install-update-r-on-linux) to
install/upgrade to the most recent version of R on Ubuntu (18.04) or
Mint (19).
