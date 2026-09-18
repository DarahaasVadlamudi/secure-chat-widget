# API Integration Guide

This document describes the API integration points used by the
embeddable chat widget.

## API Integration Points

The widget uses backend APIs for:

- Widget configuration
- Department information
- Address information
- Dynamic form fields
- Form submission
- Chat session management
- Messaging

## API Configuration

The widget requires a backend API base URL and endpoint configuration.

Example:

    const API_CONFIG = {
        baseUrl: "https://your-api-domain.com/api",

        endpoints: {
            departments: "/departments",
            addresses: "/addresses",
            formFields: "/form-fields",
            submit: "/submit"
        }
    };

Do not commit production credentials, authentication tokens, or other
private configuration values to a public repository.

## Widget Configuration

The widget first retrieves the configuration required to initialize
the chat interface.

The configuration can include information such as the widget ID,
site information and available departments.

## Handshake

A handshake is performed between the widget and the backend before
creating a chat session.

The handshake allows the backend to validate the widget request and
establish the required session context.

## Chat Session

After the initial handshake, a chat session can be created for the
visitor.

The session is then used for subsequent communication between the
widget and the backend.

## Departments

The widget can retrieve the available departments from the backend.

Example:

    GET /departments

The returned departments can be displayed to the visitor for selection.

## Addresses

After a department is selected, the widget can retrieve the associated
addresses.

Example:

    GET /addresses?departmentId=1

The returned information can be used to display the relevant business
or office details.

## Dynamic Form Fields

The widget can retrieve form fields dynamically based on the selected
configuration.

Example:

    GET /form-fields?addressId=1

The response can contain information such as:

- Field name
- Label
- Input type
- Required status

This allows the form displayed by the widget to be configured by the
backend.

## Form Submission

After the visitor completes the required information, the widget can
submit the form data to the backend.

Example:

    POST /submit

Example request:

    {
        "widgetId": "YOUR_WIDGET_ID",
        "firstName": "John",
        "lastName": "Doe",
        "email": "john@example.com",
        "mobile": "1234567890",
        "message": "Hello"
    }

## Messaging

Once a chat session has been established, the widget can communicate
with the backend to exchange messages.

The messaging layer is responsible for sending visitor messages and
handling responses from the backend.

## Error Handling

API requests should be handled appropriately so that failures do not
leave the widget in an unusable state.

Example:

    try {
        const response = await fetch(url);

        if (!response.ok) {
            throw new Error(`API Error: ${response.status}`);
        }

        const data = await response.json();

        return data;
    } catch (error) {
        console.error("API request failed:", error);
    }

## Loading States

The widget should provide feedback while waiting for API responses.

Examples:

    Loading departments...

    Submitting...

Loading states help prevent the interface from appearing unresponsive.

## Security Considerations

Because the widget can be embedded into websites with different
origins, security is an important part of the integration.

The project considers:

- iframe isolation
- Origin validation
- Secure authentication
- Short-lived authentication tokens
- Content Security Policy
- Server-side authorization
- API rate limiting
- Secure cookie configuration

Production credentials and private API information should not be
included in this repository.

## Integration Flow

    Widget Loaded
          |
          v
    Fetch Configuration
          |
          v
       Handshake
          |
          v
    Create Chat Session
          |
          v
    Fetch Departments
          |
          v
    Select Department
          |
          v
    Fetch Addresses
          |
          v
    Select Address
          |
          v
    Display Form
          |
          v
    Submit Information
          |
          v
      Backend API

## Future Improvements

Possible improvements include:

- More complete backend integration
- Dynamic configuration management
- Automated testing
- Improved error handling
- CI/CD integration
- Containerized deployment
- Additional security hardening
