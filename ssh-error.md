## 1. Verify Your SSH Key is Added to Your GitHub Account
##### A-\) Check if you have an SSH key:

* Run:
```bash
ls ~/.ssh
```
* Look for files named id_rsa.pub, id_ed25519.pub, or similar. If you don’t see these files, you may need to generate a new key.
##### B-\) Generate a new SSH key (if needed):

* If you don’t have an SSH key or you want to generate a new one, run:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
* Follow the prompts to save the key (default location is ~/.ssh/id_ed25519).
##### C-\) Add the SSH key to the SSH agent:

* Start the SSH agent:
```bash
eval "$(ssh-agent -s)"
```
* Add your SSH private key to the agent:
```bash
ssh-add ~/.ssh/id_ed25519
```
##### D-\) Add your SSH key to GitHub:

* Copy the SSH public key to your clipboard:
```bash
cat ~/.ssh/id_ed25519.pub
```
* Go to GitHub SSH and GPG keys settings.
* Click "New SSH key", paste your key into the "Key" field, and give it a title.
* Click "Add SSH key" to save.
## 2. Test the SSH Connection
##### A-\) Test your SSH connection again:
* Run:
```bash
ssh -T git@github.com
```
* You should see a message like:
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```
## 3. Update Your Git Remote URL (if needed)
##### A-\) Make sure your remote URL is set to use SSH:
* Check the current remote URL:
```bash
git remote -v
```
* If it’s using HTTPS, update it to use SSH:
```bash
git remote set-url origin git@github.com:YourUsername/YourRepo.git
```
* Verify the new URL:
```bash
git remote -v
```
## 4. Retry Your Git Operations
##### A-\) Try pushing your changes again:
```bash
git push -u origin main
```
These steps should help you resolve the SSH connection issue with GitHub. If you encounter any errors along the way, please share them, and I'll help you troubleshoot further.