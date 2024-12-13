<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Side-by-Side Images with Arrow</title>
    <style>
        .image-container {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            margin: 20px 0;
            position: relative; /* For positioning the arrow */
        }

        .image-container img {
            height: auto;
            max-width: 400px;
            position: relative; /* For z-index */
            z-index: 1; /* Place images above arrow */
        }

        .public-transit,
        .complete-analysis,
        .top-10 {
            max-width: 1000px !important;
            width: 100%;
            height: auto;
        }

        h1 {
            text-align: center;
            margin: 30px 0;
            font-size: 24px;
        }

        /* Arrow container styling */
        .arrow-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none; /* Allows clicking through the arrow */
        }

        /* SVG arrow styling */
        .arrow {
            stroke: #ff4444;
            stroke-width: 3;
            fill: none;
            marker-end: url(#arrowhead);
        }
    </style>
</head>
<body>
    <h1>Morris County and New Jersey Boundaries</h1>
    <!-- First Row with Arrow -->
    <div class="image-container">
        <img src="Morris_County.png" alt="Morris County Boundaries">
        <img src="New_Jersey.png" alt="New Jersey Boundaries">
        
        <!-- SVG Arrow -->
        <svg class="arrow-container">
            <!-- Arrow definition -->
            <defs>
                <marker id="arrowhead" markerWidth="10" markerHeight="7" 
                refX="9" refY="3.5" orient="auto">
                    <polygon points="0 0, 10 3.5, 0 7" fill="#ff4444"/>
                </marker>
            </defs>
            
            <!-- Curved arrow path -->
            <path class="arrow" 
                  d="M 420 200 C 470 200, 470 150, 420 150" />
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
</body>
</html>
