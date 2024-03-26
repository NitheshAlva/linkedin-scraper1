# LinkedIn Scraper API

## Overview

This project is a LinkedIn Scraper built using Selenium for web scraping and FastAPI for serving the scraped data via RESTful APIs. It allows users to fetch detailed profile and company information from LinkedIn based on the provided LinkedIn ID.

## Installation

### Prerequisites

- Python 3.8+
- pip
- git

### Setup

1. **Clone the Repository**
   - Clone this repository to your local machine using `git clone https://github.com/drissbri/linkedin-scraper`.

2. **Create and Activate Virtual Environment**
   - Navigate to the project directory.
   - Create a virtual environment by running `python -m venv venv`.
   - Activate the virtual environment:
     - On Windows, run `venv\Scripts\activate`.
     - On macOS/Linux, run `source venv/bin/activate`.

3. **Install Dependencies**
   - Install the required packages by running `pip install -r requirements.txt`.

## Configuration

1. **Environment Variables**
   - Create a `.env` file in the root of the project.
   - Add the following environment variables:
     ```
     LINKEDIN_ACCESS_TOKEN="YourLinkedInAccessToken"
     LINKEDIN_ACCESS_TOKEN_EXP="AccessTokenExpiration"
     ```
   - Replace `"YourLinkedInAccessToken"` and `"AccessTokenExpiration"` with your actual LinkedIn access token and its expiration time.

## Usage

To start the server, run the following command in the root directory of the project:

```shell
python run.py
```

This command will start the Uvicorn server and make the API accessible on `http://localhost:8000` by default.

## API Endpoints

The LinkedIn Scraper offers endpoints for retrieving detailed profile and company information from LinkedIn. Here's what you can expect from each:

### Profile Data

- **GET** `/profile-data/{linkedin_id}`
  - Fetches profile information for the specified LinkedIn ID.
  - **Path Parameters:**
    - `linkedin_id`: The unique LinkedIn ID of the profile.
  - **Response:** JSON object containing the profile information as per the provided format.
  - **Response Format:**
    ```json
    {
      "linkedin_id": "string",
      "name": "string",
      "headline": "string",
      "education": {
        "positions": ["string"],
        "institutions": ["string"],
        "dates": ["string"]
      },
      "experience": {
        "positions": ["string"],
        "institutions": ["string"],
        "dates": ["string"]
      }
    }
    ```
  - The `education` and `experience` fields are objects that include arrays of strings for positions, institutions, and dates, providing a concise summary of the individual's educational background and work history.

### Company Data

- **GET** `/company-data/{linkedin_id}`
  - Fetches company information based on the given LinkedIn ID.
  - **Path Parameters:**
    - `linkedin_id`: The unique LinkedIn ID of the company.
  - **Response:** JSON object containing the company information as structured below.
  - **Response Format:**
    ```json
    {
      "linkedin_id": "string",
      "name": "string",
      "industry": "string",
      "about": "string"
    }
    ```
  - This format outlines the company's LinkedIn ID, name, industry sector, and a brief description of the company in the `about` field.

## Error Handling

Error handling is consistent across endpoints, aiming to provide meaningful feedback in case of failures:

- **Example Error Response:**

  ```json
  {
    "detail": "Error fetching profile details"
  }
  ```
  This response is returned with an HTTP status code of 500, indicating a server-side error during data fetching, along with a detail message explaining the error.

## Notes

- Ensure that the LinkedIn access token is valid and not expired to avoid authentication errors.
- This scraper is intended for educational purposes and should be used in accordance with LinkedIn's terms of service.

## Contributing

I welcome contributions from the community and I'm excited to see how you can improve and extend this LinkedIn Scraper project! If you're looking to contribute, here are a few ways you can do so:

### Reporting Bugs

- **Submit an Issue**: If you find a bug or encounter an issue, please create an issue on our GitHub repository. Provide as much detail as possible, including steps to reproduce the issue, the expected outcome, and the actual outcome.

### Feature Requests

- **Request a Feature**: Have an idea for a new feature or an enhancement to existing functionality? Submit a feature request through our issue tracker. Describe the feature, its potential benefits, and how it might work.

### Submitting Changes

- **Fork the Repository**: Start by forking the repository to your GitHub account.
- **Create a Branch**: Create a new branch for your changes. Use a clear and descriptive name for your branch, such as `fix-issue-1` or `add-new-feature`.
- **Make Your Changes**: Implement your changes, adhering to the existing coding style as much as possible.
- **Write Tests**: If you're adding new functionality or fixing a bug, please add tests to cover your changes.
- **Document Your Changes**: Update the README or documentation with any necessary changes due to your contribution.
- **Submit a Pull Request (PR)**: Once your changes are complete, submit a pull request to the main branch of the original repository. Include a clear description of your changes and any other relevant information.

### Code Review Process

- **Review & Feedback**: After submitting a PR, the project maintainers will review your changes. Be open to feedback and ready to make adjustments as needed.
- **Approval & Merge**: If your contribution is approved, the project maintainers will merge your changes into the main branch.

### General Guidelines

- Ensure your code follows the project's coding conventions and best practices.
- Keep your commits small and focused; it makes the review process easier.
- Update any documentation that your changes might affect.

I appreciate your interest in contributing to the LinkedIn Scraper project! By participating, you agree to abide by the code of conduct and collaboration guidelines. Let's build something great together!