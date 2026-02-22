# Log Rotation script
``` bash
#!/bin/bash

# Check argument
if [ $# -eq 0 ]; then
  echo "Usage: $0 <log_directory>"
  exit 1
fi

LOG_DIR=$1

# Check directory exists
if [ ! -d "$LOG_DIR" ]; then
  echo "Error: Directory does not exist"
  exit 1
fi

# -------- Compress logs older than 7 days --------
old_logs=$(find "$LOG_DIR" -type f -name "*.log" -mtime +7)

compress_count=$(echo "$old_logs" | grep -c .)

if [ "$compress_count" -gt 0 ]; then
  echo "$old_logs" | xargs gzip
fi

# -------- Delete gz older than 30 days --------
old_gz=$(find "$LOG_DIR" -type f -name "*.gz" -mtime +30)

delete_count=$(echo "$old_gz" | grep -c .)

if [ "$delete_count" -gt 0 ]; then
  echo "$old_gz" | xargs rm -f
fi

# -------- Output --------
echo "Files compressed: $compress_count"
echo "Files deleted: $delete_count"
```
# Backup
``` bash
#!/bin/bash
<<readme
usage = ./backup.sh <path to source directory> <path to backup directory>
readme

display_usage(){
                echo "usage = ./backup.sh <path to source directory> <path to backup directory>"
                exit 1
        }
if [ $# -lt 2 ];then
        display_usage
fi

source_dir=$1
timestamp=$(date '+%Y-%m-%d-%H-%M-%S')
backup_dir=$2

if [ ! -d "${source_dir}" ]; then
        echo "Error: Source directory does not exist"
        exit 1
fi
archive="${backup_dir}/backup_${timestamp}.tar.gz"

create_backup(){
        tar -czvf "${archive}" "${source_dir}" > /dev/null

if [ $? -eq 0 ]; then
        echo "backup generated successfully for ${timestamp}"
else
        echo "Backup failed"
        exit 1
fi
}

create_backup

size=$(du -h "$archive" | cut -f1)
echo "backup created : $archive"
echo "Archive size : $size"

del_backup(){
        find "$backup_dir" -type f -name "backup-*.tar.gz" -mtime +14 -delete
        if [ $? -eq 1 ];then
                echo "old backups cleaned (older than 14 days)"
        fi
}

del_backup
```
