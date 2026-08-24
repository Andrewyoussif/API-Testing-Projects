TMDB API Testing Project

📌 Project Overview

This project is an API Testing assignment for The Movie Database (TMDB) API, performed using Postman.

The objective of this project is to validate different TMDB API endpoints by checking HTTP status codes, response structure, required fields, data validity, pagination, filtering, and authorization behavior.

The project covers 10 main API testing scenarios and an additional bonus POST scenario for adding a movie to a user's watchlist.

---

🛠️ Tools & Technologies

- Postman
- TMDB REST API
- JSON
- HTTP Methods
- Git
- GitHub

---

🔐 Authentication

The TMDB API uses Bearer Token authentication at the collection level.

The project uses Postman variables for:

base_url
api_key
bearer_token

Sensitive authentication credentials are not included in the exported Postman Collection.

---

🧪 API Testing Scenarios

1. Search Movies by Keyword

Method: "GET"

Endpoint:

/search/movie

Test objective:

Verify that searching for movies using a keyword returns relevant and accurate results.

Validations

- Status code is "200 OK"
- Response contains a "results[]" array
- Movie titles are relevant to the search keyword
- Each result contains:
  - "id"
  - "title"
  - "release_date"
  - "overview"
- "total_results" is greater than "0"

---

2. Search TV Shows by Name

Method: "GET"

Endpoint:

/search/tv

Test objective:

Verify that searching for a TV show by name returns valid results.

Validations

- Status code is "200 OK"
- Response contains a "results[]" array
- At least one result is returned
- Each result contains:
  - "id"
  - "name"
  - "first_air_date"
  - "overview"
- Results are not empty

---

3. Get Movie Details by Movie ID

Method: "GET"

Endpoint:

/movie/{movie_id}

Test objective:

Retrieve and validate detailed information for a specific movie.

Validations

- Status code is "200 OK"
- Response contains:
  - "title"
  - "overview"
  - "release_date"
  - "runtime"
- "genres[]" is present and not empty
- "production_companies[]" is present
- "budget" and "revenue" fields exist

---

4. Get Movie Credits

Method: "GET"

Endpoint:

/movie/{movie_id}/credits

Test objective:

Retrieve and validate the cast and crew information of a movie.

Validations

- Status code is "200 OK"
- Response contains:
  - "cast[]"
  - "crew[]"
- Each cast member contains:
  - "id"
  - "name"
  - "character"
  - "order"
- Crew members contain:
  - "id"
  - "name"
  - "job"
  - "department"
- Cast list is not empty

---

5. Get Popular Movies

Method: "GET"

Endpoint:

/movie/popular

Test objective:

Verify that the Popular Movies endpoint returns a valid paginated list of popular movies.

Validations

- Status code is "200 OK"
- "results[]" contains 20 movies per page
- Pagination fields are present:
  - "page"
  - "total_pages"
  - "total_results"
- Each movie contains:
  - "id"
  - "title"
  - "vote_average"
  - "popularity"
- Results are sorted by popularity in descending order

---

6. Get TV Show Details by ID

Method: "GET"

Endpoint:

/tv/{series_id}

Test objective:

Retrieve and validate detailed information for a specific TV show.

Validations

- Status code is "200 OK"
- Response contains:
  - "name"
  - "overview"
  - "first_air_date"
  - "number_of_seasons"
- "genres[]" is present and not empty
- "episode_run_time[]" exists
- "networks[]" is present
- "created_by[]" is present

---

7. Get Movie Genres List

Method: "GET"

Endpoint:

/genre/movie/list

Test objective:

Verify that the API returns the available movie genres.

Validations

- Status code is "200 OK"
- Response contains a "genres[]" array
- Genres such as:
  - Action
  - Comedy
  - Drama
    are available
- Each genre contains:
  - "id"
  - "name"
- Genre list is not empty

---

8. Discover Movies by Genre

Method: "GET"

Endpoint:

/discover/movie

Test objective:

Retrieve movies filtered by a specific genre.

Validations

- Status code is "200 OK"
- Response contains a "results[]" array
- Results are filtered according to the selected genre
- Each movie contains:
  - "id"
  - "title"
  - "genre_ids[]"
  - "vote_average"
- The requested "genre_id" exists in "genre_ids[]"
- Pagination fields are present:
  - "page"
  - "total_pages"
  - "total_results"

---

9. Get Now Playing Movies

Method: "GET"

Endpoint:

/movie/now_playing

Test objective:

Verify that the Now Playing endpoint returns movies currently playing in theaters.

Validations

- Status code is "200 OK"
- Response contains:
  - "results[]"
  - "dates{}"
- "dates{}" contains:
  - "maximum"
  - "minimum"
- Each movie contains:
  - "id"
  - "title"
  - "release_date"
  - "vote_count"
- Movie release dates fall within the valid date range

---

10. Get Person Details

Method: "GET"

Endpoint:

/person/{person_id}

Test objective:

Retrieve and validate biographical and filmography information for a specific actor or director.

Validations

- Status code is "200 OK"
- Response contains:
  - "name"
  - "biography"
  - "birthday"
  - "place_of_birth"
- "known_for_department" exists
- "popularity" is a number
- "also_known_as[]" is present

---

⭐ Bonus Scenario

11. Add Movie to Watchlist

Method: "POST"

Endpoint:

/account/{account_id}/watchlist

Test objective:

Add a specific movie to an authenticated user's watchlist.

Request Body

{
  "media_type": "movie",
  "media_id": 550,
  "watchlist": true
}

Validations

- First request returns "201 Created" or "200 OK"
- Response contains:
  - "success: true"
- "status_message" confirms the item was added
- The same request is sent again
- Second request returns "200 OK"
- The movie information is correctly processed

---

📊 Testing Coverage

Area| Covered
Movie APIs| ✅
TV Show APIs| ✅
Genre APIs| ✅
Person APIs| ✅
Watchlist API| ✅ Bonus
GET Requests| ✅
POST Request| ✅ Bonus
Status Code Validation| ✅
Response Body Validation| ✅
JSON Validation| ✅
Query Parameters| ✅
Path Parameters| ✅
Authorization| ✅
Pagination Validation| ✅
Filtering Validation| ✅

---

📁 Project Structure

TMDB-API-Testing-Project/
│
├── TMDB-API-Testing-Project.postman_collection.json
└── README.md

---

▶️ How to Run

1. Download or clone the repository.
2. Open Postman.
3. Import the Postman Collection.
4. Configure your TMDB authentication details.
5. Select the required request.
6. Send the request.
7. Verify the response and test results.
8. The complete collection can also be executed using Postman's Collection Runner.

---

🎯 Skills Demonstrated

- API Testing
- Manual Testing
- Postman
- REST API Testing
- JSON
- HTTP Methods
- Bearer Token Authentication
- Query Parameters
- Path Parameters
- Response Validation
- Status Code Validation
- Data Validation
- Pagination Testing
- Filtering Testing
- Git & GitHub

---

👨‍💻 Author

Andrew Youssif

Software Tester | QC Engineer
