# ⚓ Cirdan

In this repository you will find instructions on how to build our on-board software [melvin-ob](https://github.com/CIARC-CUIYC/melvin-ob) alongside our own SiL-Framework [Palantíri](https://github.com/CIARC-CUIYC/Palantiri) in an isolated Docker Compose Scenario for quick, platform-independent deployment, testing and debugging.

---
## ✅ Dependencies
Before following the Setup instructions from this repository please make sure that you have the following dependencies installed on your system:
* Docker, please follow the official [instructions](https://docs.docker.com/engine/install/) for your target hardware.
* Git for cloning the repositories, please follow the official [instructions](https://git-scm.com/downloads) for your target hardware

## 🔨 Setup Instructions

1. **Clone the Palantiri repository**
   ```bash
   git clone  https://github.com/CIARC-CUIYC/Palantiri.git
   cd Palantiri
   ```

2. **Build the Palantiri Docker image**
    ```bash
   docker build -t sil-adapter:latest .
   ```

2. **Clone the melvin-ob repository**
   ```bash
   git clone https://github.com/CIARC-CUIYC/melvin-ob.git
   ```

3. **Build the melvin-ob Docker image**
   ```bash
   docker build -t melvin-ob:latest .
   ```

4. **Clone the Cirdan repository and orchestrate**
   ```bash
   git clone https://github.com/CIARC-CUIYC/cirdan.git
   cd cirdan
   docker compose up
   ```

5. **Connect to melvin-ob and start the SuT**
    > [!IMPORTANT]  
    > The Palantiri Flask Webserver needs a few seconds too boot up. You can monitor this in the same terminal where you executed the 
    > previous commands.
    ```bash
   docker exec -it cirdan-melvin-ob-1
   tmux attach
   ./melvin-bin
   ```

## 📖 Further Resources
For further information on how to use Palantiri or the on-board software melvin-ob please consult the corresponding repositories.