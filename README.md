# Connect-MCP-Server-Claude-with-Starrocks
A repository for connecting MCP Server Claude with StarRocks to enable seamless data integration and analytics. This project demonstrates how to transfer and synchronize data between MCP Server Claude and StarRocks, providing a foundation for scalable, high-performance data processing and analysis.

```
{
    "mcpServers": {
        "mcp-server-starrocks": {
            "command": "docker",
            "args": [
                "run",
                "-i",
                "--rm",
                "--network",
                "host",
                "ghcr.io/metorial/mcp-container--starrocks--mcp-server-starrocks--mcp-server-starrocks",
                "mcp-server-starrocks"
            ],
            "env": {
                "STARROCKS_HOST": "localhost",
                "STARROCKS_PORT": "9030",
                "STARROCKS_USER": "root",
                "STARROCKS_PASSWORD": "",
                "CONNECTION_TIMEOUT": "30",
                "MAX_RETRY_ATTEMPTS": "5",
                "DEBUG": "true",
				"HIVE_METASTORE_HOST": "localhost",
                "HIVE_METASTORE_PORT": "9083",
                "HIVE_METASTORE_URI": "thrift://localhost:9083",
                "DEFAULT_CATALOG": "hudi_catalog_hms",
                "STARROCKS_CATALOG": "hudi_catalog_hms",
                "STARROCKS_DATABASE": "default",
                "ENABLE_CATALOG_SUPPORT": "true",
                "CATALOG_TYPE": "hudi"
            }
        }
    },
    "inputs": []
}
```

### Configuration Explanation

This configuration defines how to run the MCP Server for StarRocks using Docker and specifies the necessary environment variables for connecting to StarRocks and Hive Metastore.

- The `mcp-server-starrocks` service is started as a Docker container, using the `ghcr.io/metorial/mcp-container--starrocks--mcp-server-starrocks--mcp-server-starrocks` image.
- The container is run with host network mode for direct connectivity.

**Environment variables:**
- `STARROCKS_HOST`, `STARROCKS_PORT`, `STARROCKS_USER`, `STARROCKS_PASSWORD`: Connection details for the StarRocks instance.
- `CONNECTION_TIMEOUT`, `MAX_RETRY_ATTEMPTS`, `DEBUG`: Control connection timeout, retry behavior, and debug mode.
- `HIVE_METASTORE_HOST`, `HIVE_METASTORE_PORT`, `HIVE_METASTORE_URI`: Connection information for the Hive Metastore, which is used to manage Hudi table metadata.
- `DEFAULT_CATALOG`, `STARROCKS_CATALOG`, `STARROCKS_DATABASE`: Set the default catalog and database for StarRocks queries, typically pointing to the Hudi catalog and the default database.
- `ENABLE_CATALOG_SUPPORT`, `CATALOG_TYPE`: Enable catalog support and specify the type as Hudi for compatibility with Hudi tables.

This setup allows the MCP Server to connect to both StarRocks and Hive Metastore, enabling seamless data integration and management between your data sources.
