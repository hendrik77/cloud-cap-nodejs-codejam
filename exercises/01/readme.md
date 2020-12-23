# Exercise 01 - Installing the CAP related tools

In this exercise you'll install all the tools required to work comfortably with the Node.js flavor of CAP in a local environment.

Successfully completing this exercise relies on the hardware and software [prerequisites](../../prerequisites.md) published for this CodeJam. These prerequisites describe the requirement for some software preinstalled; this includes VS Code and Node.js. This exercise will focus on tools relating to both of these. (If you haven't already installed Node.js, we recommend version 10 (LTS)).

## Steps

After completing these steps you'll have a working local environment for development of CAP based projects with Node.js, using the CAP "development kit" package `@sap/cds-dk`.

### 1. Install the CDS command line tool

The CDS command line tool is the heart of everything you do when developing CAP services locally. It is Node.js based and comes in the form of an NPM package (which further depends on other packages). The package and its dependencies are in the `@sap` namespace and are available from the [NPM registry](https://www.npmjs.com/). 

:point_right: First, delete the relation of the `@sap` namespace to the SAP NPM registry if created before (It's not updated anymore since June 2020):

```sh
user@host:~
=> npm config delete "@sap:registry"
```

:point_right: Check that this setting is now saved in your configuration, with:

```sh
user@host:~
=> npm config ls
```

You should see output similar to this (wihtout the line @sap:registry = "https://npm.sap.com") :

```sh
; cli configs
metrics-registry = "https://registry.npmjs.org/"
scope = ""
user-agent = "npm/6.4.1 node/v10.15.3 linux x64"

; userconfig /user/.npmrc

; node bin location = /user/.nvm/versions/node/v10.15.3/bin/node
; cwd = /
; HOME = /user
; "npm config ls -l" to show all defaults.
```

:point_right: Next, explore the information about the `@sap/cds-dk` package, including its dependencies, with:

```sh
user@host:~
=> npm info @sap/cds-dk
```

This will show you that it has dependencies on other `@sap` namespaced packages, and also that there is a 'binary' (in other words an executable) called `cds` that's delivered as part of the package.

:point_right: Now, install the `@sap/cds-dk` package globally:

```sh
user@host:~
=> npm install --global @sap/cds-dk
```

This produces a fair amount of output as it works, but should eventually end with a couple of lines similar to this:

```sh
+ @sap/cds-dk@1.4.2
added 471 packages from 381 contributors in 33.398s
```

Here you can see that the version of the `@sap/cds-dk` package just installed is 1.4.2. It may be that the version of `@sap/cds-dk` that is installed when you do this exercise will be different (newer).

### 2. Install the CDS extension for VS Code

To efficiently and comfortably develop CAP based services with CDS, there is an extension for the [VS Code](https://code.visualstudio.com/) IDE. 

:point_right: To install the extension, proceed as follows:
1.	Go [to Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=SAPSE.vscode-cds#overview).
2.	Choose Install and VS Code opens the details page for the extension.
3.	In VS Code choose Install to enable the extension.

When successfully installed, you should see the extension thus (again, the version number may be different):

![CDS Language Support extension installed in VS Code](vscode-extension.png)

> **For macOS users only:** To be able to open VS Code from the command line (which you will be doing in a subsequent exercise) you need to add the installation path of VS Code to the environment variable PATH. There's an option to do this via the `Command Palette` in VS Code.

> Open the `Command Palette` with ⇧⌘P. You can also open it via the menu bar: View -> Command Palette.

> ![Command Palette navigation in the menu bar](command-palette.png)

> Search for `code` and press Enter.

> ![search for code in the command palette](install-code-path.png)

> A success message for the process should then appear at the bottom right of the screen.

> ![message that the 'code' command was successfully installed](sucessfully-installed.png)

### 3. Verify your development environment

:point_right: Run the following command from the terminal to check whether all required tools are installed (this is an experimental tool, please contact the instructor if you have any questions):

```sh
npx check-sap-cloud-readiness -codejam-cap
```

You should see an output similar to this:
![out](output.png)

If necessary, double check the [prerequisites](../../prerequisites.md)  to install the missing tools. Please contact the instructor of this CodeJam if you need help.


## Summary

You've now installed the key tools for developing with CAP locally, and are all set to create your first project.

## Questions

1. What are the benefits of using NPM here?
<!--- easy to user and de-facto standard --->

2. What are the `@sap` namespaced packages upon which `@sap/cds-dk` depends?
<!--- cds-sidecar-client, edm-converters, cds, generator-cds --->

3. What is the significance of using the `--global` option when installing the `@sap/cds-dk` package?
<!--- globally available --->

4. Can you find another way to install extensions in Code? (Hint: look at the Activity Bar)
<!--- Extension section at the activity bar can be used to add extensions --->
