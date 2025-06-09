#	--config_wss_biz_test

##	Description
This command is used to parse a JSON file, typically for testing WSS (Web Security Service) business policy configurations. The system expects a JSON file to have been made available for parsing prior to running this command. WSS refers to Web Security Service, which provides web security filtering, often integrated with cloud-based security providers similar to CSS (Cloud Security Service) implementations.

##  Arguments
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --config_wss_biz_test
```

##  Field descriptions
This command is primarily used to trigger a validation process. Output, if any, typically consists of status messages (e.g., success, failure) or error details related to the JSON parsing, rather than a structured tabular output.