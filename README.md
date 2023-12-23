# File Encryption System Documentation

## Introduction

Welcome to the documentation for the File Encryption System. This system is designed to provide secure and efficient file, folder, and text encryption, allowing users to manage their encrypted data seamlessly. The system is built using a modular monolithic architecture and utilizes technologies such as Django REST framework, Redis, Celery, PostgreSQL, Silk, and DataDog.

## User Workflow and Activities

### 1. User Registration and Key Generation:

- Users register on the platform.
- A unique encryption key is generated for the user during registration.
- The key is securely stored, potentially using a dedicated hardware module or user-managed key approach.

### 2. File, Folder, or Text Encryption:

- Users interact with the system to choose between file, folder, or text encryption.
- For folder encryption, a recursive process handles files within the folder.
- The system maintains the folder structure during encryption.

### 3. File Upload and Encryption:

- Users upload files, folders, or input text for encryption.
- A unique key is generated for each file or folder.
- Files and folders are encrypted using a strong symmetric encryption algorithm (e.g., AES).
- Encrypted content and metadata (filename, hashed key, user ID) are stored in the database.

### 4. File and Key Sharing:

- Users have the option to share encrypted files with others.
- Secure mechanisms are in place for sharing files, such as generating temporary links or requiring user authentication for access.
- Users can securely share encryption keys with trusted individuals.

### 5. File Retrieval and Decryption:

- Users log in securely.
- They select a file for retrieval.
- During retrieval, the user inputs their encryption key.
- The input key is hashed and compared to the stored hash in the database.
- If the keys match, the original key is used to decrypt the file.

### 6. Secure Download Options:

- Users have options to securely download the decrypted file.
- Secure temporary links or direct download options are provided.

### 7. Optional Email Integration:

- Users can choose to receive decrypted files via email.
- Secure email protocols and end-to-end encryption are considered for email communication.

### 8. User Workspace and Team Collaboration:

- After registration, users can create workspaces and add team members.
- Team members can access encrypted files within the workspace.
- Workspace collaboration is secured with individual user authentication.

### 9. Scheduled Encryption and Decryption:

- Users can schedule the time and date for file encryption or decryption.
- During the file upload process, users have the option to set a specific time and date for the encryption to occur automatically.
- For decrypted files, users can schedule when the decryption process should take place.
- The scheduling feature enhances user control and ensures that encryption or decryption aligns with their preferred timelines.

### 10. Notification System:

- A notification system informs users about the scheduled encryption or decryption events.
- Users receive alerts in advance to confirm or modify scheduled tasks.
- Notifications may include details such as the file name, scheduled time, and the current status of the task.

### 11. User-Controlled Key Management:

- Users can manage and rotate their encryption keys.
- Users are educated on best practices for key management.

### 12. File Management and Tagging:

- Users can organize and manage their encrypted files through a comprehensive file management system.
- Tagging functionality allows users to add descriptive tags to files for easy tracking and searching.

### 13. Size Limits and Communication:

- Size limits are implemented for uploads to manage server resources.
- Clear communication of size limits to users.
- Secure communication channels are maintained throughout the process.

### 14. User Limits for Free Accounts:

- Free users are limited in the number of encryption keys they can generate per month.
- There are file size limits imposed on uploads for free users.
- A total storage space limit is defined for free users.

### 15. Logging and Auditing:

- The system logs user activities, especially key-related operations.
- Regular auditing of logs for security and compliance.

### 16. Security Audits and Continuous Improvement:

- Regular security audits are conducted to identify and address vulnerabilities.
- User feedback is collected to inform continuous improvements to the system.

## Visual Representation (Complete Workflow)

