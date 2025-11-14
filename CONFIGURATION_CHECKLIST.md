# Configuration Checklist

## API Credentials Setup

- [ ] Mentibus API Key obtained from mentibus.com
- [ ] CreatorDB API Key obtained from creatordb.com
- [ ] Angel.co API Key obtained from angel.co
- [ ] Crunchbase API Key obtained from crunchbase.com
- [ ] LinkedIn OAuth2 credentials configured

## Google Cloud Setup

- [ ] Google Cloud Project created
- [ ] BigQuery enabled in project
- [ ] Service account created with BigQuery Editor role
- [ ] JSON credentials file downloaded
- [ ] BigQuery dataset created: `data_extraction`
- [ ] BigQuery table created: `creators_companies`

## n8n Configuration

- [ ] n8n instance running and accessible
- [ ] Import `WORKFLOW_TEMPLATE.json`
- [ ] Update all environment variables:
  - `MENTIBUS_API_KEY`
  - `CREATORDB_API_KEY`
  - `ANGEL_CO_API_KEY`
  - `CRUNCHBASE_API_KEY`
  - `GCP_PROJECT_ID`
- [ ] Configure LinkedIn OAuth2 connection
- [ ] Configure Google BigQuery credentials

## Workflow Setup

- [ ] All HTTP nodes configured with correct endpoints
- [ ] Authentication headers properly set
- [ ] Merge node configured to handle all 5 inputs
- [ ] Transform node tested with sample data
- [ ] CSV output filename pattern verified
- [ ] BigQuery connection authenticated
- [ ] BigQuery table schema matches output fields

## Testing

- [ ] Execute workflow manually
- [ ] Verify CSV file is created
- [ ] Check BigQuery table for new records
- [ ] Review extracted field names and values
- [ ] Validate data quality

## Scheduling (Optional)

- [ ] Configure trigger (daily/weekly)
- [ ] Test scheduled execution
- [ ] Monitor error logs
- [ ] Set up notifications for failures

## Output Validation

- [ ] CSV contains all 12 fields
- [ ] BigQuery table has matching schema
- [ ] Data types are correct (STRING, FLOAT64, INT64, TIMESTAMP)
- [ ] No null value issues
- [ ] Timestamps are in ISO 8601 format
- [ ] Extracted data is visible in both outputs
