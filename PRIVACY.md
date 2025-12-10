# Privacy Policy

Last updated: December 10, 2024

## Information We Collect
This application does not collect, store, or transmit any personal information. All data processing occurs locally on your n8n instance.

## How We Use Information
- OAuth tokens are used only to authenticate API requests
- No user data is stored on our servers
- Video content is uploaded directly from your device to TikTok

## Third-Party Services
This application uses:
- TikTok API for content posting
- n8n for workflow automation (self-hosted)

## Data Security
All authentication is handled through TikTok's official OAuth2 system. We do not have access to your TikTok password.

## Your Rights
You can revoke access at any time through your TikTok account settings.

## Changes to Privacy Policy
We may update this policy and will notify users of significant changes.

## Contact
[Votre email]
```

---

## **Platforms**

Cochez : **☑ Web** (puisque n8n est accessible via navigateur)

---

## **App Review - Explain how each product and scope works**

Voici une version étendue et détaillée :
```
APPLICATION OVERVIEW
This is a personal workflow automation tool built with n8n (open-source workflow automation platform) that enables users to programmatically upload video content to TikTok from their local system or cloud storage.

PRODUCTS & SCOPES EXPLANATION:

1. LOGIN KIT
Purpose: Secure user authentication via TikTok OAuth 2.0
Implementation:
- Users authorize the application through TikTok's official OAuth flow
- Establishes secure connection between user's n8n instance and TikTok account
- Generates access tokens for API operations
- No passwords stored; tokens managed locally in n8n

2. CONTENT POSTING API
Purpose: Programmatic video upload and publishing
Implementation:
- Automates video content delivery from local storage to TikTok
- Eliminates manual upload process
- Enables scheduled and batch posting workflows
- Integrates with n8n's file handling and trigger systems

SCOPES:

user.info.basic
Purpose: Retrieve authenticated user's profile information
Usage:
- Confirms correct account authentication
- Displays username/avatar in n8n workflow for verification
- Prevents accidental posting to wrong account
Data accessed: User ID, username, display name, avatar URL
Workflow integration: Used in initial authentication step to validate connection

video.upload
Purpose: Transfer video files to TikTok's infrastructure
Usage:
- Reads video files from local filesystem or connected cloud storage (Google Drive, Dropbox)
- Uploads video content using TikTok's chunked upload mechanism
- Handles large file transfers (up to TikTok's size limits)
- Required prerequisite before video publication
Workflow integration: n8n reads video file → HTTP Request node uploads to TikTok endpoint

video.publish
Purpose: Finalize video publication with metadata
Usage:
- Sets video title, description, and hashtags
- Configures privacy settings (public/private/friends)
- Controls video features (comments, duets, stitching)
- Schedules publication time if needed
Workflow integration: After upload completion, publishes with user-defined settings from n8n variables

COMPLETE USER WORKFLOW:
1. User configures n8n workflow with video source (folder watch, cloud storage, etc.)
2. Workflow triggers when new video detected
3. OAuth authentication validates user (Login Kit + user.info.basic)
4. Video file uploaded to TikTok servers (video.upload)
5. Video published with configured metadata (video.publish)
6. Confirmation sent to user via email/notification (Gmail node in n8n)

PRIVACY & SECURITY:
- Application runs entirely on user's own infrastructure (self-hosted n8n)
- No central server stores user data or credentials
- OAuth tokens stored locally in n8n's encrypted credential storage
- Only authenticated user's own content is accessed
- Complies with TikTok API Terms of Service

TARGET USERS:
- Content creators managing regular posting schedules
- Social media managers handling multiple accounts
- Individual users automating personal TikTok workflow
- Developers testing TikTok API integration

EXPECTED USAGE:
- Low to moderate volume (1-50 videos per day per user)
- Personal/educational use
- Not for commercial spam or bulk operations

TECHNICAL STACK:
- n8n (self-hosted workflow automation)
- TikTok Content Posting API v2
- OAuth 2.0 with PKCE for authentication
- Local file system or cloud storage integration
