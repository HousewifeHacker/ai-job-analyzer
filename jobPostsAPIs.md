# Remote Job Search APIs 📡

This document lists **free-to-use public APIs** that allow searching for remote job postings. You can use these endpoints to fetch jobs in JSON format, filter by category, location, or tags, and integrate them into applications or data analysis workflows.

> **Note:** Availability and rate limits may change. Always check the provider's terms of service before using an API in production.

---

## 1. Remotive

Remotive provides a simple JSON API for remote job listings.

- **Base URL:** `https://remotive.com/api/remote-jobs`

### Endpoints

| Path | Description |
|------|-------------|
| `/api/remote-jobs` | Retrieves all remote jobs.
| `/api/remote-jobs?category=software-dev` | Filter by job category.
| `/api/remote-jobs?search=python` | Full-text search query.
| `/api/remote-jobs?company_name=acme` | Filter by company name.

### Example Request

```bash
curl "https://remotive.com/api/remote-jobs?search=frontend&category=software-dev"
```

### Example Response

```json
{
  "jobs": [
    {
      "id": 1680495,
      "url": "https://remotive.com/remote-jobs/marketing/office-assistant-1680495",
      "title": "Office Assistant",
      "company_name": "Coalition Technologies ",
      "company_logo": "https://remotive.com/job/1680495/logo",
      "category": "Marketing",
      "tags": [
        "CSS",
        "excel",
        "frontend",
        "git",
        "html",
        "illustrator",
        "magento",
        "photoshop",
        "php",
        "shopify",
        "wordpress",
        "MySQL",
        "startup",
        "responsive",
        "themes",
        "bootstrap",
        "insurance",
        "jQuery",
        "Ajax"
      ],
      "job_type": "full_time",
      "publication_date": "2026-02-11T20:16:31",
      "candidate_required_location": "Worldwide",
      "salary": "$31,2k- $52k",
      "description": "<p>...HTML description...</p>"
    },
    ...
  ]
}
```

---

## 2. Remote OK 

- **Base URL:** `https://remoteok.io/api`

### Usage

Requesting the endpoint returns an array of job objects (the first element is metadata).

```bash
curl "https://remoteok.io/api"
```

You can filter by tags by appending query parameters, e.g.: `?tag=python&tag=react`.

### Example Response

```json
[
  {
    "last_updated": 1773057602,
    "legal": "API Terms of Service: Please link back (with follow, and without nofollow!) to the URL on Remote OK and mention Remote OK as a source, so we get traffic back from your site. If you do not we'll have to suspend API access.\n\nPlease don't use the Remote OK logo without written permission as it's a registered trademark, please DO use our name Remote OK though."
  },
  {
    "slug": "remote-senior-software-engineer-react-creative-chaos-1130645",
    "id": "1130645",
    "epoch": 1772726414,
    "date": "2026-03-05T16:00:14+00:00",
    "company": "Creative Chaos",
    "company_logo": "",
    "position": "Senior Software Engineer React",
    "tags": [
      "react",
      "software",
      "design",
      "jira",
      "front-end",
      "back-end",
      "security",
      "training",
      "test",
      "code",
      "web",
      "javascript",
      "html",
      "senior",
      "engineer",
      "engineering",
      "digital nomad"
    ],
    "description": "Job Summary text....",
    "location": "",
    "apply_url": "https://remoteOK.com/remote-jobs/remote-senior-software-engineer-react-creative-chaos-1130645",
    "salary_min": 0,
    "salary_max": 0,
    "logo": "",
    "url": "https://remoteOK.com/remote-jobs/remote-senior-software-engineer-react-creative-chaos-1130645"
  },
  ...
]
```

---

## 3. Adzuna

Adzuna offers a full job search API with a free tier, including remote filters. Requires an API key.

- **Base URL:** `https://api.adzuna.com/v1/api/jobs/{country}/search/{page}`
- **Docs:** [https://developer.adzuna.com/docs/search](https://developer.adzuna.com/docs/search)

### Example Request

http://api.adzuna.com:80/v1/api/jobs/gb/search/1?app_id={YOUR_APP_ID}&app_key={YOUR_APP_KEY}&results_per_page=20&what=javascript%20developer&what_exclude=java&where=london&sort_by=salary&salary_min=30000&full_time=1&permanent=1&content-type=application/json

### Example response

```json
{
  "__CLASS__": "Adzuna::API::Response::JobSearchResults",
  "results": [
    {
      "salary_min": 55000,
      "location": {
        "__CLASS__": "Adzuna::API::Response::Location",
        "area": [
          "UK",
          "London",
          "Central London",
          "The City"
        ],
        "display_name": "The City, Central London"
      },
      "salary_is_predicted": 0,
      "description": "...  and experience with more than one language a distinct advantage (python/ruby/perl/javascript/erlang).The Senior Developer Python will be involved in helping us to scale up and develop ...",
      "__CLASS__": "Adzuna::API::Response::Job",
      "created": "2013-10-23T19:32:43Z",
      "redirect_url": "http://adzuna.co.uk/jobs/land/ad/126977586?v=712F911142DFEF191FB2F0E068CD2734177B7F7E&utm_medium=api&utm_source=6eda9a47",
      "contract_time": "full_time",
      "title": "Senior Developer Python",
      "category": {
        "__CLASS__": "Adzuna::API::Response::Category",
        "label": "IT Jobs",
        "tag": "it-jobs"
      },
      "id": "126977586",
      "salary_max": 55000,
      "company": {
        "__CLASS__": "Adzuna::API::Response::Company",
        "display_name": "Exposed Solutions Limited"
      },
      "contract_type": "permanent"
    },
    ... up to another 19 ads here ...
  ]
}

```

---

## 4. TODO consider Additional Resources

- **We Work Remotely:** unofficial JSON feeds exist but no public API.
- **FlexJobs:** paid API only.
- **StackOverflow Jobs:** API shut down.

---

## Usage Tips

1. **Caching:** Many APIs do not enforce strict rate limits but caching responses can prevent hitting automation blocks.
2. **Filtering:** Use query parameters conservatively to reduce payload size.
3. **User-Agent:** Set a descriptive `User-Agent` header; some services may block default tooling signatures.
4. **Error Handling:** Check for HTTP 429 (Too Many Requests) and respect `Retry-After` headers if present.

---

