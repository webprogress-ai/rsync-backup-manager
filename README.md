# Local Rsync Manager

**WordPress plugin v0.3.1** by **WebProgress.AI** for managing Windows/Cygwin rsync backup jobs from a local WordPress installation (e.g. LocalWP).

## Features

- Save multiple source/destination backup jobs and select rsync options.
- Export one Windows batch (`.bat`) script per job or a combined script for all jobs.
- Preview BAT scripts in the WordPress admin.
- Optionally run jobs, view progress, compare folders and open folders through the local Windows Python companion.

## Install plugin

1. Zip the `wp-rsync-manager` directory, preserving that top-level folder.
2. WordPress Admin → Plugins → Add New → Upload Plugin; upload the ZIP and activate.
3. Open **Rsync Manager** in the WordPress dashboard.

## Requirements

- Local WordPress site / LocalWP for the intended workflow.
- 64-bit Cygwin and `rsync` installed at `C:\cygwin64\bin\rsync.exe` for exported batch scripts.
- Python 3 for the optional Windows agent.

## Windows agent (optional)

The companion is not a WordPress plugin and is not needed for BAT exports.

1. Copy `windows-agent/rsync_agent.py` to `C:\LocalRsync\rsync_agent.py`.
2. Start with `py -3 C:\LocalRsync\rsync_agent.py --origin http://your-site.local` (replace with your local WordPress origin).
3. Keep it running and paste the printed agent token into the plugin's agent settings.

## Safety

The BAT export intentionally does not add `--delete`; destination-only files are retained. **Older destination files can still be overwritten.** Always try `--dry-run` on noncritical data first. Backups are not versioned. Keep the Python agent bound to localhost and never expose it to the public internet.

## Repository layout

- `wp-rsync-manager/`: installable WordPress plugin source
- `windows-agent/`: optional local Python companion
- `CHANGELOG.md`: release history

## Status

This repository package is assembled from v0.3.1 WordPress plugin and the v0.3.0 Windows companion. End-to-end Windows/LocalWP transfer functionality has not been verified in this environment.
