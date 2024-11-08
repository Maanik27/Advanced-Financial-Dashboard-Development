  let
    // Define the API endpoint
    apiUrl = "https://serpapi.com/search.json",


// Define the parameters
queryParams = [ engine = "google_trends", q = "Data Analyst,The Developer,Jobs,India,Power BI" , data_type = "GEO_MAP", date = "today 5-y", tz="-330",api_key = "Peste your Key here"],

// Combine the endpoint and parameters
fullUrl = apiUrl & "?" & Uri.BuildQueryString(queryParams),

// Make the HTTP request
response = Web.Contents(fullUrl),

// Parse the JSON response
jsonResponse = Json.Document(response),

// Convert the response to a table
dataTable = Table.FromRecords({jsonResponse}),

// Extract the relevant data
comparedBreakdownByRegion = dataTable{0}[compared_breakdown_by_region]
in
    comparedBreakdownByRegion
