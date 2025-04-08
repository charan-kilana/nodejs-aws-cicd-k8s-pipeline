## ⚙️ Jenkins Global Tool Configuration

Follow these steps to configure Java, Node.js, SonarQube, and OWASP in Jenkins:

---

### 🔧 Configure Java, Node.js, SonarQube, and Dependency Check

Go to:  
**Dashboard → Manage Jenkins → Global Tool Configuration**

Set the following tool names and versions:

- **JDK Name:** `jdk17` (jdk-17.0.8.1+1)  
- **Node.js Name:** `node16` (NodeJs 16.2.0)  
- **Dependency Check Name:** `Dp-check` (dependency-check 6.5.1)  
- **SonarQube Scanner Name:** `sonar-scanner` (SonarQube Scanner 5.0.1.3006)

---
## 🐳 Install SonarQube using Docker

You can install SonarQube using the official Docker image from Docker Hub:

```bash
docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
```
![Docker installation from DockerHubScreenshot](docs/sonar_install.png)


1. **Create a user in SonarQube**
2. **Generate a token** for that user
3. **Add the token** to Jenkins under:  
   `Dashboard → Manage Jenkins → Credentials`
4. Then go to:  
   `Dashboard → Manage Jenkins → Configure System`
5. Under **SonarQube servers**, add a new instance using the token  
6. Click **Save**

---


### 🛡️ Install OWASP Dependency Check Plugin

1. Go to: `Dashboard → Manage Jenkins → Plugins`
2. Search for: `OWASP Dependency-Check`
3. Install it (**without restart**)

---

### 🔨 Configure OWASP Tool in Jenkins

After plugin installation, go to:  
`Dashboard → Manage Jenkins → Global Tool Configuration`

Add:

- **Name:** `Dp-check`  
- **Version:** `dependency-check 6.5.1`  
- **Source:** GitHub or internal mirror

