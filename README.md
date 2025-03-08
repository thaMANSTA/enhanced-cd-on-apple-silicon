# enhanced-cd-on-apple-silicon

thamansta@thaMANSTAs-Mac-mini ~ % diskutil list
/dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *251.0 GB   disk0
   1:             Apple_APFS_ISC Container disk1         524.3 MB   disk0s1
   2:                 Apple_APFS Container disk3         245.1 GB   disk0s2
   3:        Apple_APFS_Recovery Container disk2         5.4 GB     disk0s3
/dev/disk3 (synthesized):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      APFS Container Scheme -                      +245.1 GB   disk3
                                 Physical Store disk0s2
   1:                APFS Volume Macintosh HD            13.2 GB    disk3s1
   2:              APFS Snapshot com.apple.os.update-... 13.2 GB    disk3s1s1
   3:                APFS Volume Preboot                 9.6 GB     disk3s2
   4:                APFS Volume Recovery                1.5 GB     disk3s3
   5:                APFS Volume Data                    123.1 GB   disk3s5
   6:                APFS Volume VM                      4.3 GB     disk3s6
/dev/disk4 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *2.0 TB     disk4
   1:               Windows_NTFS Blue-2TB                2.0 TB     disk4s1
/dev/disk5 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:        CD_partition_scheme Tical                  *670.0 MB   disk5
   1:                      CD_DA                         41.8 MB    disk5s1
   2:                      CD_DA                         30.0 MB    disk5s2
   3:                      CD_DA                         33.5 MB    disk5s3
   4:                      CD_DA                         34.6 MB    disk5s4
   5:                      CD_DA                         36.1 MB    disk5s5
   6:                      CD_DA                         38.1 MB    disk5s6
   7:                      CD_DA                         23.8 MB    disk5s7
   8:                      CD_DA                         45.0 MB    disk5s8
   9:                      CD_DA                         27.6 MB    disk5s9
  10:                      CD_DA                         39.8 MB    disk5s10
  11:                      CD_DA                         38.4 MB    disk5s11
  12:                      CD_DA                         39.9 MB    disk5s12
  13:                      CD_DA                         35.3 MB    disk5s13
  14:                      CD_DA                         36.4 MB    disk5s14
  15:                      CD_DA                         52.0 MB    disk5s15
  16:     Apple_partition_scheme                         79.1 MB    disk5s16
  17:        Apple_partition_map                         1.0 KB     disk5s16s1
**  18:                  Apple_HFS                         73.3 MB    disk5s16s2 **

thamansta@thaMANSTAs-Mac-mini ~ % sudo mkdir /Volumes/EnhancedCD

thamansta@thaMANSTAs-Mac-mini ~ % brew install hfsutils

thamansta@thaMANSTAs-Mac-mini ~ % sudo hmount /dev/disk5s16s2 /Volumes/EnhancedCD/
Password:
Volume name is "METHOD" (locked)
Volume was created on Mon Apr 26 15:26:22 1999
Volume was last modified on Sat Feb 26 14:51:36 2000
Volume has 0 bytes free
thamansta@thaMANSTAs-Mac-mini ~ % ls -l /Volumes/EnhancedCD 
total 0


thamansta@thaMANSTAs-Mac-mini ~ % sudo hmount /dev/disk5s16 /Volumes/EnhancedCD/ 
/dev/disk5s16: contains 1 HFS partition
hmount: /dev/disk5s16: not a Macintosh HFS volume (Invalid argument)
thamansta@thaMANSTAs-Mac-mini ~ % ls -l /Volumes/EnhancedCD                     
total 0
thamansta@thaMANSTAs-Mac-mini ~ % ls -l /Volumes/EnhancedCD 
total 0
thamansta@thaMANSTAs-Mac-mini ~ % ls -l /Volumes/EnhancedCD
total 0
thamansta@thaMANSTAs-Mac-mini ~ % sudo ls -l /Volumes/EnhancedCD
total 0
thamansta@thaMANSTAs-Mac-mini ~ % umount /Volumes/Blue-2TB
thamansta@thaMANSTAs-Mac-mini ~ % 
thamansta@thaMANSTAs-Mac-mini ~ % sudo hmount /dev/disk5s161 /Volumes/EnhancedCD/
hmount: /dev/disk5s161: error opening medium (No such file or directory)
thamansta@thaMANSTAs-Mac-mini ~ % sudo hmount /dev/disk5s16s1 /Volumes/EnhancedCD/
hmount: /dev/disk5s16s1: volume is smaller than 800K (Invalid argument)
thamansta@thaMANSTAs-Mac-mini ~ % sudo hmount /dev/disk5s16s2 /Volumes/EnhancedCD/
Volume name is "METHOD" (locked)
Volume was created on Mon Apr 26 15:26:22 1999
Volume was last modified on Sat Feb 26 14:51:36 2000
Volume has 0 bytes free
thamansta@thaMANSTAs-Mac-mini ~ % hls -l /Volumes/EnhancedCD                
Failed to initialize HFS working directories: Permission denied
thamansta@thaMANSTAs-Mac-mini ~ % sudo hls -l /Volumes/EnhancedCD
hls: "/Volumes/EnhancedCD": no such file or directory
thamansta@thaMANSTAs-Mac-mini ~ % cd /Volumes/EnhancedCD
thamansta@thaMANSTAs-Mac-mini EnhancedCD % hls
Failed to initialize HFS working directories: Permission denied
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls
CLICKME                home.stk               ODCRf.mov              readme.txt
credits.stk            method.stk             QT1b.mov
Desktop Folder         METHODMA.MOV           QuickTime 3 Installer
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo su -
thaMANSTAs-Mac-mini:~ root# cd /Volumes/EnhancedCD/


