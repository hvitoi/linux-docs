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
# 1 - Attach new hard disk
---

# 2 - Create partition
fdisk /dev/sdx # Create (n) a new primary (n) partition. Choose (t) LVM Linux type

# 3 - Create physical volumes
pvcreate /dev/sdx1 # Create volume of the partition
pvdisplay

# 4 - Create volume groups
vgcreate my-vg /dev/sdx1 # Assign vg to the partition
vgdisplay my-vg

# 5 - Create logical volumes
lvcreate -n my-lv --size 1000M my-vg
lvdisplay

# 6 - Make filesystem
mkfs.xfs /dev/my-vg/my-lv

# 7 - Mount filesystem
mount /dev/my-vg/my-lv /data
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
