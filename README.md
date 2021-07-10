# A Task Manager API

This is a task manager api, nothing really more. Fork ME!

## Available routes

`POST /task`
create a new task

`GET /tasks`
returns a list of all the tasks

`GET /task/{id:int}`
returns a task by it's ID

`PUT /task/{id:int}`
updates a task by it's ID, at this stage, you need to send the entire task as a payload, not just a section of the task.

`DELETE /task/{id:int}`
Deletes a task by it's ID.

## Some notes

For development, I included a library called dotenv so you can store database secrets as environment variables
in `.env` files. It does not compile in release though.

Migrations run automatically in production and in development at production startup.

## Build Instructions

### For development

1. Create a database, (using sqlx-cli or just set it up yourself), and put the database url in a .env file
   (example provided). Must be postgres.

2. Add environment variable for rust logging, (example provided).

3. Run `cargo run`

### For production

Depending on your OS you might need to static compile the c standard library, (if you build on a newer linux distro but
are deploying to an older one). Other wise the commands are.

1. Run `cargo build --release`

For static compiling (needs musl to be installed on your linux distro)

1. Run `rustup toolchain install x86_64-unknown-linux-musl`

2. Run `cargo build --release --target x86_64-unknown-linux-musl`