thamansta@thaMANSTAs-Mac-mini EnhancedCD % hls                           
Failed to initialize HFS working directories: Permission denied
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls
CLICKME                Desktop Folder         method.stk             ODCRf.mov              QuickTime 3 Installer
credits.stk            home.stk               METHODMA.MOV           QT1b.mov               readme.txt
                                                                                                                   


thamansta@thaMANSTAs-Mac-mini EnhancedCD % ( sudo hls | xargs -I {} hcopy "{}" /tmp/TICAL )
Failed to initialize HFS working directories: Permission denied
Failed to initialize HFS working directories: Permission denied
Failed to initialize HFS working directories: Permission denied
Failed to initialize HFS working directories: Permission denied
Failed to initialize HFS working directories: Permission denied
Failed to initialize HFS working directories: Permission denied
Failed to initialize HFS working directories: Permission denied
Failed to initialize HFS working directories: Permission denied
Failed to initialize HFS working directories: Permission denied
Failed to initialize HFS working directories: Permission denied
thamansta@thaMANSTAs-Mac-mini EnhancedCD % ( sudo hls | xargs -I {} sudo hcopy "{}" /tmp/TICAL )
hcopy: "Desktop Folder": is a directory
hcopy: "QuickTime 3 Installer": is a directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % mkdir /tmp/TICAL/Desktop\ Folder/  
thamansta@thaMANSTAs-Mac-mini EnhancedCD % mkdir /tmp/TICAL/QuickTime\ 3\ Installer/
thamansta@thaMANSTAs-Mac-mini EnhancedCD % hcd Desktop Folder                                   
Failed to initialize HFS working directories: Permission denied
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd Desktop Folder
Usage: hcd [hfs-path]
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd Desktop\ Folder
thamansta@thaMANSTAs-Mac-mini EnhancedCD % ( sudo hls | xargs -I {} sudo hcopy "{}" /tmp/TICAL/Desktop\ Folder ) 
thamansta@thaMANSTAs-Mac-mini EnhancedCD % cd ../
thamansta@thaMANSTAs-Mac-mini /Volumes % cd EnhancedCD 
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd "QuickTime 3 Installer"
hcd: "QuickTime 3 Installer": no such file or directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd ".."       
hcd: "..": no such file or directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd QuickTime\ 3\ Installer
hcd: "QuickTime 3 Installer": no such file or directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hpwd
METHOD:Desktop Folder:
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd :METHOD:QuickTime\ 3\ Installer
hcd: ":METHOD:QuickTime 3 Installer": no such file or directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd :METHOD:QuickTime\ 3\ Installer:
hcd: ":METHOD:QuickTime 3 Installer:": no such file or directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd :METHOD:                        
hcd: ":METHOD:": no such file or directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd METHOD: 
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hpwd                                
METHOD:
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd METHOD:QuickTime\ 3\ Installer: 
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls
Install QuickTime?  Installer           QuickTime? Pieces   QuickTime? READ ME
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l
f  kajr/kajr    568720         0 Jul 30  1998 Install QuickTime?
f  APPL/kajr    197076         0 Aug 15  1997 Installer
d          2 items               Jul 30  1998 QuickTime? Pieces
f  ttro/ttxt      5991      4294 Jun  2  1998 QuickTime? READ ME
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l
f  kajr/kajr    568720         0 Jul 30  1998 Install QuickTime?
f  APPL/kajr    197076         0 Aug 15  1997 Installer
d          2 items               Jul 30  1998 QuickTime? Pieces
f  ttro/ttxt      5991      4294 Jun  2  1998 QuickTime? READ ME
thamansta@thaMANSTAs-Mac-mini EnhancedCD % ( sudo hls | xargs -I {} sudo hcopy -b "{}" /tmp/TICAL/QuickTime\ 3\ Installer/ )
hcopy: "Install QuickTime?": error opening destination file (Illegal byte sequence)
hcopy: "QuickTime? Pieces": is a directory
hcopy: "QuickTime? READ ME": error opening destination file (Illegal byte sequence)
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcopy Install* /tmp/TICAL/Install\ QuickTime                                
zsh: no matches found: Install*
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcopy "Install QuickTime?" /tmp/TICAL/Install\ QuickTime
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcopy "QuickTime? READ ME" /tmp/TICAL/QuickTime\ READ\ ME
thamansta@thaMANSTAs-Mac-mini EnhancedCD % hcd QuickTime? READ ME  
zsh: no matches found: QuickTime?
thamansta@thaMANSTAs-Mac-mini EnhancedCD % hcd "QuickTime? Pieces"
Failed to initialize HFS working directories: Permission denied
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd "QuickTime? Pieces"
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l
f  idcp/kakc      2916   6031462 Jul 30  1998 QuickTime?.compressed
f  APPL/ttxt    120400         0 May 30  1997 SimpleText
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcopy "QuickTime?.compressed" /tmp/TICAL/QuickTime\ Pieces/QuickTime.compressed
hcopy: "QuickTime?.compressed": error opening destination file (No such file or directory)
thamansta@thaMANSTAs-Mac-mini EnhancedCD % mkdir /tmp/TICAL/QuickTime\ Pieces
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcopy "QuickTime?.compressed" /tmp/TICAL/QuickTime\ Pieces/QuickTime.compressed
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcopy "SimpleText" /tmp/TICAL/QuickTime\ Pieces/          
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hpwd
METHOD:QuickTime 3 Installer:QuickTime? Pieces:
thamansta@thaMANSTAs-Mac-mini EnhancedCD % ls
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls
QuickTime?.compressed  SimpleText
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hcd METHOD:
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls
CLICKME                Desktop Folder         method.stk             ODCRf.mov              QuickTime 3 Installer
credits.stk            home.stk               METHODMA.MOV           QT1b.mov               readme.txt
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l
f  APPL/HSTU    963507         0 Feb 26  2000 CLICKME
f  Stak/HSTU       322     44246 Feb 20  2000 credits.stk
d          0 items               Feb 26  2000 Desktop Folder
f  Stak/HSTU       322     78770 Feb 21  2000 home.stk
f  Stak/HSTU       322    800546 Feb 21  2000 method.stk
f  MooV/TVOD         0  60682794 Jan 25  2000 METHODMA.MOV
f  MooV/TVOD      3003    628218 Jan 17  2000 ODCRf.mov
f  MooV/TVOD      1058   2312380 Oct 26  1999 QT1b.mov
d          4 items               Jul 30  1998 QuickTime 3 Installer
f  TEXT/ttxt      2716      1361 Feb 20  2000 readme.txt
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l "Desktop Folder"
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l "METHOD:Desktop Folder"
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l METHOD:Desktop\ Folder 
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l METHOD                
hls: "METHOD": no such file or directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l METHOD:QuickTime\ 3\ Installer/
hls: "METHOD:QuickTime 3 Installer/": no such file or directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l METHOD:QuickTime\ 3\ Installer:
f  kajr/kajr    568720         0 Jul 30  1998 Install QuickTime?
f  APPL/kajr    197076         0 Aug 15  1997 Installer
d          2 items               Jul 30  1998 QuickTime? Pieces
f  ttro/ttxt      5991      4294 Jun  2  1998 QuickTime? READ ME
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l METHOD:QuickTime\ 3\ Installer:QuickTime?\ Pieces: 
zsh: no matches found: METHOD:QuickTime 3 Installer:QuickTime? Pieces:
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l METHOD:QuickTime\ 3\ Installer:QuickTime\ Pieces: 
hls: "METHOD:QuickTime 3 Installer:QuickTime Pieces:": no such file or directory
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l METHOD:QuickTime\ 3\ Installer:QuickTime?\ Pieces:
zsh: no matches found: METHOD:QuickTime 3 Installer:QuickTime? Pieces:
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l METHOD:QuickTime\ 3\ Installer:QuickTime?\ Pieces:
\zsh: no matches found: METHOD:QuickTime 3 Installer:QuickTime? Pieces:
thamansta@thaMANSTAs-Mac-mini EnhancedCD % sudo hls -l METHOD:QuickTime\ 3\ Installer:QuickTime\?\ Pieces:
f  idcp/kakc      2916   6031462 Jul 30  1998 QuickTime?.compressed
f  APPL/ttxt    120400         0 May 30  1997 SimpleText

thamansta@thaMANSTAs-Mac-mini EnhancedCD % cd /tmp/TICAL

thamansta@thaMANSTAs-Mac-mini TICAL % brew install tree

thamansta@thaMANSTAs-Mac-mini TICAL % tree
.
├── CLICKME.bin
├── Desktop Folder
├── METHODMA.MOV
├── ODCRf.mov.bin
├── QT1b.mov.bin
├── QuickTime 3 Installer
│   ├── Install QuickTime
│   ├── Installer
│   ├── Installer.bin
│   ├── Installer.hqx
│   └── QuickTime Pieces
│       ├── QuickTime.compressed
│       └── SimpleText.bin
├── QuickTime READ ME
├── credits.stk.bin
├── home.stk.bin
├── method.stk.bin
└── readme.txt
4 directories, 15 files
thamansta@thaMANSTAs-Mac-mini TICAL % ls                                                             
thamansta@thaMANSTAs-Mac-mini TICAL % 
