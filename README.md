# Configuring modern Bash as the default shell for macOS

This guide uses [Upgrade to bash 4 in Mac OS X](http://clubmate.fi/upgrade-to-bash-4-in-mac-os-x/) as its base, then modifies its content over time, as appropriate. A huge thanks to [@hiljaa](https://twitter.com/hiljaa).

## Install Bash

Bash version can be queried with the `--version` flag:

```bash
$ bash --version
GNU bash, version 3.2.57(1)-release (x86_64-apple-darwin16)
Copyright (C) 2007 Free Software Foundation, Inc.
```

The actual installation is going to happen with [Homebrew](https://brew.sh), a macOS package manager.

```bash
brew install bash
```

After that, grab the value from the following command. This is where Homebrew installed your new Bash binary.

```bash
$ echo $(brew --prefix bash)/bin/bash
/usr/local/opt/bash/bin/bash
```

> [!NOTE]
> The path above is correct for Intel-based Macs. If you have an Apple Silicon-based Mac, the path will be `/opt/homebrew/opt/bash/bin/bash`.

## Testing the Bash version

Now we'll want to test our version of Bash. Imagine a file:

```bash
#! /bin/bash
# version-test.sh
echo $BASH_VERSION;
```

Make it executable and run it:

```bash
$ chmod +x ./version-test.sh
$ ./version-test.sh
3.2.57(1)-release (x86_64-apple-darwin16)
```

Seemingly it’s still using the old version of Bash. The trick is the _shebang_ on the first line, it’s pointing to the old Bash path. Change it to use the new path that you saved, above.

### Intel Mac

```bash
#! /usr/local/opt/bash/bin/bash
# version-test.sh
echo $BASH_VERSION;
```

### Apple Silicon Mac

```bash
#! /opt/homebrew/opt/bash/bin/bash
# version-test.sh
echo $BASH_VERSION;
```

### Check the version

Now run it and it gives a newer version.

```bash
$ ./version-test.sh
5.2.21(1)-release
```

## Configure the Default Shell in Terminal

Again, use the new path that you saved above.

```bash
sudo bash -c "echo $(brew --prefix bash)/bin/bash >> /etc/shells"
chsh -s $(brew --prefix bash)/bin/bash
```

Now quit Terminal, then re-launch it.

```bash
echo $BASH_VERSION;
```

## Troubleshooting

If it still shows the old Bash, just go to the _Terminal_ menu → _Preferences_ → _General_ → _Shells open with_, then choose _Default login shell_.

## See Also…

* https://superuser.com/questions/857250/how-to-update-bash-on-mac-os-x-yosemite
