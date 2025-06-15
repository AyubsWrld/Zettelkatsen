Enums are declared using the `CREATE TYPE <typename> AS ENUM`. They take strings as values and have ordering assigned to them ( in the order they were defined from least to greatest similar to how integral enums are ). 


```postgresql
CREATE TYPE SESSION_TYPE AS ENUM (
	'SESSION_TYPE_UNDEFINED' ,
	'SESSION_TYPE_TIME_BOUND',
	'SESSION_TYPE_GOAL_BASED',
	'SESSION_TYPE_APP_SPECIFIC',
	'SESSION_TYPE_LOCATION_BASED',
	'SESSION_TYPE_SCREEN_TIME_BUDGET',
	'SESSION_TYPE_DAILY_RECURRING'
)

CREATE TYPE SESSION_STATUS AS ENUM (
    'SESSION_STATUS_ERR',
    'SESSION_STATUS_ACTIVE',
    'SESSION_STATUS_INACTIVE',
    'SESSION_SUSPENDED',
    'SESSION_EXPIRED',
) ; 

CREATE TABLE Sessions (
  session_id    UUID            PRIMARY KEY NOT NULL, 
  guardian_id   UUID            NOT NULL,
  user_ids      UUID[],
  status        SESSION_STATUS  DEFAULT 'SESSION_STATUS_INACTIVE',
  session_type  SESSION_TYPE    NOT NULL,

  FOREIGN KEY (guardian_id) REFERENCES users(user_id)
);
```


___
Tags: #neovim #lsp