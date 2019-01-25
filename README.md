# stataid 
##  Obtaining and displaying information about running Stata instances and closing Stata instances in Microsoft Windows. 

__Table of Contents__
1. [Syntax](#1-syntax)
2. [Options](#2-options)
3. [Description](#3-description)
4. [Stored Values](#4-stored)
5. [Examples](#5-examples)
6. [About](#6-about)

# 1. Syntax

To obtain information about running Stata instances:

```
stataid list , [exename(_string_) list mata ]
```

To close a running Stata instance using a Windows process id:

```
stataid kill, id(_idnumber_)
```

# 2. Options

**exename(_string_)** Name of Stata executable.  **stataid** tries to determine the name of the executable, but might fail in case the executable has a non standard name.

**mata** Saves the data in a mata matrix called _stataid_.

**kill(_idnumber_)** Kills process with specific id number.


# 3. Description

**stataid** obtains information about all running Stata processes of a Microsoft Windows system. It retrieves the running tasks using **shell** and tasklist of the command line. The following information are saved: 

1. Name of the exe file (image name)

2. Process id

3. The name of the session

4. The number of the session

5. Memory used

6. The status

7. The username

8. CPU time

9. Windowtitle

**stataid** can close any Stata instance, including the running one. Using the parameter **kill**, it closes the Stata instance defined by **id()**. Internally **stataid** uses the Windows command line command _taskkil_ to kill the Stata instance. 

Note, Stata is closed _**without**_ saving any data!

# 4. Stored Values

**stataid** stores the following in **r()**:

Scalars:

**r(instances)** Number of Stata instances (only with **stataid list**).

# 5. Examples

To retrieve a list of all current running Stata instances (2 are running and list the result):

```
stata stataid list
```

The output will be:

```
. stataid list
Obtaining number of Stata instances running under StataSE-64.exe.
2 Stata instance(s) running.
```

Kill Stata instance with id _13424_:

```
. stataid kill , id(13424)
CPU process id 13424 going to be closed.
```

# 6. About

Jan Ditzen (Heriot-Watt University)

Email: j.ditzen@hw.ac.uk

Web: www.jan.ditzen.net

This version: 1.0