```
+-----------------------+           +---------------------+           +-----------------------------+
| User Registration     |           | File, Folder, or    |           | File and Key Sharing        |
| and Key Generation    |           | Text Encryption      |           |                           +-----------------------------+
|                       +---------->|                     +---------->|                           |                             |
+-----------------------+           |                     |           |                           |                             |
                                   |                     |           |                           |                             |
+-----------------------+           |                     |           |                           |                             |
| File Upload and        |           |                     |           |                           |                             |
| Encryption            |           |---------------------|           |                           |                             |
|                       +---------->| Database            |           |                           |                             |
+-----------------------+           |                     |           |                           |                             |
                                   |                     |           |                           |                             |
+-----------------------+           |                     |           |                           |                             |
| File Retrieval and     |           | Encryption Process  |           |                           |                             |
| Decryption            |           |                     |           |                           |                             |
|                       +---------->|                     +---------->|                           |                             |
+-----------------------+           +---------------------+           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| Secure Download        |           |                                   |                           |                             |
| Options               |           |                                   |                           |                             |
|                       +---------->|                                   |                           |                             |
+-----------------------+           +---------------------+           |                           |                             |
                                   | User Interface      |           |                           |                             |
+-----------------------+           |---------------------|           |                           |                             |
| Optional Email         |           | Key Management      |           |                           |                             |
| Integration           |           |                     |           |                           |                             |
|                       +---------->|                     |

           |                           |                             |
+-----------------------+           +---------------------+           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| Size Limits and         |           |                                   |                           |                             |
| Communication         |           +---------------------+           |                           |                             |
|                       +---------->| Communication Checks|           |                           |                             |
+-----------------------+           |---------------------|           |                           |                             |
                                   |                                   |                           |                             |


+-----------------------+           |                                   |                           |                             |
| Logging and Auditing  |           +---------------------+           |                           |                             |
|                       +---------->| Logging System      |           |                           |                             |
+-----------------------+           |---------------------|           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| Security Audits and    |           |                                   |                           |                             |
| Continuous Improvement|           +---------------------+           |                           |                             |
|                       +---------->| Security Audits     |           |                           |                             |
+-----------------------+           |---------------------|           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| Two-Factor            |           |                                   |

                           |                             |
| Authentication        |           |                                   |                           |                             |
|                       +---------->|                                   |                           |                             |
+-----------------------+           +---------------------+           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| Rate Limiting         |           |                                   |                           |                             |
|                       +---------->|                                   |                           |                             |
+-----------------------+           +---------------------+           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| Input Validation      |           |                                   |                           |                             |
|                       +---------->|                                   |                           |                             |
+-----------------------+           +---------------------+           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| Session Management    |           |                                   |                           |                             |
|                       +---------->|                                   |                           |                             |
+-----------------------+           +---------------------+           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| Content Security       |           |                                   |                           |                             |
| Policy (CSP)          |           |                                   |                           |                             |
|                       +---------->|                                   |                           |                             |
+-----------------------+           +---------------------+           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| Database Encryption    |           |                                   |                           |                             |
|                       +---------->|                                   |                           |                             |
+-----------------------+           +---------------------+           |                           |                             |
                                   |                                   |                           |                             |
+-----------------------+           |                                   |                           |                             |
| TLS Enforcement        |           |                                   |                           |                             |
|                       +---------->|                                   |                           |                             |
+-----------------------+           +---------------------+           +---------------------------+                             |
                                   |                                                                                               |
+-----------------------+           |                                                                                               |
| Progress Indicators     |           |                                                                                               |
| and User Guides       |           |                                                                                               |
|                       +---------->|                                                                                               |
+-----------------------+           +-----------------------------------------------------------------------------------------------+

```

## System Architecture

The File Encryption System follows a modular monolithic architecture. Key components include:

1. **Django REST Framework:**
   - Used for building the RESTful API.

2. **Redis:**
   - Acts as a message broker for Celery.

3. **Celery:**
   - Manages asynchronous tasks such as encryption and email processing.

4. **PostgreSQL:**
   - Serves as the relational database for storing user data, encrypted content, and metadata.

5. **Silk:**
   - Provides performance monitoring and profiling for Django applications.

6. **DataDog:**
   - Integrated for comprehensive monitoring, alerting, and analytics.

## Dockerization and Scalability

The system is containerized using Docker, allowing for easy deployment and scaling. Each component runs in a separate container, facilitating modularity and scalability. Docker Compose can be utilized to manage multiple containers as a single application.

## Conclusion

The File Encryption System provides a robust and secure solution for users to manage their encrypted files. Its modular monolithic architecture, coupled with Dockerization, ensures scalability and easy deployment. Regular security audits and continuous improvement based on user feedback contribute to maintaining a high level of security and user satisfaction.
