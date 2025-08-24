# rust sccache try out

- This repo shows how the crate sccache works and how much time it saves

>[!NOTE]
>Symbol to mark web external links [![alt text][1]](./README.md)
<!-- -->
>[!TIP]
>Get the link symbol with the curl command using the console
>
>>-m, --mode=MODE [![alt text][1]](https://www.man7.org/linux/man-pages/man1/mkdir.1.html) \
    set file mode (as in chmod), not a=rwx - umask
>><!-- -->
>>-p, --parents [![alt text][1]](https://www.man7.org/linux/man-pages/man1/mkdir.1.html) \
    no error if existing, make parent directories as needed,
    with their file modes unaffected by any -m option
><!-- -->
>```bash
># First make sure that the target directory exists
>mkdir -p ./img
>curl --create-dirs --output-dir img -O  "https://raw.githubusercontent.com/MathiasStadler/link_symbol_svg/360d1327d05280d53de5fa816c522f89a35891ca/img/link_symbol.svg"
>```
<!-- To comply with the format -->
FIXIT doesn't work
>[!TIP]
>Add the reference to the link image at the end of the Markdown file
<!-- -->
>```bash
> printf "\n<!-- Link sign - Don't Found a better way :-( - You know a better method? - send me a email -->\n[1]: ./img/link_symbol.svg\n"  >> ./project_path.md
>
>
>```
><!-- To comply with the format -->
## Start Date of project

```bash <!-- markdownlint-disable-line code-block-style -->
$ date
Sat Jun 14 10:26:08 AM CEST 2025
```

## OS-Version

```bash <!-- markdownlint-disable-line code-block-style -->
$ uname -a
Linux debian 6.1.0-28-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.119-1 (2024-11-22) x86_64 GNU/Linux
```

## BASH version used
<!-- To comply with the format -->
```bash
echo $BASH_VERSION
5.2.15(1)-release
```

FIXIT Not all necessary - Check it and update

## cargo install --list
<!-- To comply with the format -->
```text
cargo-audit v0.21.2:
    cargo-audit
cargo-binutils v0.3.6:
    cargo-cov
    cargo-nm
    cargo-objcopy
    cargo-objdump
    cargo-profdata
    cargo-readobj
    cargo-size
    cargo-strip
    rust-ar
    rust-cov
    rust-ld
    rust-lld
    rust-nm
    rust-objcopy
    rust-objdump
    rust-profdata
    rust-readobj
    rust-size
    rust-strip
cargo-edit v0.13.4:
    cargo-add
    cargo-rm
    cargo-set-version
    cargo-upgrade
cargo-llvm-cov v0.6.16:
    cargo-llvm-cov
cargo-nextest v0.9.94:
    cargo-nextest
cargo-tarpaulin v0.32.5:
    cargo-tarpaulin
evcxr_jupyter v0.19.0:
    evcxr_jupyter
grcov v0.10.0:
    grcov
rustfilt v0.2.1:
    rustfilt
```
<!-- To comply with the format -->
## Create for your own project a project folder in the Linux console (terminal ,bash shell), e.g. in your your own home directory, and then open this folder as a new project in the MS VSCODE program
<!-- To comply with the format -->
```bash <!-- markdownlint-disable-line code-block-style -->
# cd && mkdir <project_name folder> && cd $_
# command 'cd' change to home folder from logged in user
cd && mkdir rust-example-cov && cd $_
```
<!-- To comply with the format -->
## Init a new rust based project inside the previously generated folder
<!-- To comply with the format -->
```bash <!-- markdownlint-disable-line code-block-style -->
touch README.md \
&& ln -s README.md README \
&& cargo init "." \
&& cargo add rustfmt \
&& rustup component add rustfmt \
&& mkdir examples \
&& cp src/main.rs examples/example.rs \
&& sed -i -e 's/world/example/g' examples/example.rs \
&& rustup  show \
&& rustup  check \
&& rustup toolchain uninstall stable \
&& rustup toolchain install stable \
&& rustup update  --force \
&& rustup show \
&& mkdir tests
```
<!-- keep the format -->
## Show which toolchain is active
<!-- keep the format -->
```bash <!-- markdownlint-disable-line code-block-style -->
rustup show
# or better
rustup show |sed -n '/active toolchain/,/^$/p'
```
<!-- keep the format -->
>[!TIP]
>Delete all installed crates
<!-- To comply with the format -->
```bash <!-- markdownlint-disable-line code-block-style -->
cargo install --list |grep "^\s\s\s\s*" |xargs -n 1 echo "cargo uninstall " >/tmp/uninstall.txt
cargo install --list  |cut -d " " -f1 | grep -v "^$" |xargs -n 1 echo "cargo uninstall "
cargo install --list
```
<!-- To comply with the format -->

```text
cargo uninstall  cargo-audit
cargo uninstall  cargo-cov
cargo uninstall  cargo-nm
cargo uninstall  cargo-objcopy
cargo uninstall  cargo-objdump
cargo uninstall  cargo-profdata
cargo uninstall  cargo-readobj
cargo uninstall  cargo-size
cargo uninstall  cargo-strip
cargo uninstall  rust-ar
cargo uninstall  rust-cov
cargo uninstall  rust-ld
cargo uninstall  rust-lld
cargo uninstall  rust-nm
cargo uninstall  rust-objcopy
cargo uninstall  rust-objdump
cargo uninstall  rust-profdata
cargo uninstall  rust-readobj
cargo uninstall  rust-size
cargo uninstall  rust-strip
cargo uninstall  cargo-add
cargo uninstall  cargo-rm
cargo uninstall  cargo-set-version
cargo uninstall  cargo-upgrade
cargo uninstall  cargo-llvm-cov
cargo uninstall  cargo-nextest
cargo uninstall  cargo-tarpaulin
cargo uninstall  evcxr_jupyter
cargo uninstall  grcov
cargo uninstall  rustfilt
```
<!-- -->
>[!TIP]
>How to get the first word of a string and remove empty lines from output [![alt text][1]](https://unix.stackexchange.com/questions/65932/how-to-get-the-first-word-of-a-string)
><!-- -->
>```bash <!-- markdownlint-disable-line code-block-style -->
>cargo install --list |cut -d " " -f1 | grep -v "^$"
>```
<!-- To comply with the format -->
>[!TIP]
>Test if a command outputs an empty string [![alt text][1]](https://stackoverflow.com/questions/12137431/test-if-a-command-outputs-an-empty-string)
><!-- -->
>```bash<!-- markdownlint-disable-line code-block-style -->
>cargo install --list | grep  -c $0
>TODO Add hunan  readable output
>```
<!-- -keep the format -->
## Install sccache
<!-- keep the format -->
```bash<!-- markdownlint-disable-line code-block-style -->
cargo add sccache
```
<!-- keep the format -->
## How To Install sccache on Debian 12 - local system [![alt text][1]](https://installati.one/install-sccache-debian-12/)
<!-- keep the format -->
```bash<!-- markdownlint-disable-line code-block-style -->
cat /etc/os-release  |grep PRETTY_NAME
# PRETTY_NAME="Debian GNU/Linux 12 (bookworm)"
cat /etc/debian_version
# 12.11
# update
sudo apt-get update
# install sccache
sudo apt-get -y install sccache

```
<!-- keep the format -->
## Create and add config
<!-- keep the format -->
```bash<!-- markdownlint-disable-line code-block-style -->
# for user system wide
touch  ~/.cargo/config.toml

# config
cat > ~/.cargo/config.toml << 'EoF'
[build]
rustc-wrapper = "/usr/bin/sccache"
EoF
```
<!-- keep the format -->
## Sho statistic for sccache [![alt text][1]](/https://github.com/wasmerio/sccache)
<!-- keep the format -->
```bash<!-- markdownlint-disable-line code-block-style -->
sccache --show-stats
```

<!-- To comply with the format -->
<!-- Link sign - Don't Found a better way :-( - You know a better method? - send me a email -->
[1]: ./img/link_symbol.svg
