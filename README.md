# Secure Embeddable Chat Widget

A web-based chat widget designed to be embedded into partner websites to enable communication between website visitors and businesses.

## Overview

This project implements an embeddable chat widget that can be integrated into a partner website using a JavaScript loader.

The widget provides a separate chat interface while communicating with backend APIs for widget configuration, session management and messaging.

## Features

- Embeddable JavaScript widget
- iframe-based UI isolation
- Cross-origin communication
- Widget configuration through APIs
- Department selection
- Address selection
- Dynamic form handling
- Chat session creation
- Message submission
- Loading and error handling

## Architecture

The widget follows a simple client-side integration flow:

Partner Website → JavaScript Loader → Widget Interface → Backend APIs

The JavaScript loader creates the embedded widget and allows the widget to communicate with the backend services.

## API Flow

The widget communicates with the backend through multiple stages:

1. Fetch widget configuration
2. Perform handshake
3. Create a chat session
4. Exchange messages

Additional application data can be retrieved through APIs for:

- Departments
- Addresses
- Form fields
- Form submission

## Embedding the Widget

The widget can be integrated into a partner website using a JavaScript script tag.

Example:

    <script src="widget-loader.js"
            async
            data-widget-id="YOUR_WIDGET_ID"
            data-position="bottom-left">
    </script>

The widget loader is responsible for creating and displaying the embedded widget.

## Security Considerations

Security is an important part of an embeddable widget because it can operate across different website origins.

The project considers:

- iframe isolation
- Origin validation
- Secure authentication
- Short-lived authentication tokens
- Content Security Policy
- Server-side authorization
- API rate limiting
- Secure cookie configuration

Production credentials and private API information are not included in this repository.

## Project Structure

The repository contains project documentation and screenshots of the widget development process.

- README.md
- LICENSE
- docs/
- screenshots/
- screenshots/widget-development.png
- screenshots/widget-project.png

## Technologies

- HTML
- CSS
- JavaScript
- REST APIs
- iframe
- Git

## Documentation

Detailed API integration information is available in:

docs/API_INTEGRATION_GUIDE.md

The documentation covers:

- API configuration
- Department API
- Address API
- Form fields API
- Form submission API
- Error handling
- Loading states

## Screenshots

### Widget Development

![Widget Development](screenshots/widget-development.png)

### Project Development

![Project Development](screenshots/widget-project.png)

## Future Improvements

- Complete backend integration
- Dynamic form configuration
- Automated testing
- Improved error handling
- Better API configuration management
- CI/CD integration
- Containerized deployment
- Additional security hardening

## Author

**Darahaas Vadlamudi**
