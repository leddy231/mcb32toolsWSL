# mcb32tools on Windows Subsystem for Linux
## Installing WSL
To install WSL on Windows, follow [this guide](https://www.computerhope.com/issues/ch001879.htm). Ubuntu is the recommended distribution. Once installed the bash shell can be switched to by entering `bash` or `wsl`. The bash shell will have its working directory set to the same directory the command was issued from (So if the command is run in Documents, the shell will start in Documents). In bash the entire Windows file system can be navigated freely (mounted under /mnt/c), as well as the rest of the linux file system. This means you can keep all your code in one place and not have to move them to and from WSL. To return back to Powershell/CMD, use the command `exit`.


## Installing mcb32tools
1. Install additional packages by running the following commands one by one.
```bash
echo "deb-src http://archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse" | sudo tee -a /etc/apt/sources.list
sudo apt update
sudo apt-get install bzip2 make libftdi-dev
```
2. Download the linux .run file from the [mcb32tools Github](https://github.com/is1200-example-projects/mcb32tools/releases/).
3. Install the toolchain by running the file in bash with super user privileges. `sudo ./path_to_file/mcbtools-vX.X...-linux.gnu.run`

## Using the toolchain
1. In bash navigate to the folder with the code to compile and install
2. Enter the cross compile environment `. /opt/mcb32tools/environment` (Important space after the dot)
3. Connect your chipkit device
4. In Windows Device Manager, under "Ports (COM & LTP)" look for your device, and note the COM number (ex COM4)
5. Compile your code with `make`
6. Install your code with `make install TTYDEV=/dev/ttySX`, replace the X with the COM number for your device (ex `TTYDEV=/dev/ttyS4`)
