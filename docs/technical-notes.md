Omeka Installation and Project Development:

Technical Objectives Completed
    • Installed and configured Omeka Classic 3.1.2 in a local development environment using XAMPP on Windows 11.
    • Created a new MySQL database and user specifically for the Omeka site using phpMyAdmin.
    • Modified the db.ini file with secure, custom database credentials and connection information.
    • Uncommented the SetEnv APPLICATION_ENV development line in the .htaccess file for detailed error reporting
    • Resolved file path issues to ensure Omeka loaded correctly at http://localhost/omeka.
    • Completed the Omeka installation by configuring the site title, admin account, and upload settings via the browser-based setup screen.
    • Installed and configured ImageMagick to generate thumbnails and derivatives for Omeka items locally.
    • Verified Omeka site functionality after installation and navigated to the admin dashboard.
    • Recovered from database errors related to aria_log_control using the aria_chk recovery tool.
    • Backed up and restored mysql system tables, including columns_priv.MAI after corruption.
    • Verified proper operation of all Omeka site components after restoration and migration.
    • Established a working backup routine including site files, MySQL databases, and configuration files.
    • Switched to Laragon after repeated issues with XAMPP’s stability and service startup failures. Laragon proved more reliable for local Omeka development.

Technical Challenges Encountered
    • Access Denied error when launching XAMPP Control Panel:
Encountered a Cannot Create File “xampp-control.ini” error due to missing admin rights.
    • phpMyAdmin login issues:
Error Access Denied for user ‘pma’@’localhost’ and ‘root’@’localhost’ due to invalid or missing MySQL credentials.
    • Omeka not launching properly:
Initially saw a raw directory listing instead of the Omeka installer because the folder structure was incorrect.
    • Omeka Encountered an Error screen with no visible logs:
Required enabling error logging to display useful debugging output.
    • ImageMagick path unknown during setup:
Needed to identify and supply the correct path to the ImageMagick convert executable required for image processing.
    • Encountered a missing ‘database’ section error in db.ini.
    • Database corruption involving the aria_log_control file and .MAI table structures after improper shutdown or file loss.
    • Encountered the MySQL Server Has Gone Away error due to service interruptions or crashes.
    • Faced a login authentication error: Access denied for user ‘omeka_user’@’%localhost’ to database ‘omeka_db’.
    • db.ini parsing failed due to:
        ◦ Quotation marks around values.
        ◦ Incorrect section headers or misplaced characters.
    • Encountered MariaDB ERROR 1396 (HY000) when trying to update an existing user’s password improperly.
    • Initial startup issues with MySQL service due to missing or broken control files in the data directory.

Troubleshooting and Solutions
    • Ran XAMPP as Administrator to fix the .ini write permissions error.
    • Manually created the Omeka MySQL database and user in phpMyAdmin with specific credentials, then updated db.ini to match.
    • Reorganized Omeka files into the proper directory (htdocs/omeka) to avoid the directory listing issue.
    • Enabled error visibility in Omeka by editing application/config/config.ini, setting display_errors = On and log.errors = true.
    • Confirmed ImageMagick installation by checking the XAMPP path and entering it into the Omeka install form (e.g. C:\xampp\imagemagick). Configured settings through config.ini. Later configured for Laragon.
    • Fixed the missing ‘database’ section error by properly specifying the [database] header and correcting syntax.
    • Used aria_chk -r -o -f to repair corrupted .MAI system tables and restore MySQL functionality.
    • Resolved permission and access issues by:
        ◦ Recreating the database user with the correct password.
        ◦ Using GRANT ALL PRIVILEGES followed by FLUSH PRIVILEGES.
    • Rewrote the db.ini file without quotes, ensuring correct host, username, password, dbname, and port.
    • Used mysqldump and phpMyAdmin to export and import database backups safely.
    • Verified and adjusted MySQL’s port number to match Laragon/XAMPP configuration.
    • Checked and aligned Omeka’s database connection settings with actual MySQL user credentials.
    • Fixed InnoDB corruption in the local MySQL database, restoring all data tables and salvaging broken collections through a combination of MySQL commands and backups.
    • Successfully migrated a complete Omeka project (files, metadata, database) from XAMPP to Laragon, preserving the local exhibit structure.
    • Verified database and file path integrity post-migration and ensured plugin functionality across environments.
    • Backed up all Omeka files and exported the MySQL database for future restoration if needed.


Deployment and Hosting:

Technical Objectives Completed
    • Migrated the Omeka project to a remote hosting environment on Google Cloud Platform using a free-tier virtual machine (VM) running Ubuntu 22.04 LTS.
    • Installed and configured Apache, MariaDB (MySQL), and PHP with required extensions for Omeka.
    • Secured the MariaDB installation and created a dedicated Omeka database and user.
    • Deployed Omeka Classic by uploading the application files, setting appropriate file permissions, and configuring the db.ini file.
    • Imported an existing Omeka SQL database backup to restore project content, metadata, and exhibit structure.
    • Enabled Apache’s mod_rewrite and properly configured virtual host settings to ensure Omeka functioned correctly over the web.
    • Set up SSH key authentication for secure access to the VM.
    • Used Google Cloud Console’s browser-based SSH terminal and CLI tools to manage server and file operations.
    • Successfully launched the public-facing digital exhibit from the cloud-based Omeka installation, maintaining full access to the admin dashboard and site editing tools.
    • Reserved a static external IP address in Google Cloud to maintain a consistent public endpoint.
    • Registered a custom domain name via Cloudflare and updated DNS A records for both @ and www to point to the static IP.
    • Configured Apache Virtual Hosts to correctly serve the Omeka site at both www and root (@) domains.
    • Installed Certbot and set up Let’s Encrypt to serve the site securely over HTTPS.
    • Verified that both https://theroyalarchives.org/ and https://www.theroyalarchives.org/ display the correct Omeka site with a valid SSL certificate.
    • Configured SMTP email delivery in Omeka by editing config.ini to use a secure third-party mail server, enabling email delivery through the Contact form.
    • Enabled reCAPTCHA for the Contact form by generating API keys, updating Omeka site settings, and testing both visible and invisible CAPTCHA responses for bot protection.

