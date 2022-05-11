# CUPS and Printing

### What is CUPS?

CUPS (formerly an acronym for Common UNIX Printing System) is a modular printing system for Unix-like computer operating systems which allows a computer to act as a print server. A computer running CUPS is a host that can accept print jobs from client computers, process them, and send them to the appropriate printer. CUPS was originally developed by Apple but is now used in UNIX/Linux Systems around the world to manage print queues.

### How does Cerner use CUPS?

Cerner uses CUPS to manage backend printers for Cerner Millennium based applications. CUPS queues are best managed by the client through Olympus.

### Common CUPS commands?

| Command                    | Action                       |
| -------------------------- | ---------------------------- |
| cupsdisable \<printername> | Stops a print queue          |
| cupsenable \<printername>  | Enables a print queue        |
| lpstat -a \<printername>   | Queue Status                 |
| reject \<printername>      | Stop jobs from hitting queue |
| accept \<printername>      | Accept jobs in queue         |
| lpstat -p \<printername>   | Check printer status         |
| service cups start         | Start Cups Service           |
| service cups stop          | Stop Cups Service            |

### CUPS Web Interface?

CUPS has a web interface that makes it super easy to manage printers rather than using the Backend Commands for troubleshooting. CUPS web interface is going to always be on port 631. \
\
In your browser go to http://\<nodefqdn>:631 to see the web interface on that node.&#x20;

### Common Issues with CUPS?

Most printer issues are client caused. It's usually either network related OR the printer build wasn't configured correctly in Olympus. Validate everything looks ok. \
\
Does it print? Is the formatting correct? Can I see it in the CUPS Web Interface? Can I see jobs processing? Does a test print work? Can I ping the printer on the client side from our Appnode? Does the Olympus build look ok? Etc.\
\
These questions will point you where to look in troubleshooting the issue.&#x20;
