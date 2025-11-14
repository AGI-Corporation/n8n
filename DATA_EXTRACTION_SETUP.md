# Data Extraction Automation Workflow

## Multi-Source Integration Guide for n8n

Automated extraction from Mentibus, CreatorDB, Angel.co, Crunchbase, and LinkedIn to CSV and BigQuery.

## Data Sources

### 1. Mentibus API
- **Endpoint**: `https://api.mentibus.com/v1/creators`
- **Auth**: `Authorization: Bearer YOUR_API_KEY`
- **Data**: Creator profiles and insights

### 2. CreatorDB API
- **Endpoint**: `https://api.creatordb.com/v1/profiles`
- **Auth**: `X-API-Key: YOUR_API_KEY`
- **Data**: Creator profiles and metrics

### 3. Angel.co API
- **Endpoint**: `https://api.angel.co/v1/startups`
- **Auth**: `Authorization: Bearer YOUR_API_KEY`
- **Data**: Startup and founder information

### 4. Crunchbase API
- **Endpoint**: `https://api.crunchbase.com/v4/entities/organizations`
- **Auth**: `X-Crunchbase-User-Key: YOUR_API_KEY`
- **Data**: Company funding and intelligence

### 5. LinkedIn
- **Auth**: OAuth2 Connection
- **Data**: Professional profiles

## Output Destinations

### CSV Export
- Timestamped filename: `extracted_data_YYYY-MM-DD_HH-MM-SS.csv`
- Location: n8n file storage

### Google BigQuery
- **Project ID**: Your GCP project
- **Dataset**: `data_extraction`
- **Table**: `creators_companies`

## BigQuery Schema

```sql
CREATE TABLE data_extraction.creators_companies (
  id STRING,
  name STRING,
  email STRING,
  website STRING,
  industry STRING,
  funding FLOAT64,
  team_size INT64,
  description STRING,
  location STRING,
  country STRING,
  source STRING,
  extracted_at TIMESTAMP
);
```

## Workflow Architecture

**Stage 1: Extract** (5 parallel nodes)
- HTTP requests to each API
- OAuth2 for LinkedIn

**Stage 2: Merge**
- Combine results from all sources

**Stage 3: Transform**
- Normalize field names
- Map common fields
- Add extraction timestamp

**Stage 4: Output**
- Write CSV file
- Insert into BigQuery

## Configuration Steps

1. Set all API keys in HTTP nodes
2. Configure OAuth2 for LinkedIn
3. Set GCP project ID and BigQuery credentials
4. Create BigQuery table with schema above
5. Schedule workflow (optional)

## Output Format

Both CSV and BigQuery contain the same fields:
- id, name, email, website, industry, funding, team_size, description, location, country, source, extracted_at
