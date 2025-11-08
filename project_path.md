# project path
<!-- KtF -->
## init new project folder
<!-- KtF-->
```bash <!-- markdownlint-disable-line code-block-style -->
project_name="yfinance-rs-try-out"
echo ${project_name} 
# cd && mkdir <project_name> folder> && cd $_
# command 'cd' change to home folder from logged in user
# command 'mkdir' create the DIRECTORY(ies), if they do not already exist
# command `cd` <folder>`change to the folder
# command '$_' last argument of last command
cd && mkdir ${project_name} && cd $_

```
<!-- KtF -->
## Create a new rust based project inside the previously generated folder and update the rust binary's system wide to the last stable version
<!-- KtF -->
```bash <!-- markdownlint-disable-line code-block-style -->
touch README.md \
&& touch FROM_HERE.md \
&& ln -s README.md README \
&& cargo init "." \
&& cargo add rustfmt \
&& rustup component add rustfmt \
&& mkdir examples \
&& cp src/main.rs examples/example.rs \
&& sed -i -e 's/world/example/g' examples/example.rs \
&& rustup show \
&& rustup check \
&& rustup toolchain uninstall stable \
&& rustup toolchain install stable \
&& export RUSTC_WRAPPER=sccache
&& cargo list --update \
&& rustup update  --force \
&& rustup show \
&& rustup override set stable  \
&& mkdir tests \
&& cargo build \
&& cargo run \
&& cargo run --example example \
```
<!-- KtF-->
## Show which toolchain is active
<!-- KtF-->
```bash <!-- markdownlint-disable-line code-block-style -->
rustup show
# or better
rustup show |sed -n '/active toolchain/,/^$/p'
```
<!-- KtF-->
## Switch/activate toolchain
<!-- KtF-->
```bash <!-- markdownlint-disable-line code-block-style -->
#e.g. nightly
rustup override set nightly
# e.g stable
rustup override set stable
```
<!-- KtF-->
## Enable sccache if available
<!-- KtF-->
```bash <!-- markdownlint-disable-line code-block-style -->
export RUSTC_WRAPPER=sccache
```
<!-- KtF-->
## Update outdated crates
<!-- KtF-->
- List and update installed crates
<!-- KtF-->
```bash <!-- markdownlint-disable-line code-block-style -->
#enable sccache if available
export RUSTC_WRAPPER=sccache
cargo list --update
```
<!-- KtF-->
<!-- KtF-->
>&nbsp;[!TIP] How does "cat << EOF" work in bash? [![alt text][1]](https://stackoverflow.com/questions/2500436/how-does-cat-eof-work-in-bash)
> <!-- -->
> ```bash
>cat <<EOF > print.sh
>#!/bin/bash
>echo \$PWD
>echo $PWD
>EOF
>```
<!-- -->
[1]: ./img/link_symbol.svg
