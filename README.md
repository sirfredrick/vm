# vm

> Shell script that simplifies creating qemu virtual machines

Implements a `.iso` cache via the `repo.conf` file and organizes your vm
directories.

POSIX compliant\*
\*Requires either `wget` or `curl` to be installed and in the `PATH`

## Running

Edit the `repo.conf` file to include the name of the `.iso` file and its
download url in the following format:
```
name https://example.org
name2 https://example.com
```
Then make the script executable with
```sh
chmod +x vm
```

Then run
```sh
vm update
```
to download the `.iso` files to the `cache` directory

To remove the `.iso` files from the `cache` directory run 
```sh
vm clear
```

To create a new vm from one of the `.iso` files in the `cache` directory run
**Note:** This vm boots from `alpine.iso` has 2 GiB of RAM, 20 GiB of storage, and will be
stored in the `my-vm` directory
```sh
vm -m 2 -d alpine -s 20 create my-vm
``` 

After finishing the install process of your operating system run
```sh
vm -m 2 my-vm
```
to boot the vm in the `my-vm` directory with 2 GiB of RAM

Additional options include

* -v, version: displays the version of the vm utility
* -h, help: displays the command options
* -e: using efi boot instead of bios boot (requires `ovmf` package expected
  location is `/usr/share/ovmf/OVMF.fd`)
* -w: adds additional settings to boot a Windows vm

## Developing 

Make sure you are using a POSIX OS as the host and that `git` is installed and
on your `PATH` then run

```sh
git clone https://github.com/sirfredrick/vm.git
```

then follow the above steps to run it.

## Contributing

If you would like to contribute, please fork the repositiory and perform a
GitHub pull request. Pull requests are warmly welcome!

## Links

* Repository: [https://github.com/sirfredrick/vm](https://github.com/sirfredrick/vm)
* Issues: [https://github.com/sirfredrick/vm/issues](https://github.com/sirfredrick/vm/issues)
* Thanks to [shellhaters](https://shellhaters.org) for an easy to use link to
  the POSIX documentation.

## License
Copyright (c) 2021 Sir Fredrick

This program is free software; you can redistribute it and/or modify it under 
the terms of the GNU General Public License as published by the Free Software 
Foundation; either version 2 of the License, or (at your option) any later version.
