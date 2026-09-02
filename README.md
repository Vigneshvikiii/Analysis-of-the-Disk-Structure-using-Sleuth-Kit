#   Analysis-of-the-Disk-Structure-using-Sleuth-Kit

## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
## SAMPLE WORKFLOW (Windows)
```bash
# Step 1: View partitions
mmls.exe C:\forensics\disk.dd

# Step 2: View file system details
fsstat.exe -o 2048 C:\forensics\disk.dd

# Step 3: List files
fls.exe -r -o 2048 C:\forensics\disk.dd

# Step 4: Recover a file
icat.exe -o 2048 C:\forensics\disk.dd 6 > C:\forensics\image.jpg
```
## OUTPUT:
Disk Structure Analysis Results

<img width="625" height="410" alt="image" src="https://github.com/user-attachments/assets/4ecfcea5-c87f-4fc4-9c5e-fc15b8fe40e7" />

<img width="518" height="461" alt="image" src="https://github.com/user-attachments/assets/ce539c78-33a6-4675-ab62-09a4c86e28a1" />

<img width="637" height="462" alt="image" src="https://github.com/user-attachments/assets/3aa66174-4dd5-4180-ad9f-a771e4e574a0" />

<img width="637" height="458" alt="image" src="https://github.com/user-attachments/assets/c77d82ce-d4cf-407c-9a66-a30c4329386b" />

<img width="629" height="456" alt="image" src="https://github.com/user-attachments/assets/47251aee-c98a-4922-acc9-6e8d3b10c123" />

<img width="529" height="442" alt="image" src="https://github.com/user-attachments/assets/dac33f23-783f-4b08-822c-c081f322846a" />

<img width="487" height="451" alt="image" src="https://github.com/user-attachments/assets/f0789a76-62a9-4a0a-bf73-04b62fdb121b" />


<img width="422" height="450" alt="image" src="https://github.com/user-attachments/assets/34496fe2-1ae3-48b1-8cda-cbed2e0dbf1e" />

<img width="423" height="217" alt="image" src="https://github.com/user-attachments/assets/57c8d2d6-72e6-451e-86a0-feeafbf507ff" />

## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
