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
     
    <!-- Third Row -->
    <div class="image-container">   
        <img src="Complete_Analysis.png" alt="15 Minutes Walking Buffers from Schools and Transit Stops">
        
    <!-- Forth Row -->
    <div class="image-container">     
        <img src="Top_10.png" alt="Top 10 Locations for Accessibility">
    </div>
</body>
</html>
 


<iframe src=".html" height= "600" width= "600" ></iframe> 

You can explore this map [as its own web page here](morris_county_comprehensive_analysis.html).
