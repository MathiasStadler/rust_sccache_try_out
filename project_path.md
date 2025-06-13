# rust sccache try out

## This project shows how the Rust binary memory sccache significantly accelerates and optimizes the Rust build process

<!-- -->
>[!TIP]
>Fetch the link symbol from repo via command curl
>
>```bash
>curl --create-dirs --output-dir img -O  "https://raw.githubusercontent.com/MathiasStadler/link_symbol_svg/360d1327d05280d53de5fa816c522f89a35891ca/img/link_symbol.svg"
>```
<!-- To comply with the format -->
>[!TIP]
>Add the reference to the link image at the end of the Markdown file
<!-- -->
>```bash
> bash -c echo "\n\n<-- Link sign - Don't Found a better way :-( - You know a better method? - send me a email --> \n\n[1]: ./img/link_symbol.svg"  >> ./project_path.md
>
>
>```
><!-- -->

<!-- -->
>[!TIP]
> Don't forget to save your project on GitHub - saves you serious headaches
<!-- -->
## Create a new project folder and open it in the MS VSCODE program

```bash <!-- markdownlint-disable-line code-block-style -->
# cd && mkdir <project_name folder> && cd $_
# command 'cd' change to home folder from logged in user
set -o pipefail && \
project_name='test_project' && \
if [ -d ./$project_name ]; then echo "Folder already exits" ;else echo "Folder not exits"; echo "next"; fi; && \
echo "Create project => $project_name inside folder $(pwd)" && \
cd && \
mkdir ./$project_name && \
cd $_  && code . && \
unset $project_name && \
echo $?

[ -d ./$project_name ] && echo "Folder already exits" || echo "Folder not exits"


# set -o pipefail && \
set -euxo pipefail && \
project_name='test_project' && \
if [ -d ./$project_name ]; then echo "Folder already exits" ; \
else echo "Folder not exits"; \
echo "next"; \
echo "Create project => $project_name inside folder $(pwd)"; && \
cd; && \
mkdir ./$project_name; && \
cd $_  && code .; && \
fi;
unset $project_name; && \
echo $?;

# as script
cat <<EOF > /tmp/create_project.sh
# set -o pipefail 
set -euxo pipefail
project_name='test_project' 
if [ -d ./$project_name ]; then echo "Folder already exits" ; 
else echo "Folder not exits"; 
echo "next"; 
echo "Create project => $project_name inside folder $(pwd)"; && 
cd; && ´
mkdir ./$project_name;  
cd $_  && code .;
fi;
unset $project_name; 
echo $?;
EOF

```

>[!TIP]
>How do I check if a directory exists or not in a Bash shell script

## Init a new rust based project inside the previously generated folder
<!-- -->
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



<-- Don't Found a better way :-( - You know a better method? - send me a email --> 

[1]: ./img/link_symbol.svg
