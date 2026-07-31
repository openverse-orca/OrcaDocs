# What to do if conda environment creation fails?

## Question
When installing OrcaLab, creating a Conda environment following the guide (e.g., `conda create -n orcalab python==3.12`) fails. What could be the causes and how can it be resolved?

## Answer

Conda environment creation failures are usually caused by network issues, Conda configuration problems, permission issues, or insufficient system resources. Below are common failure causes and their corresponding solutions.

## 🛠️ Common Failure Causes & Solutions

### 1. **Network Issues**

#### Symptoms
- Error messages such as "CondaHTTPError", "ConnectionError", "ResolvePackageNotFound".
- Downloading packages hangs or is extremely slow.

#### Solutions
- **Check Network Connection**: Ensure your computer can access the internet properly.
  ```bash
  ping www.baidu.com
  # If ping fails, check your network settings or router
  ```
- **Configure Conda Mirror**: Users in certain regions may experience slow or unstable connections to the Anaconda official source. Configuring a domestic mirror such as the Tsinghua TUNA source is recommended.
  ```bash
  # Add Tsinghua mirror source
  conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
  conda config --set show_channel_urls yes

  # Remove default sources (optional, but generally recommended)
  # conda config --remove channels defaults

  # Refresh Conda configuration
  conda clean --all
  ```
- **Verify Mirror Source**: Try accessing the mirror URL to ensure it is available.
  ```bash
  curl https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  # If HTML content is returned, the source is accessible
  ```
- **Disable SSL Verification** (not recommended, only as a temporary solution):
  ```bash
  conda config --set ssl_verify false
  # Try again; remember to revert after success: conda config --set ssl_verify true
  ```

### 2. **Conda Installation or Initialization Issues**

#### Symptoms
- Terminal shows `conda: command not found`.
- `conda activate` command is ineffective.

#### Solutions
- **Check Miniconda Installation**: Confirm Miniconda is correctly installed and its installation path has been added to the system's environment variables.
- **Initialize Conda**: If Miniconda is installed but Conda commands are ineffective, initialization may be needed.
  ```bash
  # Choose based on your shell type (bash or zsh, etc.)
  conda init bash
  # For zsh: conda init zsh

  # Refresh shell configuration
  source ~/.bashrc
  # For zsh: source ~/.zshrc
  ```
- **Manual Activation**: If `conda activate` still fails, try manual activation (assuming Miniconda is installed at `~/miniconda3`):
  ```bash
  source ~/miniconda3/etc/profile.d/conda.sh
  conda activate orcalab
  ```

### 3. **Python Version or Package Conflicts**

#### Symptoms
- Error messages such as "PackageNotFound" or "ConflictingDependencies".
- Specified Python version does not exist or conflicts with existing packages.

#### Solutions
- **Check if Python Version Exists**: The Conda repository may not have the exact Python version you specified. Try using a nearby version.
  ```bash
  # Try using 3.10 or 3.11
  conda create -n orcalab python=3.10
  ```
- **Simplify Environment Creation**: If complex dependency conflicts exist, create a Python environment first, then install dependencies.
  ```bash
  conda create -n orcalab python
  conda activate orcalab
  pip install orca-lab
  ```
- **Remove Old Environment**: If a same-named environment was previously created but failed, remove it first.
  ```bash
  conda env remove -n orcalab
  conda clean --all
  ```

### 4. **System Permission Issues**

#### Symptoms
- Error messages such as "Permission denied" or "Read-only file system".
- Unable to write files in the Conda installation directory.

#### Solutions
- **Check Installation Directory Permissions**: Ensure the Conda installation directory (typically `~/miniconda3`) and its subdirectories have write permissions for the current user.
- **Avoid Installing in System Directories**: Do not attempt to create Conda environments in system directories that require root privileges.

### 5. **Insufficient Disk Space**

#### Symptoms
- Error messages such as "No space left on device" or similar.

#### Solutions
- **Check Disk Space**: Ensure your hard drive has sufficient space.
  ```bash
  df -h  # View disk usage
  ```
- **Clean Conda Cache**:
  ```bash
  conda clean --all
  ```
- **Clean Up Unnecessary Old Environments**: Remove Conda environments that are no longer in use.
  ```bash
  conda env list  # View all environments
  conda env remove -n <env_name> # Remove specified environment
  ```

### 6. **Proxy Configuration Issues**

#### Symptoms
- Similar to network issues, but only occurs on corporate or school networks.

#### Solutions
- **Configure HTTP/HTTPS Proxy**:
  ```bash
  # Temporary setting
  export HTTP_PROXY="http://your_proxy_server:port"
  export HTTPS_PROXY="http://your_proxy_server:port"

  # Conda configuration
  conda config --set proxy_servers.http http://your_proxy_server:port
  conda config --set proxy_servers.https http://your_proxy_server:port
  ```

## 📝 Comprehensive Troubleshooting Recommendations

1. **Start with Logs**: Carefully read the error messages output by Conda commands; they usually indicate where the problem lies.
2. **Check One by One**: Follow the categories above, checking network, Conda environment, Python version, permissions, disk space, etc., one at a time.
3. **Google Search**: Copy the error message into a search engine; you can usually find many similar solutions.
4. **Seek Community Help**: If self-resolution is difficult, seek help on the Conda official forum, Stack Overflow, or the OrcaLab community, providing detailed error information and your operation steps.

Environment creation is the first step in installing OrcaLab. Resolving these common issues will ensure you can begin using OrcaLab smoothly.

## Related Links
- [OrcaLab Installation Guide](environment-setup/ubuntu-installation-guide-v1.0.md)
- [What is Miniconda? Why is it needed?](FAQ-list/020-what-is-miniconda-and-why-is-it-needed.md)