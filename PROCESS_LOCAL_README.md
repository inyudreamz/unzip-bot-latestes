# Process Local Files Feature

## Overview

The `/process_local` command allows you to skip the download phase and directly trigger the extraction and upload process for archive files that are already present on the server.

## Usage

### Command Syntax
```
/process_local /path/to/your/archive.zip
```

### Example
```
/process_local /home/user/downloads/my_archive.zip
```
/process_local /app/local_unzip_dir
## Features

### What it does:
1. **Skips Download**: No need to upload files to Telegram first
2. **Direct Processing**: Immediately starts extraction process
3. **Same Upload Flow**: Uses the same extraction and upload logic as regular files
4. **Admin Only**: Restricted to bot owner for security

### Supported Archive Formats:
- `.zip` - ZIP archives
- `.rar` - RAR archives  
- `.7z` - 7-Zip archives
- `.tar` - TAR archives
- `.gz` - Gzip compressed files
- `.bz2` - Bzip2 compressed files
- `.xz` - XZ compressed files
- `.zst` - Zstandard compressed files
- `.001`, `.002`, `.003` - Split archive parts

## Workflow

1. **File Validation**: Checks if file exists and is a valid archive format
2. **Space Check**: Verifies sufficient disk space for extraction
3. **File Move**: Moves the file to user's working directory (saves disk space)
4. **Extraction**: Extracts the archive using appropriate tools (7zip, unrar, etc.)
5. **File Selection**: Shows extracted files for user to select
6. **Upload**: Uploads selected files to Telegram

## Security

- **Admin Only**: Only the bot owner can use this command
- **Path Validation**: Validates file paths to prevent directory traversal
- **Format Check**: Only processes known archive formats
- **Space Limits**: Respects disk space limits

## Error Handling

The command includes comprehensive error handling for:
- File not found
- Invalid file paths
- Insufficient disk space
- Unsupported file formats
- Extraction failures
- Permission issues

## Integration

This feature integrates seamlessly with the existing bot architecture:
- Uses the same extraction functions (`extr_files`)
- Follows the same upload workflow
- Respects user preferences (upload mode, thumbnails)
- Maintains task tracking and cleanup

## Use Cases

- **Batch Processing**: Process multiple archives without uploading each one
- **Server Files**: Extract archives that were uploaded via other means
- **Testing**: Quickly test extraction functionality with local files
- **Automation**: Integrate with scripts that place files on the server

## Limitations

- Admin access required
- Files must be accessible from the bot's working directory
- Same size limits as regular uploads apply
- Requires manual file placement on server