Technical Challenges Encountered
    • Initially attempted to launch the project using Omeka.net, however, several limitations appeared:
        ◦ Inability to upload XML files for TEI encoding.
        ◦ No access to the server, database, or file system.
        ◦ Restricted plugin support and lack of customization options.
    • Switched to Oracle Cloud, but persistent system hangs, stalled dnf operations, and package manager timeouts due to low-memory limitations in the free-tier configuration rendered software installation unreliable. Made the final switch to Google Cloud.
    • SSH authentication errors caused by:
        ◦ Mismatched or missing key files
        ◦ Inconsistencies in email vs. username headers in .pub keys
        ◦ Key disappearance or permission issues across both local (WSL) and cloud terminals
    • WSL and scp failed to consistently recognize Windows-mounted file paths, resulting in upload errors and broken transfers.
    • Omeka installer displayed mod_rewrite errors due to missing Apache configuration directives.
    • SQL file uploads appeared empty after being moved into the VM, leading to repeated failures to import the database.
    • Switching between multiple development environments (XAMPP, Laragon, Oracle VM, Google VM) introduced inconsistencies in MySQL user credentials and db.ini settings that caused admin login errors after database restoration.
    • Google Cloud’s SDK tools and WSL terminal occasionally conflicted in permissions and path resolution while attempting file uploads.
    • Initial DNS propagation delays and Apache misconfiguration resulted in theroyalarchives.org showing the default Apache page, while www.theroyalarchives.org loaded the Omeka site correctly.

Troubleshooting and Solutions
    • Switched from Oracle Cloud to Google Cloud Platform after repeated VM resource and network issues.
    • Regenerated SSH key pairs directly within WSL to simplify authentication and manually managed .ssh/authorized_keys. Did the same in Google Cloud Console’s browser-based SSH terminal when WSL continued to encounter errors.
    • Bypassed unreliable file transfer methods by uploading ZIP archives directly to the browser-based VM terminal, then unzipping and moving content with mv inside the VM.
    • Verified successful file uploads using ls, head, and file size checks before attempting to move SQL imports.
    • Ensured proper Apache configuration by adding AllowOverride All directives and <Directory /var/www/html> blocks to the default virtual host file, resolving mod_rewrite errors.
    • Confirmed SQL file content before import by checking its location and size; re-exported the database to ensure a working backup.
    • Adjusted login expectations after restoring the old database with different admin credentials than originally set during VM setup.
    • Maintained a streamlined toolset and fallback strategy, using browser-based access for all critical operations when SDK or WSL presented barriers.
    • Reserved a static external IP address to prevent changes each time the VM restarted, which resolved DNS mismatches.
    • Fixed root domain (theroyalarchives.org) misrouting by editing Apache’s DocumentRoot and ServerName directives and reloading the service.
    • Installed Let’s Encrypt SSL certificates via Certbot and confirmed valid HTTPS access from both domain variants.
    • Validated all DNS and SSL setup with live testing and browser inspection tools.


General Project Notes:

Technical Objectives Completed
    • Encoded four medieval letters in TEI/XML using Oxygen XML Editor, incorporating structured markup for people, places, institutions, roles, and rhetorical features.
    • Uploaded plain text, XML, and PNG files to Omeka Classic.
    • Used Voyant Tools to analyze both individual and corpus-level letter content, generating visualizations such as Cirrus wordclouds, word trends, and KWIC statistics.
    • Used ProWritingAid to check and refine all exhibit prose for grammar, clarity, and tone.
    • Applied Dublin Core metadata standards to all letters and associated analyses to ensure consistent item description and discoverability.
    • Created an inventory of all item metadata using Microsoft OneNote, allowing for cross-checking and planning of Dublin Core fields across all letters and tools.
    • Applied custom exhibit organization strategies, such as creating landing pages with explanatory text.
    • Managed navigation logic to ensure that all exhibit sections and subpages were accessible in a meaningful order.

Technical Challenges Encountered
    • Omeka’s exhibit text editor did not initially display line breaks or spacing correctly.
    • XML files could not be uploaded to Omeka Classic by default, due to the file type being disallowed in the system settings.

Troubleshooting and Solutions
    • Incorrectly displayed line breaks and spacing were resolved by toggling between the HTML view and plain text editor, and manually adding <br> tags where necessary.
    • The XML upload issue was resolved by navigating to the Security tab in Settings and adding xml and text/html to both the Allowed File Extensions and Allowed File Types fields.