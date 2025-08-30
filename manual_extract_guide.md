# Manual Extraction Guide

This guide explains how to use the new `/extract_manual` command to manually place files and trigger extraction through the Telegram bot.

## How It Works

The new `/extract_manual` command allows you to:
1. Manually place split archive files in the bot's merge directory
2. Trigger the extraction process through the Telegram bot
3. Get the same extraction and upload functionality as the regular merge command

## Step-by-Step Process

### Step 1: Prepare Your Files
1. Make sure you have all the split archive files (e.g., `file.001`, `file.002`, `file.003`, etc.)
2. Identify your user ID (you can find this by sending any message to the bot and checking the logs)

### Step 2: Place Files Manually
1. Create the directory structure: `{DOWNLOAD_LOCATION}/{your_user_id}/merge/`
   - Replace `{DOWNLOAD_LOCATION}` with the bot's download location (usually `/tmp` or similar)
   - Replace `{your_user_id}` with your actual Telegram user ID
2. Copy all your split archive files into this directory

Example:
```bash
mkdir -p /tmp/123456789/merge/
cp /path/to/your/files/*.001 /tmp/123456789/merge/
cp /path/to/your/files/*.002 /tmp/123456789/merge/
# ... copy all split files
```

### Step 3: Trigger Extraction
1. Send `/extract_manual` to the bot
2. The bot will:
   - Check if files exist in your merge directory
   - Identify the main archive file
   - Show you the file name and type
   - Present extraction options (🗂️ Normal / 🔐 Password protected)

### Step 4: Choose Extraction Mode
- **🗂️ Normal mode**: Extract without password
- **🔐 Password protected**: Extract with password (bot will ask for password)

### Step 5: Upload Files
After successful extraction:
- The bot will show you all extracted files
- You can choose to upload individual files or all files
- Files will be uploaded according to your upload mode settings

## Supported Archive Types

The bot supports:
- **RAR archives**: `.rar`, `.r01`, `.r02`, etc., or `.part1.rar`, `.part2.rar`, etc.
- **Volume archives**: `.001`, `.002`, `.003`, etc.

## Error Handling

The bot will show appropriate error messages if:
- No files are found in the merge directory
- No valid archive files are detected
- Extraction fails (wrong password, corrupted files, etc.)
- No files are extracted (password protected archives)

## Benefits

- **Faster processing**: Skip the Telegram download step
- **Better control**: You can verify files before extraction
- **Same functionality**: Get all the features of the regular merge command
- **Error recovery**: Easy to retry if something goes wrong

## Example Usage

```bash
# 1. Create directory
mkdir -p /tmp/123456789/merge/

# 2. Copy your split files
cp my_archive.001 /tmp/123456789/merge/
cp my_archive.002 /tmp/123456789/merge/
cp my_archive.003 /tmp/123456789/merge/

# 3. Send command to bot
/extract_manual

# 4. Choose extraction mode and follow prompts
```

## Notes

- The bot will automatically clean up temporary files after extraction
- Make sure you have sufficient disk space for extraction
- The extraction process is logged for monitoring
- You can cancel the process at any time using the ❌ button
