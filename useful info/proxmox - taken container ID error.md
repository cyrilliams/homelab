# Taken VM/CT ID Error in Proxmox

If you run into an error where you started the creation of a VM or CT and cancelled it mid creation and cannot use that same ID, try these steps from ChatGPT:


---


1. Check if the container actually exists (partially created)

On the Proxmox host:

pct list

If you see the CTID there (even stopped), delete it:

pct destroy <CTID>
2. Check the LXC config directory

Sometimes the config file remains even if the container doesn’t show in the GUI.

ls /etc/pve/lxc/

If you see something like:

101.conf

That means Proxmox still thinks the container exists.

Delete it manually:

rm /etc/pve/lxc/<CTID>.conf
3. Check storage for leftover container disk

Depending on your storage backend:

If using local-lvm:
lvs

Look for something like:

vm-101-disk-0

Remove it:

lvremove /dev/pve/vm-<CTID>-disk-0
If using directory storage (local):
ls /var/lib/lxc/
ls /var/lib/vz/images/

Delete any matching CTID folder:

rm -rf /var/lib/lxc/<CTID>
rm -rf /var/lib/vz/images/<CTID>
4. Check for lock files

Sometimes a lock remains if the task was interrupted:

ls /var/lock/lxc/

or:

ls /run/lock/lxc/

Remove any file referencing that CTID.

5. Verify no active tasks are stuck
ps aux | grep pct

or check the Proxmox GUI → Tasks

If something is stuck, kill it:

kill -9 <PID>
6. Final sanity check

After cleanup:

pct list
ls /etc/pve/lxc/

If the CTID is gone from both, you're good.

Quick shortcut (most common fix)

In most cases, this alone fixes it:

rm /etc/pve/lxc/<CTID>.conf
