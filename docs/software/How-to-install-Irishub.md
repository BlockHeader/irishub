# How to install IRIShub 

There are two ways to get Iris running on your server. You can download the binary files from our release pages, or you can download the source code and compile it locally.

#### Download Binary Directly

Go to the download page: 

https://github.com/irisnet/irishub/releases/  

then get the release v0.12.3 on your computer.

> Note: there are two different binaries available. One for testnet and the other for betanet.

`unzip -C /usr/local/bin  iris$VERSION.$OS-$ARCH.zip` to `/usr/local/bin/ ` 

You can verify you have the right version installed by running the following commands:

```
$ iris version
v0.12.3

$ iriscli version
v0.12.3
```

#### Compile Source Code

- Install Go 1.10+

```
$ sudo add-apt-repository ppa:gophers/archive
$ sudo apt-get update
$ sudo apt-get install golang-1.10-go
```

> Note that golang-1.10-go puts binaries in /usr/lib/go-1.10/bin. If you want them on your PATH, you need to make that change yourself.

Using snaps also works quite well:

```
This will give you the latest version of go
$ sudo snap install --classic go
```

> A restart is required for the command to be recognized.

Then you need to verify the versions of Go:

```
$ go version
go version go1.10.3 darwin/amd64
```

Then, you need to add `GOPATH` to system `PATH` , then your system could correctly compile the code.

Open your `.profile` in your home directory. Add the following lines at the end of file:

```
GOPATH=$HOME/go
PATH=$GOPATH/bin:$PATH
```

Save the file and exit the editor. Then run the following to make your bash reload your profile configurations.

```
$ source $HOME/.profile
```

Now you should see something like this if you echo your\$GOPATH and \$PATH variables

```
$ echo $GOPATH
/home/iris/go
$ echo $PATH
/home/isir/go/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

- Get the code and compile Iris

After setup Go correctly, you should be able to compile and run **Iris**.
Make sure that your server can access to google.com for that our project depends on some libraries provided by google.

* To compile for `testnet`:

```
mkdir -p $GOPATH/src/github.com/irisnet
cd $GOPATH/src/github.com/irisnet
git clone https://github.com/irisnet/irishub
cd irishub && git checkout v0.12.3
curl https://raw.githubusercontent.com/golang/dep/master/install.sh | sh
make get_tools
make get_vendor_deps
make all
```

* To compile for `betanet`:
```
mkdir -p $GOPATH/src/github.com/irisnet
cd $GOPATH/src/github.com/irisnet
git clone https://github.com/irisnet/irishub
cd irishub && git checkout v0.12.3
curl https://raw.githubusercontent.com/golang/dep/master/install.sh | sh
make get_tools
make get_vendor_deps
source scripts/setProdEnv.sh
make all
```

If your environment variables have set up correctly, you should not get any errors by running the above commands.
Now check your **Iris** version.

```
$ iris version
v0.12.3
$ iriscli version
v0.12.3
```
