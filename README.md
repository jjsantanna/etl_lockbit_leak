# ETL Lockbit Ransomware Leaked data

We've Extract, Tansformed, and Load the leaked data related to Lockbit (at: lockbitapyx2kr5b7ma7qn6ziwqgbrij2czhcbojuxmgnwpkgv2yx2yd.onion). 
We've uncompressed the original file (paneldb_dump.zip), it reveal a single file paneldb_dump.sql, and for each table in this .sql file we've created an isolated .parquet file.
This is how you can easily load the data to begin you analysis. Let me know if you need any different format. 

```
import pandas as pd

df_api_history = pd.read_parquet("raw_parquet/df_api_history.parquet")
df_btc_addresses = pd.read_parquet("raw_parquet/df_btc_addresses.parquet")
df_builds = pd.read_parquet("raw_parquet/df_builds.parquet")
df_builds_configurations = pd.read_parquet("raw_parquet/df_builds_configurations.parquet")
df_chats = pd.read_parquet("raw_parquet/df_chats.parquet")
df_clients = pd.read_parquet("raw_parquet/df_clients.parquet")
df_events = pd.read_parquet("raw_parquet/df_events.parquet")
df_events_seen = pd.read_parquet("raw_parquet/df_events_seen.parquet")
df_faq = pd.read_parquet("raw_parquet/df_faq.parquet")
df_files = pd.read_parquet("raw_parquet/df_files.parquet")
df_invites = pd.read_parquet("raw_parquet/df_invites.parquet")
df_jobs = pd.read_parquet("raw_parquet/df_jobs.parquet")
df_migrations = pd.read_parquet("raw_parquet/df_migrations.parquet")
df_news = pd.read_parquet("raw_parquet/df_news.parquet")
df_pkeys = pd.read_parquet("raw_parquet/df_pkeys.parquet")
df_socket_messages = pd.read_parquet("raw_parquet/df_socket_messages.parquet")
df_system_invalid_requests = pd.read_parquet("raw_parquet/df_system_invalid_requests.parquet")
df_testfiles = pd.read_parquet("raw_parquet/df_testfiles.parquet")
df_users = pd.read_parquet("raw_parquet/df_users.parquet")
df_visits = pd.read_parquet("raw_parquet/df_visits.parquet")
```
