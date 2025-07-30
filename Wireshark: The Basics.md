
### **TryHackMe: Cyber Security 101**

**Room:** `Wireshark: The basics`  
**Status:** Completed  
**Date:** 2025-07-29

----------

### **Goal**

Learn how to use Wireshark to capture and analyze network traffic, identify protocols, filter packets, and extract useful information from network captures.

---------

### **Key Topics Covered**


**1. Introduction to Wireshark**

Wireshark is a powerful packet sniffing and network traffic analysis tool used to capture, inspect, and analyze network packets in real time or from saved captures (PCAP files).

**Common uses include:**

-   Detecting and troubleshooting network issues (load failure points, congestion)
    
-   Spotting security anomalies (rogue hosts, abnormal ports, suspicious traffic)
    
-   Investigating protocol behavior (response codes, payload details)
    

----------

**2. Wireshark GUI Components**

-   **Toolbar:** Menus and shortcuts for capturing, filtering, sorting, exporting, and merging packets.
    
-   **Display Filter Bar:** Main area to input filter expressions for quick queries.
    
-   **Recent Files:** Lists previously opened captures for quick access via double-click.
    
-   **Capture Filter & Interfaces:** Shows available network interfaces (e.g., lo, eth0) and capture filters to select sniffing points.
    
-   **Status Bar:** Displays tool status, profile info, and packet counts.
    

----------

**3. Packet List & Detail Panes**

Upon loading a PCAP, Wireshark displays:

-   **Packet List Pane:** Summary info for each packet (source/destination IP, protocol, info). Select packets here to view details.
    
-   **Packet Details Pane:** Hierarchical protocol breakdown of the selected packet.
    
-   **Packet Bytes Pane:** Hex and ASCII decoded view of raw packet data, highlights fields based on selection in details pane.
    

----------

**4. Packet Coloring**

Wireshark uses colors to quickly identify protocols and anomalies:

-   **Permanent rules:** Saved under preferences, accessible via `View → Coloring Rules`
    
-   **Temporary rules:** Active only during session, set via right-click or `View → Conversation Filter`
    
-   Toggle coloring with `Colourise Packet List` menu option.
    

----------

**5. Starting & Managing Captures**

-   Use the **blue shark fin button** to start capturing live traffic.
    
-   The **red button** stops capture; the **green button** restarts.
    
-   You can merge two PCAP files via `File → Merge`.
    
-   View capture file properties at `Statistics → Capture File Properties` or by clicking the PCAP icon bottom-left.
    

----------

**6. Packet Dissection (Protocol Layers)**

Packets dissected per OSI model layers:

-   **Frame (Layer 1):** Physical layer details, frame length, capture length, encapsulation.
    
-   **Data Link (Layer 2):** MAC addresses (source/destination), Ethernet info.
    
-   **Network (Layer 3):** IP addresses, TTL, checksums.
    
-   **Transport (Layer 4):** Protocol (TCP/UDP), ports, payload length, errors.
    
-   **Application (Layer 5):** Protocol specifics (HTTP, FTP, SMB), headers, content length.
    
-   **Application Data:** Raw data like HTML or text content.
    

Double-clicking packets opens detailed views for deeper analysis.

----------

**7. Packet Navigation**

-   Packets numbered sequentially to ease reference.
    
-   Use `Go → Go to Packet…` to jump to a specific packet number.
    
-   Use `Edit → Find Packet` to search inside packets by:
    
    -   Display filter
        
    -   Hex value
        
    -   String (case insensitive by default)
        
    -   Regex
        

Searches can be conducted in any pane: list, details, or bytes — knowing where data appears is key.

----------

**8. Marking and Commenting Packets**

-   **Marking:** Highlight important packets for quick identification (shown in black). Lost after closing file.
    
-   **Commenting:** Persistent notes saved with capture file until removed. Useful for collaboration or documentation.
    

----------

**9. Exporting Objects**

-   Extract objects from protocols like HTTP, SMB, DICOM, IMF, TFTP using:  
    `File → Export Objects → [protocol]`
    

Allows saving specific file streams (e.g., images, documents) from captures.

----------

**10. Time Display Formats**

-   Default time shown as "Seconds Since Beginning of Capture."
    
-   Recommended: Switch to UTC or other human-readable formats via  
    `View → Time Display Format` for easier analysis.
    

----------

**11. Expert Information**

Wireshark flags protocol states and anomalies (false positives possible):

-   Accessible via status bar or `Analyze → Expert Information`
    
-   Displays categorized alerts by severity: errors, warnings, notes.
    
-   Helps spot common problems quickly.
    

----------

**12. Packet Filtering**

Wireshark supports two filter types:

-   **Capture Filters:** Limit which packets are captured (pre-capture).
    
-   **Display Filters:** Filter which packets are shown post-capture without affecting capture file.
    

**Filtering techniques:**

-   **Apply as Filter:** Right-click a field and filter on its value immediately.
    
-   **Prepare as Filter:** Prepare filter query but don’t apply yet; combine multiple filters before applying.
    
-   **Conversation Filter:** Filters all related packets by IPs and ports, good for session analysis.
    
-   **Colorize Conversation:** Highlights packets without filtering, useful for visual grouping.
    

----------

**13. Custom Columns**

Add useful columns to the packet list pane:

-   Right-click a field and select `Apply as Column` to track values across all packets.
    
-   Enable or disable columns by clicking on the column headers.
    

----------

**14. Follow Stream**

Reconstruct application-layer data streams (e.g., HTTP conversations):

-   Use right-click on a packet and select `Follow → [Protocol] Stream` or via `Analyze → Follow [Protocol] Stream`.
    
-   Opens a new window showing reassembled raw traffic (including unencrypted data like usernames/passwords).
    
-   Wireshark automatically applies a display filter for that stream, removable by clicking the 'x'.

----

### **What I Learned**

-   Wireshark is essential for capturing and analyzing network traffic in real time or from saved files
    
-   The interface breaks down packets into list, details, and raw bytes for layered inspection
    
-   Colouring rules make it easier to spot different protocols and anomalies visually
    
-   Capture filters limit the data recorded, while display filters refine what is shown for analysis
    
-   Protocol dissection reveals details at each OSI layer, from Ethernet up to application protocols
    
-   Following a TCP or HTTP stream helps reconstruct and understand full conversations
    
-   Marking, commenting, and exporting objects help organize and share insights from captures
    
-   Expert info flags anomalies and warnings, guiding focused troubleshooting
    
-   Customizable columns let you highlight the most relevant packet details for your needs
    
-   Time display options improve readability and context during analysis

