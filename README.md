# VMontheFly

cloud-init script used to initialize VM _on the fly_ (actually on first boot). I personally use it to setup my workspace when I am starting a new project 
but I also appended some dummy configuration to further expose what's possible to setup.

## Steps:

The config does the following:
- Configures default **ubuntu** user
- Copies SSH public key
- Set hostname
- Apt package update, upgrade and install
- Set up `.vimrc`, `.gitconfig` and `.bash_aliases` files

In general, files appended in the last step are arbitrary, so one can freely modify it. 

At the same time I would like to warn the user to set the **defer** parameter under write_files paragraph if writing to `/home/ubuntu`, since I personally encountered some weird configurations, which to some extent make sense since you cannot create a file under a specific user
until the user is created.
**defer** parameter defers writing the file until final stage, after users were created, and packages were installed. 

## Test

Script can be tested using [Multipass](https://multipass.run/) by running:

    multipass launch --cloud-init </path/to/config/script>
