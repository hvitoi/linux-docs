# Storage

- Local storage
- SAN (Storage Area Network)
- NAS (Network Attached Storage)

- Create a new partition

```sh
fdisk /dev/sdx # n(ew)
mkfs.xfs /dev/sdx # Make the XFS filesystem
mount /dev/sdx1 /data # Mount
echo "/dev/sdb1 /data xfs defaults 0 0" >> /etc/fstab # Permanent mount
umount /data # Unmount
```

## Logical Volume Management (LVM)

- LVM allow multiple physical disks to be combined together
- The advantage is to easily add/remove new disks to a `volume group`

```sh
# Create a new partition
fdisk "/dev/sdx" # Create (n) a new primary (n) partition. Choose (t) LVM Linux type

# Create a physical volume (it's created on an existing partition)
pvcreate "/dev/sdx1"
pvdisplay

# Create volume group and assign it to a physical volume
vgcreate "volume-group" "/dev/sdx1"
vgdisplay "volume-group"

# Create a logical volume (attached to a volume group)
lvcreate -n "logical-volume" --size 1000M "volume-group"
lvdisplay

# Make filesystem
mkfs.xfs "/dev/vg/lv"

# Mount filesystem
mount "/dev/vg/lv" "/data"
df -h
```

- Extend a logical volume by adding a new physical volume to it

```sh
# Attach new hard disk
---

# Create a new partition
fdisk /dev/sdy # Create (n) a new primary (n) partition. Choose (t) LVM Linux type

# Create physical volume
vgcreate /dev/sdy1
pvs # or pvdisplay

# Extend a volume group
vgextend my-vg /dev/sdy1

# Extend a logical volume
lvextend -L+1024M /dev/mapper/my-vg-my-lg

# Extend the filesystem
xfs_growfs /dev/mapper/my-vg-my-lg
```

## RAID (Redundant Array of Independent Disks)

- If one disk dies, you have another disk! Redundancy!
- Types of RAID

  - `RAID 0`: One disk 5G + One disk 5G = 1 Composite 10G (No redundancy!)
  - `RAID 1`: One disk 5G + One disk 5G = 1 Composite 5G (Mirrored! Slow! Replication)
  - `RAID 5`: One disk 5G + One disk 5G + One disk 5G = 1 Composite 12G (Best)

- RAID is configured on the physical disks. And LVM is configured on logical disks
