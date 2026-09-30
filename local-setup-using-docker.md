## 🚀 Open Source Local Setup Cheat Sheet

### 1. Key Terminology & Concepts

* **Forking:** Creating a copy of someone else's repository under your own GitHub account. This gives you write access to push changes and create Pull Requests (PRs) without modifying the original code directly.
* **Cloning:** Downloading the remote code repository from GitHub onto your local machine via Git.
* **`cd` (Change Directory):** A command-line instruction used to navigate into a specific folder in your terminal so commands execute inside that workspace.
* **Environment File (`.env`):** A file containing local configuration parameters (ports, API keys, database URLs). Projects provide a `.env.example` template that you copy to `.env` so sensitive variables remain local and aren't pushed to GitHub.
* **Docker & Docker Compose:**
* **Docker:** Runs applications inside isolated environments called containers (so you don't need to manually install Node, MongoDB, etc., on your host OS).
* **Docker Compose:** A tool for defining and running multi-container Docker applications (e.g., frontend server + backend server + database) using a single configuration file (`docker-compose.yml`).



---

### 2. Standard Open Source Local Setup Workflow

Follow these exact steps whenever setting up a new open source repository locally:

#### Step 1: Fork & Clone

1. Go to the project's GitHub page and click **Fork** (top right).
2. Open your local terminal / VS Code inside your target workspace directory.
3. Clone your forked repository:
```bash
git clone https://github.com/YOUR_USERNAME/PROJECT_NAME.git

```


4. Move into the project root directory:
```bash
cd PROJECT_NAME

```



#### Step 2: Configure Environment Variables

Copy the template configuration file to create your active local environment file:

* **Linux / Mac / Git Bash:**
```bash
cp .env.example .env

```


* **Windows Command Prompt:**
```cmd
copy .env.example .env

```



#### Step 3: Build & Start with Docker

1. **Build container images** (downloads dependencies, sets up DB and app layers):
```bash
docker-compose -f docker-compose-development.yml build

```


*(Or `docker compose -f docker-compose-development.yml build` for Docker Compose V2).*
2. **Boot up services:**
```bash
docker-compose -f docker-compose-development.yml up

```


3. **Access application:** Open your browser and go to `http://localhost:8000` (or whichever port is defined in `.env`).

---

### 3. Interview Talking Points

If asked in an interview about your open source experience or containerization knowledge, you can highlight:

* **Docker Compose for Development:** *"Instead of manually installing database instances (like MongoDB) and specific Node.js versions directly on my host system, I use Docker Compose to orchestrate isolated multi-container environments. This guarantees environment consistency across different developer machines."*
* **Open Source Workflow:** *"I follow the standard GitHub fork-and-clone workflow. I maintain upstream repository tracks while making modular changes on feature branches in my personal fork before opening pull requests."*
* **Configuration Management:** *"I manage local development configurations by deriving `.env` files from `.env.example` templates, ensuring environment specifics stay untracked in `.gitignore` to prevent credential exposure."*