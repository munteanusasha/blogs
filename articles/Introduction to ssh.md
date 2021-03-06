>  ssh (SSH client) is a program for logging into a remote machine and for executing commands on a remote machine.  It is intended to provide secure encrypted communications between two untrusted hosts over an insecure network.

## Example

```bash
- Connect to a remote server:
  ssh username@remote_host

- Connect to a remote server with a specific identity (private key):
  ssh -i path/to/key_file username@remote_host

- Connect to a remote server using a specific port:
  ssh username@remote_host -p 2222

- Run a command on a remote server:
  ssh remote_host command -with -flags

- SSH tunneling: Dynamic port forwarding (SOCKS proxy on localhost:9999):
  ssh -D 9999 -C username@remote_host

- SSH tunneling: Forward a specific port (localhost:9999 to slashdot.org:80) along with disabling pseudo-[t]ty allocation and executio[n] of remote commands:
  ssh -L 9999:slashdot.org:80 -N -T username@remote_host

- SSH jumping: Connect through a jumphost to a remote server (Multiple jump hops may be specified separated by comma characters):
  ssh -J username@jump_host username@remote_host

- Agent forwarding: Forward the authentication information to the remote machine (see `man ssh_config` for available options):
  ssh -A username@remote_host
```

## Public key authentication

Local system has a cryptographic key pair - public key and private key. The server is configured to recognize the public key by adding it to [~/.ssh/authorized_keys](https://www.ssh.com/ssh/authorized_keys/). Anyone that has the corresponding private key will be granted access to the server.

## Client config setting

Instead of annoyingly typing

```ssh
ssh root@11.111.222.333 -p 2333
```

We can actually set the ssh config in `~/.ssh/config` with

```ssh
Host remoteServer           # host name alias that is easy to memorize
HostName 11.111.222.333     # host ip or host name
User root                   # user
Port 2333                   # port
IdentityFile ~/.ssh/id_rsa  # private key location
```

Then we can do the equivalent with easy typing:

```ssh
ssh remoteServer
```

