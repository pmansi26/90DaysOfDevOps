# 1.What ConfigMaps and Secrets are and when to use each
## ConfigMap:
Stores non-sensitive configuration data (e.g., app settings, config files).

## Secret:
Stores sensitive data (e.g., passwords, API keys).

## When to use
- Use ConfigMap for general configuration
- Use Secret for confidential data
  
# 2.Difference between Environment Variables and Volume Mounts

| Feature              | Environment Variables                     | Volume Mounts                          |
|---------------------|--------------------------------------------|----------------------------------------|
| Data Access         | Accessed via env variables (`$VAR`)        | Accessed as files in filesystem        |
| Source              | ConfigMap / Secret                         | ConfigMap / Secret                     |
| Update Behavior     | Requires Pod restart to reflect changes    | Updates automatically (live)           |
| Use Case            | Small config values                        | Large configs / files                  |
| Visibility          | Visible in process environment             | Visible as files inside container      |
| Example             | DB_USER=admin                              | /etc/config/DB_USER file               |

# 3.Why Base64 is Encoding, Not Encryption

Base64 is encoding because it simply converts data into another format using a standard algorithm. It does not provide any security.

Anyone can easily decode Base64 back to the original data without any key, which means the data is not protected.

Encryption, on the other hand, uses a secret key to secure data so that only authorized users can access it.

# 4.How ConfigMap updates propagate to volumes but not env vars
## ConfigMap Updates: Volume vs Environment Variables

### Volume Mounts
- ConfigMap data is mounted as files inside the container  
- Updates are reflected automatically (live updates)  
- No Pod restart required  

### Environment Variables
- Values are set only at container startup  
- Changes in ConfigMap are not reflected automatically  
- Pod restart is required to get updated values

# Screenshot of configmap , secrets , pods running

