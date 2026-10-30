Python MySQL ETL Reporting Pipeline
A sanitized educational demonstration of an ETL workflow: extract game-log-style records, validate and aggregate them, then export a structured Excel report. Sample records are entirely synthetic. This is not a copy of the original workplace notebook.
Workflow
1. Extract — load synthetic CSV by default; optionally query an authorized MySQL database with bound date parameters.
2. Transform — validate schema, timestamps and numeric amounts; aggregate bets and payouts by provider.
3. Load — write an .xlsx report into the ignored output/ directory.
Run
python -m pip install -r requirements.txt
jupyter notebook notebooks/game_log_etl_pipeline.ipynb
Run all cells. By default no database connection is made. To connect to your own authorized MySQL source, copy .env.example to .env, fill in settings locally, and change USE_SAMPLE_DATA to False. Adapt the illustrative SQL schema to your own approved schema. The optional live mode assumes timestamps are already in the reporting timezone; the timezone label is not a conversion.
Security
- Never commit .env, production workbooks, real query outputs, internal provider IDs, or proprietary SQL.
- Use a least-privilege read-only database account and encrypted network transport as required by your environment.
- Rotate any credentials that have previously been disclosed.
- The original notebook used an external credential notebook and internal workbook row mappings; neither is included here.
- This sample is not a full production deployment: add tests, monitoring, explicit timezone conversions, and retry policy before operational use.
