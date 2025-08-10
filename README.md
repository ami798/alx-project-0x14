# alx-project-0x14
## API Version
The API version is v1 (current).

## Available Endpoints
/titles: The main endpoint for fetching a list of titles (movies, series, and episodes). It supports various filters and sorting options.

/titles/{id}: Retrieves detailed information for a single title using its unique IMDb ID.

/titles/{id}/ratings: Fetches the rating and number of votes for a specific title.

/titles/search/keyword/{keyword}: Searches for titles using a keyword.

/titles/search/title/{title}: Searches for titles by their name or a part of their name.

/actors: Returns an array of actors, with optional pagination.

/actors/{id}: Retrieves detailed information for a single actor.

/title/utils/genres: Returns a list of available genres for filtering.

## Request and Response Format
A typical request to the main /titles endpoint might look like this:

GET https://moviesdatabase.p.rapidapi.com/titles?year=2023&genre=Action&limit=10&page=1

The API returns a JSON object. For endpoints with multiple results, the main object contains a results key, which is an array of objects.

Example Response Object:

JSON

{
  "results": [
    {
      "id": "tt1234567",
      "titleText": { "text": "The Movie Title" },
      "primaryImage": { "url": "https://example.com/poster.jpg" },
      "releaseYear": { "year": "2023" }
    },
    // ... more movie objects
  ],
  "page": 1,
  "next": "...",
  "entries": 10
}
## Authentication
All requests to the MoviesDatabase API require an API key for authentication. This key must be included in the request headers with the key x-rapidapi-key and the host x-rapidapi-host. For example:

"x-rapidapi-host": "moviesdatabase.p.rapidapi.com"
"x-rapidapi-key": "YOUR_API_KEY_HERE"
## Error Handling
The API returns standard HTTP status codes for different errors. Common error responses and their meanings are:

401 Unauthorized: Occurs when the provided x-rapidapi-key is invalid or missing.

404 Not Found: Occurs when the requested endpoint or resource does not exist.

500 Internal Server Error: Indicates an issue on the API's side.

Developers should implement try/catch blocks and check the response status (response.ok) to handle these errors gracefully in their application.

## Usage Limits and Best Practices
Rate Limits: The API has usage limits based on your subscription plan. It is important to monitor and handle rate limiting to prevent application downtime.

Pagination: The API supports pagination with page and limit query parameters. Using these parameters is a best practice to manage request size and reduce load on both the client and server. The maximum limit is 50 objects per page.

Caching: To optimize performance and reduce the number of API calls, consider client-side caching for responses that do not change frequently.

Environment Variables: To protect sensitive information, API keys should be stored as environment variables and accessed from server-side code (e.g., Next.js API routes), not exposed directly in the client-side code.