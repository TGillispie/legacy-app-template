Everything below this line is the template for a project README.  It covers basic installation, and running instrutions.  Sections on config files, testing methods and some additional information on files stored in a repository are also included.

*_project_* is inteded as a place holder and is used in a limited number of places through this template.

---------------------------------------------------------------------------

This is the _project_.  The follow instrutions describe setting up and running the _project_.

 ## Contents

- [Quick Setup](#quick-setup)
- [Setup](#setup)
   - [Get the Code](#get-the-code)
   - [Setup Config and Environment](#setup-config)
   - [Install Dependencies](#install-dependencies)
   - [(optional) post-install](#optional-setup-post-install-script)
   - [Setup Notes](#setup-notes)
- [Troubleshooting :link:](./common-errors.md)
- [Run The Code](#run)
- [File Descriptions](#application-files)
   - [Program Files](#program-files)
- [Run Verification](#test)
   - [Running Tests](#running-tests)
   - [Test Files](#test-files)
- [Legal](#legal)


## Quick Setup
The following steps are fairly quick, unless Apache and perl are not setup already.  See [Setup](#setup) for a full install.

```
# Clone the _project_ repository.
*git clone https://github.com/NEFSC/_project_.git prj-name

# Copy the application config and .env files to the repository root.

# Update config files with local values.

# The remainder steps are optional and intend to assist with application deployment.

# (optional)

# Update the post-install script with any custom setup commands specific to the local environment.
# cp post-install.example post-install
# chmod +x post-install

# Run the deployment script.  The deploy script runs in order: pre-install, and then post-install.  Those two scripts are not part of this repository and should contain custom instrutions specific to an environment.

## To update a new version or deploy an application, old code must be removed
## while taking care not to remove user files or application log files.
## Place those commands for the current enviornment in pre-install & post-install
## as necessary.

./deploy
```

## Setup
These steps assume _project_ will run under Apache w/ Perl.

### Get The Code
Clone this repository.

``` git clone https://github.com/NEFSC/_project_.git _repo_```

### Setup Config
There are several config files.  They can be found in the .gitigonre file, but have been listed here for completness.

File | Description
-- | --
.env | Local environment variables used by ./deploy.
*StudyFleet* |
modules/x-html/x/config.php | Site Config
modules/y-html/y/utilities/config.php | Site Config
*COOP RES* |
modules/sf-cgi/secrets_git.pl | App Config


### Install Dependencies

#### Install & Setup perl 5.32.1
[Install Perl :link:](../../../../TGillispie/language-notes/blob/main/lang/perl/README.md#install-perl)

#### Install any missing perl modules.
```
  perl -MCPAN -e shell

  install CGI::Session
  install Net::LDAP
  install Barcode::Code128
  install Mail::Sender  # email defaults saved in blib/lib/Mail/Sender.config
```

#### (Optional) Setup post-install Script
Post-install is for custom environment setup instructions.  The post-install script will run at the end of the deploy script.
```
  # Create a post install script or copy the example.  Be sure to update the script for the intended environment.
  cp post-install.example post-install
```

### Setup Notes
[Perl Setup Doc :link:](../../../../TGillispie/language-notes/blob/main/lang/perl/README.md#setup-support)


## Run
Apache is the current recomendation.


## Application Files
### Program Files
All perl files.
All php files.
All SAS files.
All html files and assets.


## Test
App is tested by direct user interaction at the mmoment.
### Running Tests
### Test Files
