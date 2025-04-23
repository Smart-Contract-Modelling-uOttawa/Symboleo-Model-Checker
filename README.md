# Symboleo-Model-Checker
An nuXMV-based model checker tool

In order to run the examples you can download nuXmv for https://nuxmv.fbk.eu
and then, once installed run the following commands on the shell:

```
prompt > nuXmv -cpp -v 0 -load MeatSales_nusmvcmd.txt MeatSales.smv

prompt > nuXmv -cpp -v 0 -load PizzaDeliveryContract_nusmvcmd.txt PizzaDeliveryContract.smv
```
# Installation on macOS (Apple Silicon – M1/M2)

If you're on a Mac with an Apple Silicon chip (M1, M2 or M3), you need to run the x86_64 version of nuXmv using Rosetta, as the official build is not natively compatible.

**Step 1: Download nuXmv (x86_64 version)**

- Go to https://nuxmv.fbk.eu
- Download nuXmv 2.0.0 – Mac OS X 64-bit (x86)

**Step 2: Install Rosetta (if not already installed)**
```
softwareupdate --install-rosetta
```
**Step 3: Install Homebrew (x86_64 version, via Rosetta)**

/usr/local is used for x86_64 architecture (Rosetta), so install Homebrew for that architecture:
```
arch -x86_64 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
This installs Homebrew in /usr/local (not /opt/homebrew which is for arm64).

**Step 4: Install GMP (required by nuXmv)**
```
arch -x86_64 /usr/local/bin/brew install gmp
```
Then create a symlink so nuXmv can find the GMP library:
```
sudo ln -sf /usr/local/Cellar/gmp/*/lib/libgmp.10.dylib /usr/local/lib/libgmp.10.dylib
```
**Step 5: Run nuXmv under Rosetta** 

Use the arch command to run nuXmv in x86_64 mode:
```
arch -x86_64 /path/to/nuXmv-2.0.0-Darwin/bin/nuXmv -int
```
You can also create an alias:
```
alias nuxmv="arch -x86_64 /path/to/nuXmv-2.0.0-Darwin/bin/nuXmv"
```

**Running Examples**

Once installed, you can run the example contracts using the following commands:
```
MacBook-Air bin % nuXmv -int MeatSale.smv
> go_msat
> check_ltlspec_ic3 -i
or 
> read_model -i MeatSale.smv
> go

To load another model
> reset
To list all available commands
> help
To quit from the shell
> quit
```