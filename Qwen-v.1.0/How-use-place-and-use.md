#######################################################

1. Configuration Files (/etc/setfop)
File: /etc/setfop/setfop.conf
File: /etc/setfop/paths.conf
File: /etc/setfop/severity.rules

2. Data & State Files (/var/lib/setfop/ & /var/log/setfop/)
/var/lib/setfop/templates/baseline.yaml
/var/log/setfop/audit.log
/var/log/setfop/daemon.log

3. System Service File (/usr/lib/systemd/system/)
File: /usr/lib/systemd/system/setfopd.service

#######################################################

~~~~~~~~~~~~~~~~~ How to Initialize ~~~~~~~~~~~~~~~~~~

# 1. Reload systemd to recognize the new service file
sudo systemctl daemon-reload

# 2. Set strict permissions on config files (Root only)
sudo chmod 600 /etc/setfop/*.conf
sudo chown root:root /etc/setfop/*.conf

# 3. Ensure log directories are writable by root
sudo chown root:root /var/log/setfop
sudo chmod 755 /var/log/setfop

# 4. (Optional) Run a manual baseline generation if your binary supports it
# sudo /opt/setfop/bin/setfopd --generate-baseline

# 5. Start and Enable the daemon
sudo systemctl enable setfopd
sudo systemctl start setfopd

# 6. Check status
sudo systemctl status setfopd
