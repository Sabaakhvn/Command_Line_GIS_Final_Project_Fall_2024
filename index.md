<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Side-by-Side Images with Arrow</title>
    <style>
        /* Set the background color to black */
        body {
            background-color: black;
            color: white; /* Set text color to white for readability */
            #font-family: Arial, sans-serif; /* Optional: Add a clean font */
        }
        
        .image-container {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            margin: 20px 0;
            position: relative;
        }

        .image-container img {
            height: auto;
            max-width: 500px;
            position: relative;
            z-index: 1;
        }

        .description {
            text-align: center;
            margin-top: 10px;
            font-size: 16px;
            color: #555;
        }
        
        .public-transit,
        .complete-analysis,
        .top-10 {
            max-width: 900px !important;
            width: 100%;
            height: auto;
        }

        h1 {
            text-align: center;
            margin: 30px 0;
            font-size: 30px;
        }

        .arrow-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .arrow {
            stroke: #ff0000;
            stroke-width: 4;
            fill: none;
            marker-end: url(#arrowhead);
        }

        iframe {
            border: 0;
            width: 100%; /* Make the map responsive */
            height: 1200px; /* Adjust the height of the map */
        }
    </style>
</head>
<body>
    <h1>Morris County and New Jersey Boundaries</h1>
    <div class="image-container">
        <div>
            <img src="Morris_County.png" alt="Morris County Boundaries">
            <img src="New_Jersey.png" alt="New Jersey Boundaries">
        </div>
        
    <div class="description">
        <p>This map provides a detailed view of Morris County, including its municipalities and key boundaries.</p>
    </div>
          
        <!-- SVG Arrow -->
        <svg class="arrow-container">
            <defs>
                <marker id="arrowhead" markerWidth="10" markerHeight="7" 
                refX="9" refY="3.5" orient="auto">
                    <polygon points="0 0, 10 3.5, 0 7" fill="#ff0000"/>
                </marker>
            </defs>
            
            <!-- Curved arrow path pointing from NJ to Morris County -->
            <path class="arrow" 
                  d="M 380 200 C 300 200, 300 250, 380 250" />
        </svg>
    </div>

    <h1>Public Transit Utilization in Morris County</h1>
    <div class="image-container">
        <img src="Public_Transit_Utilization.png" alt="Public Transit Utilization in Morris County" class="public-transit">
    </div>

    <h1>15 Minutes Walking Buffers from Schools and Transit Stops in Morris County</h1>
    <div class="image-container">   
        <img src="Complete_Analysis.png" alt="15 Minutes Walking Buffers from Schools and Transit Stops in Morris County" class="complete-analysis">
    </div>   

    <h1>Top 10 Locations for Accessibility in Morris County</h1>
    <div class="image-container">     
        <img src="Top_10.png" alt="Top 10 Locations for Accessibility in Morris County" class="top-10">
    </div>

    <h1>Morris County Interactive Map</h1>
    <!-- Map Section -->
    <div class="map-container">
        <iframe src="morris_county_comprehensive_analysis.html" title="Interactive Map"></iframe>
    </div>
</body>
</html>
