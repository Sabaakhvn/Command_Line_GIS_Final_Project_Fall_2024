<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Side-by-Side Images</title>
    <style>
        .image-container {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            margin: 20px 0; /* Add some vertical spacing between containers */
        }

        /* Style for the first row images (Morris County and New Jersey) */
        .image-container img {
            height: auto;
            max-width: 600px; /* Default size for first row images */
        }

        /* Larger size for the last three images */
        .public-transit,
        .complete-analysis,
        .top-10 {
            max-width: 900px !important; /* Increased from 800px to 900px */
            width: 100%; /* Makes image responsive */
            height: auto;
        }

        /* Make headings consistent */
        h1 {
            text-align: center;
            margin: 30px 0;
            font-size: 30px;
        }
        
        iframe {
            border: 0;
            width: 90%; /* Make the map responsive */
            height: 900px; /* Adjust the height of the map */
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

    <h1>Morris County Interactive Map</h1>
    <!-- Map Section -->
    <div class="map-container">
        <iframe src="morris_county_comprehensive_analysis.html" title="Morris County Interactive Map"></iframe>
    </div>
</body>
</html>


