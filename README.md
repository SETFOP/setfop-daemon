# This is how the structure of setfoop-daemon will be.

/etc/setfop/                    # Configuration Directory (Root-owned)

├── setfop.conf                 # Main daemon configuration

├── paths.conf                  # Path definitions (what to monitor)

├── severity.rules              # Severity classification rules

└── certificates/               # For log signing (optional security)

/var/lib/setfop/                # State & Data Directory

├── templates/                  # SETFOP Template storage

│   ├── baseline.yaml           # Current baseline template

│   └── history/                # Historical templates (versioned)

├── cache/                      # Runtime state cache

│   └── inode_cache.db          # Quick lookup for inode states

└── checkpoints/                # Scan checkpoints for resume

/var/log/setfop/                # Log Directory

├── audit.jsonl                 # Main audit log (JSON Lines format)

├── daemon.log                  # Daemon operational logs

└── rotated/                    # Archived/rotated logs

/opt/setfop/                    # Binary & Executables

└── bin/

    └── setfopd                 # Main daemon binary

/usr/lib/systemd/system/        # Systemd Service Definition

└── setfopd.service             # Service unit file
