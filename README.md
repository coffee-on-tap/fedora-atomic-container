# README

### Operating System

- https://fedoraproject.org/atomic-desktops/silverblue/

### Pre-requisite packages

| Package        | Source          | URL |
| -------------- | --------------- | ----------------------------- |
| toolbx         | Included        | https://containertoolbx.org/  |
| Podman Desktop | Software Center | https://podman-desktop.io/    |

### Create toolbox
- Use included toolbx to create a container, by default uses the same OS as host - this is what I do below:

```bash
toolbx create github-dev
```

### Enter the container
```bash
toolbx enter github-dev
```

- The terminal will change to reflect entering the container, else you can verify the container is initialized in Podman Desktop
- If using VS Code, remotely connect to the container - any conda environments you installed in the host are available in /var/home/atomic/PATH/TO/CONDA
- I find this method convenient for me, I spin up a venv in my working directory and pip install other requirements there
- Drop a .gitignore to avoid uploading everything to Github

### Installing software inside container
- Once inside the container, installation procedes at the package level so familiar tools like dnf work
- Like Docker, anything installed here is *only* in the container

```bash
sudo dnf group install "Development Tools"
sudo dnf install gcc-gfortran
sudo dnf install lapack-devel-3.11.0-5.fc39.x86_64 openblas-devel-0.3.21-6.fc39.x86_64
```

### How I want to use conatinerization
- Jump between dev environments with clashing dependencies with the same ease as I do just shifting focus from one project to another
- Isolate conda/pip and system level packages to the development space while making no changes to the host (increased stability)
- Easily document and save environments to use elsewhere (e.g., HPC, Google Cloud, Azure, AWS)

### Important note
- This is my first week with Atomic after 15 years of a more traditional Linux experience, still figuring things out.
- Have fun learning!
