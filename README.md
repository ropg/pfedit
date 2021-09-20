# pfedit
 
Editing `/etc/pf.conf` on FreeBSD or derivatives can be harrowing as you run the risk of locking yourself out of your server. But it's 2021 and there's no need for one stupid mistake to cause problems like that. This script implements the same protection found on many routers (Cisco, Juniper, ...): it adds a second time you have to press enter to prove you didn't just lock yourself out. If you did, pfedit reverts to the old configuration.

When you run `pfedit`, it shows a copy of `pf.conf` (called `pf.conf.new`) in the editor you set in `$EDITOR`. After you're done editing, you'll see: 

```text
Press enter to use new rules or Ctrl-C to abort.
Press enter again if you're still there.
OK, keeping new PF config. Previous config is in /etc/pf.conf.old.
```

If you do not press that second enter within 10 seconds (or your terminal disconnects):

```text
Press enter to use new rules or Ctrl-C to abort.
Press enter again if you're still there.
Reverting to previous PF config. Yours saved in /etc/pf.conf.new.
```

&nbsp;

### Needs bash

`nohup` and `read` somehow didn't work the way I wanted in `/bin/sh`. Should probably be investigated/fixed so that it runs in `/bin/sh` if this ever gets a man page and gets submitted and all.
