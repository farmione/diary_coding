## High level overview
### SDD 1: Designing streaming platform

#### Requirements:
* Users can watch videos ( TV shows , documentary )
* Videos are uploaded by someone admin user
* Smooth streaming
* Users could be 2 million/day
* Users watches videos average 1hr/day 
* Scalable, available, reliable system
* Downloads are out of scope

#### Sub-system breakdown:
` Video Streaming Platform `  |  `Internal Video Upload System` | `REST APIs for subscription and user recmmendation`

    Video Streaming Platform
    ---------                     ---------    
    |  U    |     get video       |       |  if not cached get    ----
    |  S    | ------------------> |   C   | ------------------>   |''|  Source     
    |  E    | <------------------ |   D   | <------------------   |''| 
    |  R    |       via stream    |   N   |     return            ---- 
    ---------                     ---------  
 *  When downloading, streaming continues. after downloading content will be consumed from device
 
 *  As streaming continuously receive data from remote server , so right streaming protocol need to pick
 *  Some streaming protocols -   
                              `HTTP Live Streaming` 
                              `Microsoft Smooth Streaming` 
                              `Adobe HTTP Synamic Streaming` 
                              `Dynamic adaptive Streaming over HTTP` 
 * Use CDN to optimize latency

    `Video Upload Platform


