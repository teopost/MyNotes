SSH login without password
===

1. Create public and private keys using ssh-key-gen on local-host
---

    teopost@local-host$ ssh-keygen
    Generating public/private rsa key pair.
    Enter file in which to save the key (/home/jsmith/.ssh/id_rsa):[Enter key]
    Enter passphrase (empty for no passphrase): [Press enter key]
    Enter same passphrase again: [Pess enter key]
    Your identification has been saved in /home/teopost/.ssh/id_rsa.
    Your public key has been saved in /home/teopost/.ssh/id_rsa.pub.
    The key fingerprint is:
    33:b3:fe:af:95:95:18:11:31:d5:de:96:2f:f2:35:f9 teopost@local-host
    
2. Copy the public key to remote-host using ssh-copy-id
---

    teopost@local-host$ ssh-copy-id -i ~/.ssh/id_rsa.pub remote-host
    teopost@remote-host's password:
    Now try logging into the machine, with "ssh 'remote-host'", and check in:
    
    .ssh/authorized_keys
    
    to make sure we haven't added extra keys that you weren't expecting.

Note: ssh-copy-id appends the keys to the remote-host’s .ssh/authorized_key.

3. Login to remote-host without entering the password
---

    teopost@local-host$ ssh remote-host
    Last login: Sun Nov 16 17:22:33 2008 from 192.168.1.2
    [Note: SSH did not ask for password.]
    
    teopost@remote-host$ [Note: You are on remote-host here]
