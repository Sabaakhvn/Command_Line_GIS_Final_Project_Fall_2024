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
<body>
    <h1>Morris County and New Jersey Boundaries</h1>
    <div class="image-container">
        <img src="Morris_County.png" alt="Morris County Boundaries">
        <img src="New_Jersey.png" alt="New Jersey Boundaries">
        <img src="Public_Transit_Utilization.png" alt="Public Transit Utilization Pattern in Morris County ">
        <img src="Complete_Analysis.png" alt="Walking Buffers from Schools and Transit Stops in Morris County">
        <img src="Top_10.png" alt="Top 10 Tracts for Accessibility">
    </div>
</body>
</html>
 


<iframe src=".html" height= "600" width= "600" ></iframe> 

You can explore this map [as its own web page here](morris_county_comprehensive_analysis.html).
