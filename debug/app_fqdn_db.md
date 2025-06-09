#	--app_fqdn_db

##	Description
This command displays the current database of Fully Qualified Domain Names (FQDNs) and their associated applications and classes as recognized by the VeloCloud Edge. This information is used for application identification and policy enforcement.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --app_fqdn_db
FQDN   APPLICATION  CLASS

example_com:velocli>
```
*(Note: The example output provided is a header only. In a live system, this would be followed by rows of FQDNs, their corresponding applications, and classes.)*

##  Field descriptions
| Column      | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| FQDN        | The Fully Qualified Domain Name (e.g., `www.example.com`).                  |
| APPLICATION | The application identified by the VeloCloud Edge for the corresponding FQDN. |
| CLASS       | The classification of the application (e.g., social media, business, etc.). |