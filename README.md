# Secure-log-in-Anti-Sharing-plugin

WordPress plugin License Tested up to WP 6.6
A comprehensive WordPress plugin for embedding and playing videos with advanced security features to protect your content from unauthorized access, sharing, and piracy. Built with modern HTML5 standards and customizable options, it's perfect for educators, content creators, and businesses delivering premium video experiences.
Table of Contents

Features
Installation
Configuration
Usage
Security Features
Testing
Screenshots
FAQ
Contributing
Support
Changelog
License

Features

Secure Video Embedding: Embed videos using shortcodes with built-in protections against hotlinking and unauthorized downloads.
Customizable Player: Responsive HTML5 player with controls for autoplay, loop, subtitles, and posters.
Access Controls: Restrict videos by user roles, IP ranges, or login status.
Advanced Anti-Sharing: Disable right-click, detect screen recording, and overlay dynamic watermarks.
Geolocation Monitoring: Flag suspicious access from unexpected locations.
OTP Verification: Require one-time passwords for high-security videos.
Threshold-Based Flagging: Monitor IP changes, device fingerprints, session limits, and content access to detect sharing.
Admin Dashboard: Easy management of videos, logs, and notifications.
Performance Optimized: Lazy loading, CDN support, and minimal resource usage.
Compatibility: Works with major themes and plugins (e.g., Elementor, Gutenberg).

Installation

Download the Plugin:
Clone or download the ZIP from the GitHub Releases page.

Upload via WordPress:
Log in to your WordPress admin dashboard.
Navigate to Plugins > Add New > Upload Plugin.
Select the ZIP file and click Install Now.
Activate the plugin from the Plugins page.

Manual Installation (Alternative):
Extract the ZIP and upload the wordpress-secure-video-player folder to /wp-content/plugins/.
Activate via Plugins > Installed Plugins.

Initial Setup:
Go to Settings > Secure Video Player to configure options.
Upload videos to /wp-content/uploads/videos/ or use external URLs.


Requirements:

WordPress 5.0+
PHP 7.4+
No external dependencies (uses native WP functions and browser APIs).

Configuration
Access the settings at Settings > Secure Video Player in your WordPress dashboard. The plugin provides a user-friendly form with tabs for General, Security, and Logging.
General Settings

Player Defaults: Set width (e.g., 800px), height (450px), autoplay (off by default), and loop.
Video Storage: Choose local uploads or external sources (e.g., Vimeo with API keys for embeds).

Security Settings
Enable and configure these to protect your content:

<img width="952" height="685" alt="image" src="https://github.com/user-attachments/assets/8f4f1c94-e54e-4a7e-a85c-1f57cb2da751" />
<img width="956" height="241" alt="image" src="https://github.com/user-attachments/assets/d89389ad-1f27-49c3-a12c-617b288ddd64" />

Settings are saved securely and apply globally or per-video via shortcode attributes.


Setting Description Default Recommendation Enable Anti-Sharing Features Blocks right-click, context menus, and adds watermarks to deter downloads/sharing.OffEnable for all videos. Enable Geolocation Flagging Tracks viewer location via browser API; flags if outside the expected range.OffEnable for region-locked content. Enable OTP Verification Send a one-time password via email before playback.OffEnable for premium/paid videos.IP ThresholdMax unique IPs per user/session before flagging (e.g., 5).53-7 based on audience.Distance Threshold (km)Max location change allowed (e.g., 100km); flags potential sharing.10050-200km.Admin Notification Email for security alerts (e.g., flags, breaches). Your admin email Set a dedicated address. Session Limit: Max concurrent sessions per user (e.g., 1).Off (1)Enable with limit 1-2.Device Fingerprint Threshold Max unique devices per user (e.g., 3).Content Access Threshold Max views per session/day (e.g., 10).105-20.IP Grace Period (days)Days to ignore IP changes (e.g., travel).77-30.
Settings are saved securely and apply globally or per-video via shortcode attributes.

Usage
Embedding Videos
Use the [secure_video_player] shortcode in posts, pages, or widgets. Example:
text[secure_video_player 
    src="https://your-site.com/wp-content/uploads/videos/sample.mp4" 
    poster="https://your-site.com/wp-content/uploads/images/poster.jpg"
    width="800" 
    height="450"
    autoplay="false" 
    loop="true" 
    subtitles="https://your-site.com/subs.vtt"
    security_level="high"  // Applies OTP/geolocation
]

Attributes:
src: Video URL (required, MP4/WebM/OGG).
poster: Thumbnail image.
width/height: Player dimensions.
autoplay/loop/muted: Boolean controls.
subtitles: VTT file for captions.
security_level: low/medium/high to override global settings.


Managing Videos

Upload via Media > Add New and tag as "Secure Video".
View logs and flags at Settings > Secure Video Player > Logs.

Security Features
This plugin goes beyond basic embedding:

Hotlink Protection: .htaccess rules block external embeds.
Nonce & Sanitization: All forms use WP nonces and esc_* functions.
Logging: Tracks plays, flags, and IPs in a custom DB table (wp_secure_video_logs).
Notifications: Email alerts for breaches; integrable with Slack via hooks.
Privacy Compliant: Anonymizes data (hashed IPs); supports GDPR deletion.

For audits, see the Testing section.
Testing
Tested on WordPress 6.6 with PHP 8.2. Thoroughly verified for functionality and security.
Quick Tests

Basic Playback: Embed a video; ensure it loads/responsively plays.
Security: Enable features; attempt hotlinking (should 403) or multi-IP access (should flag).
Edge Cases: Invalid URLs (error message), mobile rotation (adapts), large files (streams).

Tools

LocalWP/XAMPP for staging.
WPScan for vulnerabilities.
Browser DevTools for JS errors.

Full protocol in TESTING.md (create if needed).
Screenshots
(Add images here: e.g., Admin Settings )

Admin dashboard.
Player in action.
Security logs.

FAQ
Q: Does it support streaming?
A: Yes, for HLS/DASH via attributes; local files stream progressively.
Q: How do I disable security for a video?
A: Set security_level="low" in shortcode.
Q: What if geolocation is blocked?
A: Falls back to IP-based checks; no breakage.
Q: Integration with membership plugins?
A: Yes, hooks into restrict_content for seamless role checks.
Contributing
We welcome contributions!

Fork the repo.
Create a feature branch (git checkout -b feature/amazing-feature).
Commit changes (git commit -m 'Add amazing feature').
Push to branch (git push origin feature/amazing-feature).
Open a Pull Request.

Follow WordPress Coding Standards. Run phpcs before submitting.
Support

Issues: GitHub Issues.
Forum: WordPress.org (once submitted).
Email: ablofazlbabaei@gmail.com 

Changelog
1.0.0 - December 6, 2025

Initial release.
Core player with security suite.
Admin settings and shortcode support.
Bug fixes from merge conflicts.

Earlier Versions

Pre-release: Basic video player without security.

License
This plugin is licensed under the GNU General Public License v2.0+. See LICENSE for details.
