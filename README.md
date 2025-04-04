# MCP Server for LinkedIn Profile Scraping

Welcome to the MCP server designed to leverage the Fresh LinkedIn Profile Data API for extracting LinkedIn profile details. This server operates as a model context protocol (MCP) and provides a streamlined tool, `get_profile`, which takes a LinkedIn profile URL as input and returns the corresponding profile data in a structured JSON format.

## Key Features

- **Profile Data Retrieval:** Seamlessly fetch LinkedIn profile information, including skills, while keeping most additional details disabled for a cleaner output.
- **Asynchronous Operations:** Utilizes `httpx` to perform non-blocking HTTP requests, ensuring efficient data fetching without hindering performance.
- **Environment Configuration:** Automatically loads the `RAPIDAPI_KEY` from your environment variables using the `dotenv` package, simplifying setup and enhancing security.

## Prerequisites

- **Python 3.7+** – Ensure you are using Python version 3.7 or higher.
- **MCP Framework:** Make sure the MCP framework is installed.
- **Required Libraries:** Install `httpx`, `python-dotenv`, and other dependencies.
- **RAPIDAPI_KEY:** Obtain an API key from [RapidAPI](https://rapidapi.com/) and add it to a `.env` file in your project directory (or set it in your environment).

## Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/AIAnytime/Awesome-MCP-Server
   cd linkedin_profile_scraper
   ```

2. **Install Dependencies:**

   ```bash
   uv add mcp[cli] httpx requests
   ```


3. **Set Up Environment Variables:**

   Create a `.env` file in the project directory with the following content:

   ```ini
   RAPIDAPI_KEY=your_rapidapi_key_here
   ```

## Running the Server

To run the MCP server, execute:

```bash
uv run linkedin.py
```

The server will start and listen for incoming requests via standard I/O.

## MCP Client Configuration

To connect your MCP client to this server, add the following configuration to your `config.json`. Adjust the paths as necessary for your environment:

```json
{
  "mcpServers": {
     "linkedin-mcp": {
      "command": "/Users/shubham/.local/bin/uv",
      "args": [
          "--directory",
          "/Users/shubham/Documents/projects/linkedin-mcp",
          "run",
          "main.py"
      ]
  }
  }
}
```

## Code Overview

- **Environment Setup:** The server uses `dotenv` to load the `RAPIDAPI_KEY` required to authenticate with the Fresh LinkedIn Profile Data API.
- **API Call:** The asynchronous function `get_linkedin_data` makes a GET request to the API with specified query parameters.
- **MCP Tool:** The `get_profile` tool wraps the API call and returns formatted JSON data, or an error message if the call fails.
- **Server Execution:** The MCP server is run with the `stdio` transport.


## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.