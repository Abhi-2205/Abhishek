
Step1 -Create a new Bash script file using touch or directly with a text editor like nano or vim.
Write Commands
touch monitor.sh
chmod +x monitor.sh


Step 2-  Open the script file in a text editor.
Write Command
nano monitor.sh

Step 3 - Start with a Shebang At the top of your script include  the shebang line to specify the script 
should be run in bash
Write script  
#!/bin/bash

Step 4 Start by adding the functions outlined in the previous steps. For example, you can add the function
to monitor cpu and memory
Write script
top_apps() {
    echo "Top 10 Applications by CPU and Memory Usage:"
    ps -eo pid,comm,%cpu,%mem --sort=-%cpu | head -n 11
}

Step 5 - At the end of your script, add a case statement to handle command-line arguments.

Write Script
case "$1" in
    -cpu) top_apps ;;
    -memory) memory_usage ;;
    -network) network_monitoring ;;
    -disk) disk_usage ;;
    -load) system_load ;;
    -processes) process_monitoring ;;
    -services) service_monitoring ;;
    *) echo "Usage: $0 {-cpu|-memory|-network|-disk|-load|-processes|-services}" ;;
esac

Step 6- If you want your script to run continuously and update the information every few seconds, implement a 
main loop
 
Write 
while true; do
    clear
    top_apps
    network_monitoring
    disk_usage
    system_load
    memory_usage
    process_monitoring
    service_monitoring
    sleep 5
done


After this save the script and exit

Step 7- Test the Script 
 
Command 
./monitor.sh

Step 8- est the command-line switches to view specific sections of the dashboard.
./monitor.sh -cpu
./monitor.sh -memory
./monitor.sh -network


OP-

Top 10 Applications by CPU and Memory Usage:
    PID COMMAND         %CPU %MEM
  25550 ps               100  0.0
   2173 Isolated Web Co 10.6  7.9
    864 Xorg             4.5  1.2
   2952 chrome           4.2  2.8
  22193 kworker/u24:2-f  4.1  0.0
   1523 firefox-esr      3.9  5.1
     11 kworker/u24:0-f  3.5  0.0
     91 kworker/u24:4-e  3.2  0.0
   2852 chrome           2.4  2.4
  18881 kworker/u24:1-e  1.9  0.0
./monitor.sh: line 19: network_monitoring: command not found
./monitor.sh: line 20: disk_usage: command not found
./monitor.sh: line 21: system_load: command not found
./monitor.sh: line 22: memory_usage: command not found
./monitor.sh: line 23: process_monitoring: command not found
./monitor.sh: line 24: service_monitoring: command not found


