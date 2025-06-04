# ETL Lockbit Ransomware Leaked data

We've Extract, Tansformed, and Load (ETL) the leaked data related to Lockbit (at: lockbitapyx2kr5b7ma7qn6ziwqgbrij2czhcbojuxmgnwpkgv2yx2yd.onion). 
We've uncompressed the original file 'paneldb_dump.zip', it reveal a single file 'paneldb_dump.sql', and for each table in this .sql file we've created an isolated .parquet file.
This is how you can easily load the data to begin you analysis.  

```
# !pip install pandas pyarrow requests

import pandas as pd
import io
import requests

tables_list = ['api_history', 'btc_addresses', 'builds', 'builds_configurations', 'chats',
               'clients', 'events', 'events_seen', 'faq', 'files', 'invites', 'jobs',
               'migrations', 'news', 'pkeys', 'socket_messages', 'system_invalid_requests',
               'testfiles', 'users', 'visits']

for table in tables_list:
    base_url = "https://raw.githubusercontent.com/jjsantanna/etl_lockbit_leak/main/raw_parquet/"
    parquet_file = f"df_{table}.parquet"
    url = base_url + parquet_file

    try:
        response = requests.get(url)
        response.raise_for_status()  # Raise error for bad status codes
        df = pd.read_parquet(io.BytesIO(response.content))
        globals()[f'df_{table}'] = df  # Create variable dynamically
        print(f"df_{table} loaded, {len(df)} rows")
    except Exception as e:
        print(f"Failed to load df_{table}: {e}")
```

If you are not technical and you would like the data in another format, just DM me https://www.linkedin.com/in/jjcsantanna/
