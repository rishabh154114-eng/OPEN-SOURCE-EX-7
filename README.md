# OPEN-SOURCE-EX-7
# Name:T.Rishabh srivatsav
# Reg no:25001966

# AIM :

To create a logical volume named lv_app_logs on the vg_backup volume group with 50 extents, format it using ext3, and mount it under /production.

# STEPS INVOLVED :

<h2>STEP 1:</h2>
Create the physical volume

sudo pvcreate /dev/sdb


<h2>STEP 2:</h2>
Create the volume group vg_backup with 8MiB extent size

sudo vgcreate -s 8M vg_backup /dev/sdb


<h2>STEP 3:</h2>
Verify the PE size

vgdisplay vg_backup | grep "PE Size"


<h2>STEP 4:</h2>
Create logical volume lv_app_logs with 50 extents

sudo lvcreate -l 50 -n lv_app_logs vg_backup


<h2>STEP 5:</h2>
Format the LV with ext3 filesystem

sudo mkfs.ext3 /dev/vg_backup/lv_app_logs


<h2>STEP 6:</h2>
Create mount point

sudo mkdir /production


<h2>STEP 7:</h2>
Mount the logical volume

sudo mount /dev/vg_backup/lv_app_logs /production


<h2>STEP 8:</h2>
Verify the mounted filesystem

df -h /production


<h2>STEP 9:</h2>
Make the mount permanent

echo "/dev/vg_backup/lv_app_logs /production ext3 defaults 0 0" | sudo tee -a /etc/fstab

# OUTPUT :

<img width="424" height="145" alt="image" src="https://github.com/user-attachments/assets/784cbeba-ba87-43fc-a4b5-05a1b450be1e" /> </br>
# Result :
This expirement has done succesffully
