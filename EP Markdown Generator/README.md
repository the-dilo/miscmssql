# Purpose
The goal of this script is to generate tables using Git style Markdown from extended properties of common database objects. This allows for a free, extensible way to have a self-documenting database that can generate its own readme file alongside another solution to script a database into source control. 

It will create a table if properties exist for the following object types:

- Tables
- Views
- Stored Procedures
- Inline Table Functions
- Scalar Functions
- Triggers
- Default Constraints
- Check Constraints

# Usage
The only parameter for this procedure is a database name, since the original usage for this was to be included in a utility database:

    EXEC dbo.usp_genEPMarkdown @dbname = 'AdventureWorks'

It can be called via bcp to output a readme.md file to be pushed to a git repo:

    bcp "EXEC dbo.usp_genEPMarkdown @dbname = 'AdventureWorks'" queryout readme.md -S myserver.com -c