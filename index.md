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
            max-width: 600px;
            position: relative;
            z-index: 1;
        }

        .description {
            text-align: left;
            margin-top: 10px;
            font-size: 16px;
            color: #FFF;
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
            <img src="Morris_County.png" alt="Morris County Boundaries">
            <img src="New_Jersey.png" alt="New Jersey Boundaries">
          
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

    <!-- Description -->
    <div class="description">
        <p>For my project on identifying the optimal location to purchase a home in New Jersey, I utilized multiple datasets sourced from the New Jersey Geographic Information Network (NJGIN) and the American Community Survey (ACS). The primary dataset, containing information on median income, home values, and residential property taxes at the census tract level, was obtained from NJGIN. This GeoJSON served as the foundational layer for spatial analysis and was enriched with additional demographic variables from the ACS, including population and commuting statistics, through table joins and data aggregation.

To further enhance the analysis, I aggregated race-related variables from the ACS into the median income, home value, and residential property tax dataset. These variables included racial groups such as American Indian and Alaska Native (B02001_004E), Asian (B02001_005E), Native Hawaiian and Other Pacific Islander (B02001_006E), and Other Race (B02001_007E). This integration allowed for a more comprehensive understanding of demographic distributions and their potential impact on housing and economic factors at the census tract level.
Datasets detailing school point locations, bus stops by transit line, and rail stations were also sourced from NJGIN to assess accessibility and quality-of-life factors. These datasets, updated as recently as 2023 and 2024 and provided in shapefile and GeoJSON format, were spatially joined to census tracts to integrate information on public transportation and proximity to schools.

From the ACS, I incorporated variables such as the total number of workers over 16 years old (B08101_001) and the number of workers commuting via public transportation (B08101_025) to evaluate commuting patterns and accessibility. Additionally, I calculated population density by deriving the area of each census tract in square miles from its geometry and dividing the total population by this area. This metric provided deeper insights into population distribution across tracts and its relationship with other socioeconomic factors.

As part of the final interactive map, I created heatmaps to visually represent median income and population density across the Morris County. These heatmaps provided an intuitive way to identify spatial patterns and disparities, helping to highlight areas that align with the project's criteria for optimal residential locations.</p>
    </div>
        
    <h1>Public Transit Utilization in Morris County</h1>
    <div class="image-container">
        <img src="Public_Transit_Utilization.png" alt="Public Transit Utilization in Morris County" class="public-transit">
    </div>

    <!-- Description -->
    <div class="description">
        <p> The "Public Transportation Utilization in Morris County" choropleth map visualizes the percentage of workers aged 16 and older who commute via public transportation across census tracts. Using data from the American Community Survey (ACS) 5-Year Estimates, two variables were analyzed: Total Workers (B08101_001) and Public Transit Commuters (B08101_025). The percentage of public transit commuters was calculated and mapped, with tracts shaded according to utilization levels. To ensure data reliability, the Coefficient of Variation (CV) was used as a precision measure, with tracts having a CV above 40% flagged with hatched patterns to indicate lower reliability. Census tracts with missing data were distinctly marked in gray. The choropleth map effectively highlights variations in public transit usage, with darker shades indicating higher utilization rates and lighter shades representing lower percentages. </p>
     </div>

    <h1>15 Minutes Walking Buffers from Schools and Transit Stops in Morris County</h1>
    <div class="image-container">   
        <img src="Complete_Analysis.png" alt="15 Minutes Walking Buffers from Schools and Transit Stops in Morris County" class="complete-analysis">
    </div>   
    
    <!-- Description -->
    <div class="description">
This map provides a comprehensive spatial analysis of accessibility in Morris County by examining 15-minute walking buffers from transit stops and schools. The top-left panel shows areas within a 15-minute walk of transit stops (highlighted in red), while the top-right panel displays similar walking buffers from schools (marked in green). The bottom-left panel combines these buffers, visualizing areas with overlapping accessibility to both transit and schools. Finally, the bottom-right panel integrates all data layers into a complete analysis, clearly illustrating transit stops, schools, and their respective buffers to identify regions with strong accessibility coverage and gaps. 
    </div>
    
    <h1>Top 10 Locations for Accessibility in Morris County</h1>
    <div class="image-container">     
        <img src="Top_10.png" alt="Top 10 Locations for Accessibility in Morris County" class="top-10">
    </div>
    
    <!-- Description -->
    <div class="description">
This map provides a comprehensive analysis of accessibility coverage in Morris County, focusing on transit stops and schools at the census tract level. The Transit Coverage by Tract (top-left) and School Coverage by Tract (top-right) panels depict the percentage of each tract within a 15-minute walking buffer from transit stops and schools, respectively, with darker red shades indicating higher coverage. The Combined Coverage Score (bottom-left) integrates both transit and school coverage into a single metric, highlighting areas with the best overall accessibility. Finally, the Top 10 Tracts for Accessibility (bottom-right) identifies the ten census tracts with the highest combined scores, marking them in red and numbering them for clarity. 
    </div>
 
    <h1>Morris County Interactive Map</h1>
    <!-- Map Section -->
    <div class="map-container">
        <iframe src="morris_county_comprehensive_analysis.html" title="Interactive Map"></iframe>
    </div>
</body>
</html>
