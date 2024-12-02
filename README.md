
# FileWatcherService

The FileWatcherService is a Windows service application developed in .NET Framework that monitors changes in a specified directory. The service is capable of detecting file creations, modifications, and deletions and performs specified actions accordingly. It is ideal for scenarios where real-time monitoring of file changes is required.

## Features

- **File Monitoring**: Monitors a specified directory for file creations, deletions, and modifications.
- **Logging**: Logs all file activities, including the type of action (created, modified, deleted), the filename, and the timestamp.
- **Configurable Directory**: The directory to monitor can be configured, allowing flexibility in choosing which folder to watch.
- **Windows Service**: Runs as a background Windows service, automatically starting with the system and providing continuous monitoring.

## Requirements

- **Development Environment**: Visual Studio 2010 or higher
- **.NET Framework**: Version 4.0 or higher
- **Administrator Privileges**: To install and run the service, administrator privileges are required.

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/keskinmertcan/FileWatcherService.git
   ```

2. **Open the Solution**:
   - Open the solution in Visual Studio.

3. **Build the Project**:
   - Build the solution to create the executable for the Windows service.

4. **Install the Service**:
   - Use the `InstallUtil` utility to install the service:
     ```bash
     InstallUtil.exe FileWatcherService.exe
     ```
   - Ensure you run the command prompt as an administrator.

5. **Configure the Service**:
   - Update the configuration file (`app.config`) to specify the directory to be monitored.

6. **Start the Service**:
   - Open the Services management console (`services.msc`), find `FileWatcherService`, and start it.

## Usage

- **Directory Monitoring**: Once started, the service will monitor the specified directory for any file changes, including:
  - **File Created**: When a new file is added to the directory.
  - **File Modified**: When an existing file is modified.
  - **File Deleted**: When a file is removed from the directory.
- **Log File**: All file activities are logged to a text file located in the service directory. This log includes details about the type of event, file name, and timestamp.

## Configuration

- The directory to be monitored can be configured in the `app.config` file:
  ```xml
  <appSettings>
    <add key="WatchDirectory" value="C:\Path\To\Directory" />
  </appSettings>
  ```
- You can change the `WatchDirectory` value to the desired directory path.

## Security

- **Run as Administrator**: The service requires administrator privileges to install, start, and stop.
- **Access Control**: Ensure that the service has appropriate permissions to read from and write to the monitored directory.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! If you have ideas for improving the service or new features, feel free to submit a pull request or raise an issue.

---

The FileWatcherService is designed to provide reliable, real-time monitoring of file activities in a directory, making it an ideal solution for systems that require continuous observation of file changes.

### Notes

- Ensure that the directory being monitored is accessible by the service with sufficient read and write permissions.
- Currently, the service supports monitoring a single directory, but future updates may include support for multiple directories or network paths.
