# **Manual CLI Installation**

---

The newest Binary Releases can be found here: [https://github.com/decred/decred-binaries/releases](https://github.com/decred/decred-binaries/releases). With the exception of the `.msi` and `.dmg` files, they are archives of the latest executable binaries for each release. Although most of this will be unzip and go, instructions are provided for Mac, Linux, and Windows below (assumed proficiency for *BSD users).

> OSX/macOS

1. Download the correct file:

    For 32-bit computers, download the `decred-darwin-386-v1.0.8.tar.gz` file. <br />
    For 64-bit computers, download the `decred-darwin-amd64-v1.0.8.tar.gz` file.

2. Navigate to download location and extract the .tar.gz file:

    Finder: simply double click on the .tar.gz file. <br />
    Terminal: use the `tar -xvzf filename.tar.gz` command. 

    **NOTE**: If you are using Safari on macOS Sierra and have the 'Open "safe" files after downloading' preference enabled, .gz and .zip files are automatically uncompressed after download. The `tar -xvzf filename.tar.gz` command results in this error: `tar: Error opening archive: Failed to open 'filename.tar.gz'`. Use `tar -xvzf filename.tar` instead (remove the .gz from the previous command).
    
    Both of these should extract the tar into a folder that shares the same name. (`e.g. tar -xvzf decred-darwin-amd64-v1.0.8.tar.gz` should extract to `decred-darwin-amd64-v1.0.8`). It should include `dcrctl`, `dcrd`, `dcrwallet`, `sample-dcrctl.conf`, `sample-dcrd.conf`, and `sample-dcrwallet.conf`.


> Linux

1. Download the correct file:

    For 32-bit computers, download the `decred-linux-386-v1.0.8.tar.gz` file. <br />
    For 64-bit computers, download the `decred-darwin-amd64-v1.0.8.tar.gz` file. <br />
    For 32-bit ARM computers, download the `decred-linux-arm-v1.0.8.tar.gz` file. <br />
    For 64-bit ARM computers, download the `decred-linux-arm64-v1.0.8.tar.gz` file.

2. Navigate to download location and extract the .tar.gz file:

    Ubuntu File Browser: simply right click on the .tar.gz and select "Extract Here". <br />
    Terminal: use the `tar -xvzf filename.tar.gz` command. 
    
    Both of these should extract the tar.gz into a folder that shares the same name. (`e.g. tar -xvzf decred-darwin-amd64-v1.0.8.tar.gz` should extract to `decred-darwin-amd64-v1.0.8`). It should include `dcrctl`, `dcrd`, `dcrwallet`, `sample-dcrctl.conf`, `sample-dcrd.conf`, and `sample-dcrwallet.conf`.

> Windows

Note: Windows 7/8/10 natively provides support for `.zip` files, therefore it is preferable to use the `.zip` file so that third-party applications aren't required for the `.tar.gz` file. Instructions are provided for the `.zip` file.

1. Download the correct file:

    For 32-bit computers, download the `decred-windows-386-v1.0.8.zip` file. <br />
    For 64-bit computers, download the `decred-windows-amd64-v1.0.8.zip` file.

2. Navigate to download location and unzip the `.zip` file:

    File Explorer: Right click on the .zip file, select "Extract All.." and a prompt should open asking for the directory to use. The default will extract the `.zip` to a folder with the same name. It should include `dcrctl`, `dcrd`, `dcrwallet`, `sample-dcrctl.conf`, `sample-dcrd.conf`, and `sample-dcrwallet.conf`.

If you decide to download the `.tar.gz` file, it will require two separate extractions in some third-party application (7-zip, winRAR, etc..) to get to the actual binaries.

---

## Minimum Configuration

At the very minimum, for `dcrd`, `dcrwallet`, and `dcrctl` to be able to communicate with each other, they need to be launched with the same rpcuser/rpcpass combination. For manual configuration please follow these steps:

1. If the operating system dependent home directories listed in the [configuration files](#configuration-file-locations) section above do not exist, please create them for `dcrd`, `dcrwallet`, and `dcrctl`.
2. Copy the [sample dcrd configuration file](https://github.com/decred/dcrd/blob/master/sample-dcrd.conf) from GitHub, and paste it into a new text file. Save the text file as `dcrd.conf` in `dcrd`'s home directory.
3. Copy the [sample dcrwallet configuration file](https://github.com/decred/dcrwallet/blob/master/sample-dcrwallet.conf) from GitHub, and paste it into a new text file. Save the text file as `dcrwallet.conf` in `dcrwallet`'s home directory.
4. Create an empty text file and save it as `dcrctl.conf` in `dcrctl`'s home directory.
5. Choose an arbitrary username and password, these will only be used for each application to communicate via remote procedure call. The easiest configuration is to set them all equal.
6. Inside `dcrd.conf`, underneath `[Application Options]`, add the following lines:<br /><br />
        `rpcuser=<chosen-username>`<br />
        `rpcpass=<chosen-password>`<br /><br />
7. Inside `dcrwallet.conf`, underneath `[Application Options]`, add the following lines:<br /><br />
        `username=<chosen-username>`<br />
        `password=<chosen-password>`<br /><br />
8. Inside `dcrctl.conf`, add the following lines:<br /><br />
        `rpcuser=<chosen-username>`<br />
        `rpcpass=<chosen-password>`<br /><br />
9. Save all three configuration files.
