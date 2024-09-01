## Setting Up SSH for GitHub on Linux

Follow these steps to set up SSH keys for GitHub access on your Linux machine.

### 1. **Test SSH Access to GitHub**

First, test if you can connect to GitHub via SSH:
```bash
ssh -T git@github.com
```
Type yes and then press Enter key.
If you don't have an SSH key set up, you'll see a warning or error message.
```plaintext
git@github.com: Permission denied (publickey).
```

### 2. **Generate a New SSH Key**

Generate a new SSH key using the `ed25519` algorithm:

```bash
ssh-keygen -t ed25519 -C "<your-email-address>"
```

- When prompted, type your password (or leave it blank for no password).
- The public key will be generated at `~/.ssh/id_ed25519.pub` with the following format:

```plaintext
ssh-ed25519 <long-key> <your-email-address>
```

### 3. **Copy the SSH Key to Your Clipboard**
To copy the contents of your SSH public key, use the cat command:
```bash
cat ~/.ssh/id_ed25519.pub
```
This will display the key in your terminal. Manually select and copy the output (which starts with ssh-ed25519).

### 4. **Add SSH Key to GitHub**

1. Log into GitHub.
2. Navigate to **Profile Icon > Settings**.
3. In the left panel, go to **Access > SSH and GPG keys**.
4. Click the **New SSH Key** button on the right.
5. Fill out the form:
   - **Title**: Any descriptive text.
   - **Key type**: Authentication Key.
   - **Key**: Paste the contents of `~/.ssh/id_ed25519.pub`.
6. Press the **Add SSH key** button at the bottom.

### 5. **Test SSH Connection to GitHub**

Test the connection again:

```bash
ssh -T git@github.com
```

You should see a message like:

```plaintext
Hi <your-user-name>! You've successfully authenticated, but GitHub does not provide shell access.
```

### 6. **Configure Git**

Set your global Git username and email:

```bash
git config --global user.name "<your-user-name>"
git config --global user.email "<your-email-address>"
```

### 7. **Clone a GitHub Repository**

You can now clone a GitHub repository using SSH:

```bash
git clone git@github.com:<repo-path>.git
```

## Reference Link
 - [How to setup SSH for GitHub repository](https://www.youtube.com/watch?v=snCP3c7wXw0)
