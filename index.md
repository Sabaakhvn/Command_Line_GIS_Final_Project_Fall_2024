<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Side-by-Side Images</title>
    <style>
        .image-container {
            display: flex;
            justify-content: center; /* Center images horizontally */
            align-items: center; /* Align images vertically */
            gap: 20px; /* Space between images */
        }
        .image-container img {
            height: auto; /* Preserve aspect ratio */
        }
        .public-transit {
            max-width: 800px; /* Increase the width of Public Transit Utilization */
            height: auto; /* Maintain aspect ratio */
        }
        .complete-analysis {
            max-width: 800px; /* Increase the width of Complete Analysis */
            height: auto; /* Maintain aspect ratio */
        }
        .top-10 {
            max-width: 800px; /* Increase the width of Top 10 */
            height: auto; /* Maintain aspect ratio */
        }
    </style>
</head>
<body>
    <h1>Morris County and New Jersey Boundaries</h1>
    <!-- First Row -->
    <div class="image-container">
        <img src="Morris_County.png" alt="Morris County Boundaries">
        <img src="New_Jersey.png" alt="New Jersey Boundaries">
    </div>

    <h1>Public Transit Utilization in Morris County</h1>
    <!-- Second Row -->
    <div class="image-container">
        <img src="Public_Transit_Utilization.png" alt="Public Transit Utilization in Morris County" class="public-transit">
    </div>

    <h1>15 Minutes Walking Buffers from Schools and Transit Stops in Morris County</h1>
    <!-- Third Row -->
    <div class="image-container">   
        <img src="Complete_Analysis.png" alt="15 Minutes Walking Buffers from Schools and Transit Stops in Morris County" class="complete-analysis">
    </div>   

    <h1>Top 10 Locations for Accessibility in Morris County</h1>
    <!-- Fourth Row -->
    <div class="image-container">     
        <img src="Top_10.png" alt="Top 10 Locations for Accessibility in Morris County" class="top-10">
    </div>
</body>
</html>



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Side-by-Side Images</title>
    <style>
        .image-container {
            display: flex;
            justify-content: center; /* Center images horizontally */
            align-items: center; /* Align images vertically */
            gap: 20px; /* Space between images */
        }
        .image-container img {
            height: auto; /* Preserve aspect ratio */
        }
        .image-container img:first-child {
            width: auto; /* Keep Morris County image aspect ratio */
        }
        .image-container img:last-child {
            max-width: 400px; /* Set specific width for New Jersey */
        }
        
        /* Specific styling for individual images */
        img[src="Public_Transit_Utilization.png"] {
            max-width: 800px; /* Increase the width of Public Transit Utilization */
            height: auto; /* Keep aspect ratio */
        }
        img[src="Complete_Analysis.png"] {
            max-width: 800px; /* Increase the width of Complete Analysis */
            height: auto; /* Keep aspect ratio */
        }
        img[src="Top_10.png"] {
            max-width: 800px; /* Increase the width of Top 10 */
            height: auto; /* Keep aspect ratio */
        }
    </style>
</head>
<h1>Morris County and New Jersey Boundaries</h1>
    
    <!-- First Row -->
    <div class="image-container">
        <img src="Morris_County.png" alt="Morris County Boundaries">
        <img src="New_Jersey.png" alt="New Jersey Boundaries">
    </div>

<h1>Public Transit Utilization in Morris County</h1>
    <!-- Second Row -->
    <div class="image-container">
        <img src="Public_Transit_Utilization.png" alt="Public Transit Utilization in Morris County">
    </div>

<h1>15 Minutes Walking Buffers from Schools and Transit Stops in Morris County</h1>
    <!-- Third Row -->
    <div class="image-container">   
        <img src="Complete_Analysis.png" alt="15 Minutes Walking Buffers from Schools and Transit Stops in Morris County">
    </div>   

<h1>Top 10 Locations for Accessibility in Morris County</h1>
    <!-- Forth Row -->
    <div class="image-container">     
        <img src="Top_10.png" alt="Top 10 Locations for Accessibility in Morris County">
    </div>
</body>
</html>
 


<iframe src=".html" height= "600" width= "600" ></iframe> 

You can explore this map [as its own web page here](morris_county_comprehensive_analysis.html).
