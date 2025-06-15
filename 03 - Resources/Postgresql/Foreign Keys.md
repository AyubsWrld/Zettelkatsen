```postgresql
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