Great! Now that you've successfully uploaded your project to GitHub, you can use the following **Markdown formula** with Git commands for any future project you want to upload to GitHub. This formula will work for any folder, assuming you've already created a repository on GitHub.

Here's a Markdown template with the Git commands you need:


# Steps to Upload Your Project to GitHub

1. **Navigate to your project folder in PowerShell or terminal**:
   ```bash
   cd C:\path\to\your\project\folder


2. **Initialize Git in your folder**:
   ```bash
   git init
   ```

3. **Add the remote repository** (replace the URL with your GitHub repository URL):
   ```bash
   git remote add origin https://github.com/yourusername/your-repository.git
   ```

4. **Stage all files for commit**:
   ```bash
   git add .
   ```

5. **Commit your changes**:
   ```bash
   git commit -m "Initial commit"
   ```

6. **Pull changes from GitHub to merge any existing files (e.g., README, LICENSE)**:
   ```bash
   git pull origin main --allow-unrelated-histories
   ```

   *If there are conflicts, resolve them, and then commit the resolved files.*

7. **Push your changes to the remote GitHub repository**:
   ```bash
   git push -u origin main
   ```



### Notes:
- Make sure your repository is already created on GitHub before running the commands.
- Replace `yourusername` and `your-repository` with your actual GitHub username and repository name.
- If you're not using the `main` branch, replace `main` with the name of the branch you're working with.


### Explanation:
- The `git init` command initializes a Git repository in the folder.
- The `git remote add origin` command connects your local project to the GitHub repository.
- The `git add .` command stages all your files to be committed.
- The `git commit -m "message"` commits the changes with a descriptive message.
- The `git pull origin main --allow-unrelated-histories` command helps integrate any existing files in the remote repository, such as a README or LICENSE, into your local repository.
- The `git push -u origin main` pushes your local commits to the remote GitHub repository.

### When using this formula, replace the relevant parts with your own project folder path, GitHub repository URL, and branch name as needed.

This formula will work for any future project you want to upload to GitHub. Just follow the steps, and you're good to go!



The issue you're encountering is related to authentication when pushing to GitHub. GitHub has discontinued the use of username and password for authentication over HTTPS, so you need to authenticate using a personal access token (PAT).

Here are the steps to resolve the issue:

### Step 1: Create a Personal Access Token (PAT)
1. Go to GitHub: [GitHub Personal Access Token](https://github.com/settings/tokens).
2. Click on **Generate new token**.
3. Select the necessary scopes for your token (at least **repo** to push and pull to repositories).
4. Click **Generate token**.
5. **Copy the token** and store it somewhere secure. You won’t be able to view it again.

### Step 2: Update Remote URL with Token
You need to use the token for authentication instead of a password.

1. Run the following command to remove the existing remote URL:
   ```bash
   git remote remove origin
   ```

2. Now, add the remote again but include your token in the URL like so:
   ```bash
   git remote add origin https://<YOUR_TOKEN>@github.com/daiwik-project/MAD-1-Project.git
   ```

   Replace `<YOUR_TOKEN>` with your actual GitHub personal access token.

### Step 3: Push Changes
Now that the remote is set with the token, you can push your changes:
```bash
git push -u origin main
```

### Alternative Step: Use SSH Instead of HTTPS
If you prefer to avoid using a token every time, you can set up SSH authentication:
1. [Generate SSH Key](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh) and add it to your GitHub account.
2. Change the remote URL to SSH:
   ```bash
   git remote set-url origin git@github.com:daiwik-project/MAD-1-Project.git
   ```
3. Now, you can push using SSH without needing to enter a token each time:
   ```bash
   git push -u origin main
   ```

Let me know if you need further clarification!
