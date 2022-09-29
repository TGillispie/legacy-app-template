## Legacy Project High Level Tasks
- [Identify Non-Repo Files](#identify-non-repo-files)
  - [logs, users, temporary](#log-user-and-temporary-files)
  - [Mixed Non-Repo/Repo Files](#mixed-non-reporepo-files)
  - [Secret Files](#secret-files)
  - [Pre-SCM Files](#pre-scm-files)
- [Document Basic Setup Instructions](#document-basic-setup-instructions)
- [Identify Missing Perl Modules](#document-basic-setup-instructions)


## Identify Non-Repo Files
Identify common user and app files that do not belong in the repository so they can be added to the .gitignore.

### Log, User, and Temporary Files
Some examples are any user created data, log files created by the application, and sas output files.  Another example is any folder full of logs and user data, or any folder that should be ommitted from a repository entirely.

```
/tmp
/backup
/dist
.env
app_config.x
1601321898.txt
1642520101.txt
1642520518.txt
410342_07APR11.TXT
410527_11JUL19.TXT
410527_13JAN12.TXT
coop_gps_load.log
coop_gps_load.lst
gps_load.log
```

### Mixed Non-Repo/Repo Files
A complex situation can arise where folders contain some app files within a bunch of user or logging files.  This is not ideal, but can be worked around fairly easily if separating those files is not a priority.

Inside .gitignore folders can be ignored while still tracking sub-folders or appication files.  [git-scm: Pattern Format - An Optional Prefix](https://git-scm.com/docs/gitignore/2.16.6#_pattern_format)

```
# Don't ignore the logging directory explicitily.
!logging/

# Ignore all files in logging.
logging/*

# Don't ignore any .sas files.
!logging/*.sas
```

### Secret Files
Secret files like enviornment and application configuration files should not be stored in the repository.  They often provide revealing details which could be used to compromise an application, or service.  Generally, these types of file are also specific to a particular environment, and are not common to all running versions of a program.

### Pre SCM Files
Pre Source Control Managmenet Files should not be ommited from a repository using .gitignore, they should be removed all together.  These types of files are pre-SCM mechanisims.  The implementation of an SCM mitigates the need for these types of manual revison conrol files.  Pre-SCM files might need to be archived somewhere, but should not be stored in the repository.

```
src/                  # Actual application code.
src-development/      # Likely a previous SCM mechanisim.
src/login.pl          # Actual application code.
src/login_1.pl        # Likely a previous SCM mechanisim.
src/login(_old).pl    # Very likely a previous SCM mechanisim.
```

## Document Basic Setup Instructions
Document application setup instructions in a README.md file or through a deployment script or both.  Generally setup instructions contain two parts: removing the previous code and adding the new code.

The removal process should take care not to remove any user data, application logs, or config files.  Only remove app code which will be replaced by a new version stored in the repository.

## Identify missing modules
Run code directly or via the main entry point when hosted by a web server to find missing modules and libraries.  Document those missing files.  If building an environment, update the current environment to include those modules and libraries.
