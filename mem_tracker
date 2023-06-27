#!/bin/bash

if [ -z "$1" ]; then
    echo "Error- PID to monitor was not provided."
    exit 1
fi

pid="$1"

while true; do
    mem_usage=$(ps -p "$pid" -o pid=,%mem=,%cpu=,rss=,vsz=,comm= --sort=-%mem |
                awk '{printf "%s\t%.2f%%\t%s\t%d KB\t%d KB\t%s\n", $1, $2, $3, $4, $5, $6}')

    if [ ! -z "$mem_usage" ]; then
        echo "$(date +'%Y-%m-%d %H:%M:%S') $mem_usage" >> memory_usage.log
    fi

    sleep 60
done
