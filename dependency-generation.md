The **quickest and easiest** approach is using **Oracle Data Dictionary queries + Graphviz**. Here are the step-by-step instructions:

## Quick Steps to Generate Dependency Graph:

### Step 1: Install Graphviz
```bash
# Windows (using Chocolatey)
choco install graphviz

# Mac (using Homebrew)
brew install graphviz

# Ubuntu/Debian
sudo apt-get install graphviz

# CentOS/RHEL
sudo yum install graphviz
```

### Step 2: Run the SQL Query
1. Connect to your Oracle database using SQL*Plus, SQL Developer, or any Oracle client
2. Replace `'YOUR_SCHEMA'` with your actual schema name in the query above
3. Run the first query and save the output to a text file (e.g., `dependencies.txt`)

### Step 3: Create DOT File
Create a file called `dependencies.dot` with this structure:
```
digraph dependencies {
    rankdir=LR;
    node [shape=box, style=rounded];
    
    // Paste your query results here
    "SCHEMA.PACKAGE1" -> "SCHEMA.PROCEDURE1";
    "SCHEMA.PACKAGE1" -> "SCHEMA.FUNCTION1";
    // ... more dependencies
}
```

### Step 4: Generate the Graph
```bash
# Generate PNG image
dot -Tpng dependencies.dot -o dependency_graph.png

# Generate SVG (scalable)
dot -Tsvg dependencies.dot -o dependency_graph.svg

# Generate PDF
dot -Tpdf dependencies.dot -o dependency_graph.pdf
```

### Alternative: One-Step Automation Script
If you want to automate this, create a simple script that:
1. Runs the SQL query and exports results
2. Wraps results in DOT format
3. Generates the graph

**Time required:** 5-10 minutes once Graphviz is installed.

**Why this is the easiest:**
- Uses Oracle's built-in metadata (no code parsing needed)
- Graphviz is lightweight and widely available
- Single SQL query captures most dependencies
- Works with any Oracle version

