# Subgit - Git Repository Scanner

Subgit is a bash script for scanning vulnerable .git directories recursively within URLs. It is designed to be used in conjunction with tools like hakrawler, waybackurls, etc., to detect potential security risks in web applications during Git repository enumeration.

## How to Run

1. **Prerequisites**: Ensure you have `curl` installed on your system.
   
2. **Usage**:
   
   - To run the script with a list of URLs from a file:
     ```
     cat urls.txt | ./subgit
     ```

   - To run the script with hakrawler:
     ```
     hakrawler -url https://example.com -depth 2 -plain | ./subgit
     ```

   - To run the script with waybackurls:
     ```
     echo "https://example.com" | waybackurls | ./subgit
     ```

3. **Options**:

   - `-c` or `--continue`: Continue from where left off. (Not recommended for use with waybackurls due to known bug. Will be fixed soon.)
   - `-d` or `--delete`: Delete scanned paths and start fresh. (Not recommended for use with waybackurls due to known bug. Will be fixed soon.)

## Note

- **Warning**: Avoid using `-c` or `-d` options for now when using with waybackurls, as there is a known bug. This will be fixed in a future release.
- Upon running the script, a folder named `.subdirconfig` will be created in your home directory. This folder contains a JSON file (`scanned_paths.json`) that stores information about scanned paths and their status.

