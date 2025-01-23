# LogAnalyser
Log Analyser

#!/bin/bash

if [ $# -ne 1 ]; then
    echo "Usage: $0 <logfile>"
    exit 1
fi

LOGFILE="$1"

if [ ! -f "$LOGFILE" ]; then
    echo "Error: File '$LOGFILE' not found!"
    exit 1
fi

echo "Analyzing log file: $LOGFILE"

# Extract and count occurrences of IP addresses
echo "Top 5 IP addresses with the most requests:"
awk '{print $1}' "$LOGFILE" | sort | uniq -c | sort -rn | head -5 | awk '{print $2 " - " $1 " requests"}'
echo

# Extract and count occurrences of request paths
echo "Top 5 most requested paths:"
awk -F'"' '{print $2}' "$LOGFILE" | awk '{print $2}' | sort | uniq -c | sort -rn | head -5 | awk '{print $2 " - " $1 " requests"}'
echo

# Extract and count occurrences of response status codes
echo "Top 5 response status codes:"
awk '{print $9}' "$LOGFILE" | sort | uniq -c | sort -rn | head -5 | awk '{print $2 " - " $1 " requests"}'
echo

# Extract and count occurrences of user agents
echo "Top 5 user agents:"
awk -F'"' '{print $6}' "$LOGFILE" | sort | uniq -c | sort -rn | head -5 | awk '{sub($1 FS, ""); print $0 " - " $1 " requests"}'


