#Simple Postgres Automation Using Docker
Simple automation for postgresql running in Docker using docker-compose

*Note: This guide will allow you to containerize Postgres; however, you must go into docker's settings and assure proper # cores and memory is allocated as large queries will take a very long time otherwise*

0. Ensure that docker is installed on your system. If you are a Windows user, and using Docker desktop, recent versions enforce the use of a WSL based engine. To set that up follow the MS guide [here](https://docs.docker.com/docker-for-windows/wsl/). If you are a Windows home user, make sure to use the WSL 2 instructions.  

1. Create a database.env file on the root of the project at the same level as the docker-compose.yml and define the following, ensure that the passwords you set follow compliant password requirements. Note: Postgres does not enforce strong passwords, but it is recommended to follow the strong rules that SQL Server uses found [here](https://docs.microsoft.com/en-us/sql/relational-databases/security/password-policy?view=sql-server-ver15):
    ```
        POSTGRES_USER=[USERNAME]
        POSTGRES_PASSWORD=[COMPLIANT PASSWORD]
        POSTGRES_DB=[DEFAULT DB NAME]
    ```

2. Open a terminal (for windows use Powershell), and cd into the directory of the docker-compose file

3. Run `docker-compose up --build` and wait for the terminal to read "Ready to Accept Connections"

4. open any Database GUI that has a valid postgres connection driver (This guide assumes the use of Datagrip):
	```
	Host: Localhost
	Port: 5432
	User: user defined in .env file
	Password: password defined in .env file
	Database: postgres
	```
5. When you are finished working, simply open a terminal (for windows use Powershell) and run `docker-compose down` or press `Ctrl+C` to stop the container if you are not running in detached mode this will turn off the server, freeing system resources and re-openeing port 5432