1. Navigate the Filesystem
pwd : Print Working Directory (shows your current path, e.g., /home/username).

ls : List files and folders in the current directory.

ls -l : Detailed view (shows permissions, owner, size, and timestamp).

ls -la : Includes hidden files (files starting with a .).

cd /etc : Move into the system configuration directory.

cd ~ or cd : Jump straight to your home folder.

cd .. : Move up one level in the directory tree.




2. Create and Delete Files & Folders
mkdir ~/security-practice : Create a practice folder in your home directory.

touch file1.txt notes.log : Create empty files.

echo "Hello" > file1.txt : Write text to a file (overwrites existing content).

echo "Line 2" >> file1.txt : Append text to the end of a file.

cat file1.txt : Display the entire contents of a file.

cp file1.txt backup.txt : Copy a file.

mv file2.txt renamed.txt : Move or rename a file.

rm renamed.txt : Delete a file.

rm -rf old-folder/ : Force delete a folder and everything inside it.


3. Search Inside Files (grep & find)
grep "Hello" file1.txt : Search for a specific word inside a file.

grep -i "hello" file1.txt : Case-insensitive search.

grep -r "root" /etc/ : Recursively search for a string across all files in a directory.

find /home -name "*.txt" : Locate files matching a specific name pattern.

find / -user root -type f : Find all regular files owned by the root user.

find /tmp -newer /etc/passwd : Find files in /tmp modified after the passwd file.


Day 4: Processes, Services & Persistence
⚡ 1. Process Monitoring & Triaging
ps aux : Snapshot of all currently running processes across all users.

top or htop : Real-time interactive process monitoring (press q to exit).

pgrep sshd : Quickly find the Process ID (PID) of a specific service.

kill 1234 : Send a graceful termination signal (SIGTERM) to PID 1234.

kill -9 1234 : Force kill (SIGKILL) an unresponsive process immediately.

👾 Malware Hunting: When investigating a suspected breach, run ps aux to look for anomalies, such as unrecognized binaries executing out of temporary directories like /tmp.

🌐 2. Services & Network Auditing
sudo systemctl status ssh : Check if the SSH daemon is actively running.

sudo systemctl start|stop|restart apache2 : Manage web server states.

sudo systemctl enable|disable ssh : Toggle whether a service launches automatically at boot.

ss -tulnp : View open network ports and active connections with associated PIDs.

ss -tulnp | grep LISTEN : Filter out everything except ports actively listening for inbound traffic.

⏳ 3. Persistence Inspection (Cron Jobs)
Attackers establish persistence on systems by scheduling tasks. Check these locations regularly:

crontab -l : View cron jobs scheduled for your current user.

sudo crontab -l -u root : View cron jobs scheduled directly under the root account.

cat /etc/crontab : Inspect system-wide cron configurations.

ls /etc/cron.d/ : Check the system drop-in directory for automated execution scripts.
