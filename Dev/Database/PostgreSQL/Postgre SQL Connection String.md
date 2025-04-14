#Database-notes
## What is a Connection String?

- The ****connection string**** is a ****string**** of ****characters**** that defines all the details needed to make an ****application possible**** to allow connection to a [****database****](https://www.geeksforgeeks.org/what-is-database/) or other ****data sources.****  
    
- It typically includes the server ****location****, ****host****, ****database name,**** user credentials (username and password) and optional settings such as the ****port number****, ****encryption method**** or other parameters.  
    
- In databases like [****PostgreSQL****](https://www.geeksforgeeks.org/postgresql-tutorial/), a connection string simplifies the process by consolidating all these settings into a single, structured string for easy connection.  
    
- This will enable applications to access and interact with a ****database**** properly and thus ensure ****proper authentication**** and ****communication**** between the ****application**** and the server.

## Basic Format of a Connection String

The format of a ****PostgreSQL**** connection string is as follows:
```
postgresql://[user[:password]@][host][:port][/dbname][?param1=value1&param2=value2]
```

**Explanation***:
- **postgresql://:*** This prefix identifies the ****protocol****.
- **user:*** The username for the database.
- **password:** (Optional) Password for the user.
- ***host:** The address of the PostgreSQL server (e.g., localhost or an [****IP address****](https://www.geeksforgeeks.org/what-is-an-ip-address/)).
- **port:*** (Optional) The port where ***PostgreSQL*** is listening. **Default*** is **5432**.
- ***dbname:** The name of the database you want to connect to.
- **Parameters:** Additional connection options can be passed as URL parameters.

## Alternative Key-Value Format

In addition to the URI style, PostgreSQL also supports a ****key-value pair**** format for connection strings:

host=localhost port=5432 dbname=mydatabase user=myuser password=mypassword

Both formats work similarly and are widely supported by PostgreSQL clients.

## Examples of PostgreSQL Connection Strings

Below are some common connection string examples for different scenarios:

### Example 1: Local Connection (default port)

Suppose we need to connect to a PostgreSQL database hosted on a local server using a specific user, password, and database name****.****

postgresql://user:password@localhost/mydatabase

****Explanation:**** This is a PostgreSQL connection URL used to connect to a PostgreSQL database. It includes the username (`user`), password (`password`), host (`localhost`) and database name (`mydatabase`). This URL format is commonly used in applications to establish a connection with the specified PostgreSQL database.

### Example 2: Remote Server Connection

Suppose we need to establish a connection to a PostgreSQL database hosted at a remote server using connection credentials. The connection string must include the username, password, host address, port number and database name.

postgresql://user:password@192.168.1.100:5432/mydatabase

****Explanation:**** The provided connection string **`**postgresql://user:password@192.168.1.100:5432/mydatabase**`** specifies the necessary details for connecting to the PostgreSQL database. It includes the username (`user`), password (`password`), server IP address ****(******`**192.168.1.100**`******), port (******`**5432**`******)**** and the target database name (`mydatabase`).

### Example 3: Without Password (trust authentication)

Suppose we are trying to connect to a PostgreSQL database using a connection string but need clarification on its format and purpose.

postgresql://user@localhost/mydatabase

****Explanation****: The connection string `postgresql://user@localhost/mydatabase` is used to connect to a PostgreSQL database. It specifies the protocol (`postgresql`), the username (`user`), the host (`localhost`), and the database name (`mydatabase`). This string is essential for establishing a connection between your application and the PostgreSQL database.

### Example 4: With SSL

Suppose need to connect to a PostgreSQL database located on a local server using SSL encryption.

postgresql://user:password@localhost/mydatabase?sslmode=require

****Explanation****:

The connection string `postgresql://user:password@localhost/mydatabase?sslmode=require` is used to establish a secure connection to a PostgreSQL database. It includes the username (`user`), password (`password`), host (`localhost`), and database name (`mydatabase`).

## Server Connection Parameters

But PostgreSQL provides for many extra parameters that can be used to get more advanced configurations:

- ****sslmode:**** controls [SSL encryption](https://www.geeksforgeeks.org/secure-socket-layer-ssl/) (e.g., require, disable, verify-full).
- ****connect_timeout****: This specifies the number of seconds a program should wait to obtain a connection before it times out.
- ****application_name =**** gives a name to the client connection that may help ****track connections**** through server logs.

It passes additional configuration options directly to the PostgreSQL server.

### Example:

postgresql://user:password@localhost/mydatabase?sslmode=require&connect_timeout=10&application_name=myapp

## Environment Variables for Connection Strings

- PostgreSQL also supports defining connection parameters using [environment variables](https://www.geeksforgeeks.org/environment-variables-in-linux-unix/).  
    
- This method is often used in production environments to avoid exposing credentials in code.

### Common environment variables

- ****PGHOST****: Hostname of the PostgreSQL server.
- ****PGPORT****: Port number (default is 5432).
- ****PGUSER:**** Username for authentication.
- ****PGPASSWORD:**** Password for authentication.
- ****PGDATABASE:**** Database name.

## Connecting via Connection String in PostgreSQL Client Tools

Nearly all ****PostgreSQL client tools****, including psql or any PostgreSQL library for ****languages**** such as [Python](https://www.geeksforgeeks.org/python-programming-language-tutorial/), [Node.js](https://www.geeksforgeeks.org/nodejs/), or Java, can accept a connection string. For example, to connect using psql:

psql "postgresql://user:password@localhost/mydatabase"

## Troubleshooting with ****PostgreSQL Connection Strings****

Some of the most common issues users experience when working with connection strings are:

- ****Port Number Incorrect :**** Make sure [PostgreSQL](https://www.geeksforgeeks.org/postgresql-tutorial/) is on the correct port.
- ****Host Issues:**** Check that the host is reachable and not blocked by a firewall.
- ****Authentication Failures:**** Check the username and password and ****authentication**** method, ****for example****, whether the value for authentication or ****trust, md5, or scram-sha-256**** is explicitly set.
- ****SSL Configuration:**** If ****force_ssl**** is enabled, then specify an ****sslmode****.


**Resetting Password for the PostgreSQL User** 

Resetting the Password for `admin`
1. Switch to the `postgres` user:
	```
		sudo -i -u postgres
	``` 
2. Open the PostgreSQL Shell
```
psql
```
3. Update the password for the ```admin``` user:
```
ALTER USER admin PASSWORD 'new_secure_password';
```
4. Exit the shell:
```
\q
```

