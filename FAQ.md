[Read Me](README.md) > FAQ

# Frequently Asked Questions

## Problem #1 
I'm getting following error(**macOS**):
> unable to set up TCP listener: Permission denied (os error 13) 

### Solution
Try to run http-to-https-letsencrypt with admin privileges.

## Problem #2 
I'm getting following error:
> unable to set up TCP listener: Address already in use (os error 48)


### Solution
Some application is already using port 80. 
Find out PID and stop it.

> sudo fuser 80/tcp # works on linux
> 
> sudo lsof -i :80 # works on macOS as well as on linux

## Problem #3
I started http-to-https-letsencrypt on http://127.0.0.1:80, 
but unable to query it from local network.

### Solution
Server is running on loopback device. Find out ip address 
of you network device and restart http-to-https-letsencrypt
using provided ip.

> ifconfig # find ip address macOS or linux
> 
> ipconfig #windows


## Problem #4
I see the following error in the console:
> unable to parse request: invalid utf-8 sequence of _n_ bytes from index _m_

### Solution
Server received not properly encoded request in UTF-8 charset. Request may be sent from various software on your network. You can ignore this message.


## Problem #5
I see the following error in the console:
> unable to parse request: Unable to parse method, request uri and http version

### Solution
Server received not valid request, for example it may contain a typo or [ASCII invisible control characters](https://en.wikipedia.org/wiki/Control_character). Request may be sent from various software on your network. You can ignore this message.

## Problem #6
I see the following error in the console(**Linux**):
> unable to set up TCP listener: Cannot assign requested address (os error 99) 
> 

### Solution
Most probably you are trying to start server on port 80. To start server on port 80 try to run it as an administrator or user with admin privileges.

## Problem #7
How do I start server on IPv6?

### Solution
Simply start server with -ip=:: (or -i=::).

## Problem #8
I have started server on ip=:: but unable to access it via fe80::... address.

### Solution
Try to access the server using IPv4 _inet_ address, from the same interface. Internally your IPv4 address will be converted to IPv6 variant [::ffff:192.168.m.n].

## Problem 9
I'm not able to connect to server, getting error:

> Failed to connect to 192.168.m.n port x after y ms: Connection refused

### Solution
Most likely firewall is blocking incoming request, try to stop firewall and retry.

## Problem 10
I'm not able to start server as root:

> Command not found

### Solution
Root does not have /usr/bin as part of his $PATH variable. Try to start server by explicitly specifying path to http-to-https-letsencrypt: _/usr/bin/http-to-https-letsencrypt_ 

## Problem 16
I'm trying to build http-to-https-letsencrypt from source and getting the error:

> linker 'cc' not found

### Solution
You need to install development tools:
> sudo dnf group install "Development Tools"  #RHEL and derivatives
>
> sudo yum install cmake make gcc #RHEL and derivatives


> sudo apt-get install build-essential # Ubuntu and derivatives
>
> sudo apt-get install make gcc cmake  # Ubuntu and derivatives

> sudo pacman -S base-devel # Arch Linux

## Problem 17
While building from IDE getting error:

> error[E0514]: found crate `NAME` compiled by an incompatible version of rustc

### Solution
Usually whenever such error encountered by me, I'm performing clean and build from the console, eliminating the built-in IDE compilation, and it works fine.

> cargo clean
>
> cargo build


## Problem 18
While building from IDE getting error:

> error: failed to get `NAME` as a dependency of package `NAME VERSION
> 
> failed to load source for dependency `rust-web-server`
> 
> Unable to update registry `crates-io`
> 
> failed to fetch `https://github.com/rust-lang/crates.io-index`
> 
> failed open - 'PATH.git/FETCH_HEAD' is locked: Permission denied; class=Os (2); code=Locked (-14)

### Solution
Usually whenever such error encountered by me, I'm performing clean and build from the console as an administrator, eliminating the built-in IDE compilation, and it works fine.

> sudo cargo clean
>
> sudo cargo build

## Problem 19
While getting sources getting an error:

> The following untracked working tree files would be overwritten by merge (checkout): Cargo.lock

### Solution
Delete `Cargo.lock`, it will be regenerated automatically.

> rm Cargo.lock

