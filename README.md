# WARNING

**Never, ever just clone this repo and trust the pubkeys!
Use the GPG signature to validate it first!**

## GPG Key information

- GPG Key: 0x2EFAB48B
- Fingerprint: DBFF9099EDB0D28F6E46CCB5F8BDB1832EFAB48B
- Keyserver: keys.mozilla.org

## How to verify a key

    $ gpg --keyserver keys.mozilla.org --recv-keys 2EFAB48B
    $ gpg --verify rhubscher.sig rhubscher.pub

## The problem we try to solve

The storage team builds test/dev tools using one-off AWS
instances. Some of these tools become indispensable, yet, don't
warrant being monitored and managed by ops.

In the past, tools have broken down while their creators were on
vacation or unavailable, leading to bummer-times for everybody
involved--either sshing into a box while on PTO, or the tool just
being borked for days.

## The solution

This repo contains public keys for the storage team crew.

If toolmakers upload their fellow devs' pubkeys to a long-lived
awsbox, anybody can reboot or troubleshoot a downed machine when its
creator is out on vacation.

*Yay vacation.*

## How to use 

Only use the pubkeys verified with the storage team public key.

    $ gpg --verify rhubscher.sig rhubscher.pub


## When to use

If you create a tool on an awsbox that someone might need to maintain
while you're away, then you can upload the storage-team-pubkeys to that
awsbox and relax.

## How to update with new keys

File a Pull-Request to this repository and send an email with the
sha384sum of your key at storage-team@mozilla.com

Someone will validate the sha384sum and sign your public key with the
storage-team GPG key before merging your pull-request.

We trust github and git because you can't modify the keys without
resigning them with the right GPG key.


## How to sign the key

You first need the storage team secret key and password.

Then you can run:

    $ gpg --default-key 2EFAB48B  -o rhubscher.sig --detach-sign rhubscher.pub
