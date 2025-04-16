<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Side-by-Side Images with Arrow</title>
    <style>
        /* Set the background to a light blue gradient palette */
        body {
            background: linear-gradient(135deg, #EFF8FF, #C8EFFE);
            color: #2c3e50; /* Dark text for readability */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
        }
        
        /* Student information header styles */
        .student-header {
            text-align: left;
            padding: 20px;
            margin-bottom: 30px;
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }

        .student-info {
            margin: 5px 0;
            font-size: 24px;
            font-weight: bold;
            line-height: 1.6;
            color: #2c3e50;
        }

        .school-info {
            font-size: 18px;
            color: #34495e;
        }
        
        .content-section {
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 30px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }
        
        .content-section:hover {
            transform: translateY(-5px);
        }

        .image-container {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 30px;
            margin: 30px 0;
            position: relative;
            flex-wrap: wrap;
        }

        .image-container img {
            height: auto;
            max-width: 600px;
            position: relative;
            z-index: 1;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .image-container img:hover {
            transform: scale(1.03);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
        }

        .description {
            text-align: left;
            margin-top: 20px;
            font-size: 16px;
            line-height: 1.8;
            color: #2c3e50;
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
            font-size: 38px;
            color: #2c3e50;
            text-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
            position: relative;
            padding-bottom: 10px;
        }
        
        h1::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: #2c3e50;
            border-radius: 2px;
        }

        iframe {
            border: 0;
            width: 100%; /* Make the map responsive */
            height: 1200px; /* Adjust the height of the map */
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        
        /* Navigation menu */
        .navigation {
            position: sticky;
            top: 0;
            background-color: #2c3e50;
            padding: 15px;
            border-radius: 0 0 10px 10px;
            margin-bottom: 20px;
            z-index: 100;
            display: flex;
            justify-content: center;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }
        
        .navigation a {
            color: white;
            text-decoration: none;
            margin: 0 15px;
            padding: 5px 10px;
            border-radius: 5px;
            transition: background-color 0.3s ease;
        }
        
        .navigation a:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }
        
        /* Add progress indicator */
        .progress-container {
            width: 100%;
            height: 5px;
            background: rgba(255, 255, 255, 0.3);
            position: fixed;
            top: 0;
            left: 0;
            z-index: 101;
        }
        
        .progress-bar {
            height: 5px;
            background: #2c3e50;
            width: 0%;
        }
        
        /* Back to top button */
        .back-to-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #2c3e50;
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            text-align: center;
            line-height: 50px;
            font-size: 24px;
            cursor: pointer;
            opacity: 0;
            transition: opacity 0.3s ease;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
            z-index: 99;
        }
        
        .back-to-top.visible {
            opacity: 1;
        }
        
        /* Add image captions */
        .image-wrapper {
            position: relative;
            margin: 10px;
        }
        
        .image-caption {
            background-color: rgba(44, 62, 80, 0.8);
            color: white;
            padding: 10px;
            border-radius: 0 0 8px 8px;
            font-size: 14px;
            text-align: center;
        }
    </style>
</head>
<body>
    <!-- Progress bar -->
    <div class="progress-container">
        <div class="progress-bar" id="progressBar"></div>
    </div>
    
    <!-- Navigation menu -->
    <div class="navigation">
        <a href="#student-info">Student Info</a>
        <a href="#county-boundaries">County Boundaries</a>
        <a href="#transit-utilization">Transit Utilization</a>
        <a href="#walking-buffers">Walking Buffers</a>
        <a href="#top-locations">Top Locations</a>
        <a href="#interactive-map">Interactive Map</a>
    </div>
    
    <!-- Student Information Header -->
    <div class="student-header" id="student-info">
        <p class="student-info">Saba Akhavansadr</p>
        <p class="student-info school-info">Command Line GIS</p>
        <p class="student-info school-info">Fall 2024</p>
        <p class="student-info school-info">Professor Will Payne</p>
        <p class="student-info school-info">Bloustein School of Planning and Public Policy</p>
        <p class="student-info school-info">Rutgers University, New Brunswick, NJ</p>
    </div>
    
    <section class="content-section" id="county-boundaries">
        <h1>Morris County and New Jersey Boundaries</h1>
        <div class="image-container">
            <div class="image-wrapper">
                <img src="Morris_County.png" alt="Morris County Boundaries">
                <div class="image-caption">Morris County Boundaries Map</div>
            </div>
            <div class="image-wrapper">
                <img src="New_Jersey.png" alt="New Jersey Boundaries">
                <div class="image-caption">New Jersey State Boundaries Map</div>
            </div>
        </div>

        <!-- Description -->
        <div class="description">
            <p>This project aims to identify the optimal residential locations in New Jersey by leveraging spatial and demographic data. Primary datasets were obtained from the New Jersey Geographic Information Network (NJGIN) and the American Community Survey (ACS). The foundational dataset, sourced from NJGIN in GeoJSON format, includes census tract-level information on median household income, home values, and residential property taxes. This dataset was enriched through table joins and data aggregation with ACS variables related to population characteristics and commuting behavior.

To provide a more nuanced understanding of demographic distribution and its potential influence on housing and economic indicators, the analysis integrated race-specific variables from the ACS. These included population estimates for American Indian and Alaska Native (B02001_004E), Asian (B02001_005E), Native Hawaiian and Other Pacific Islander (B02001_006E), and Other Race (B02001_007E) groups.

Additional geospatial layers were incorporated to assess accessibility and quality-of-life factors. These included datasets on school locations, bus stops by transit line, and rail stations, all sourced from NJGIN in shapefile and GeoJSON formats and updated through 2023 and 2024. These were spatially joined to the census tract boundaries to evaluate proximity to educational and transit infrastructure.

Commuting behavior was assessed using ACS variables such as the total number of workers aged 16 and over (B08101_001) and the number commuting via public transportation (B08101_025). Population density was derived by calculating the tract area in square miles from geometric data and dividing the total population by this area, providing additional insight into spatial population distribution.

The final output includes interactive heatmaps visualizing median income and population density across Morris County. These visualizations help identify spatial patterns and disparities, supporting the project's goal of highlighting tracts that best meet the defined criteria for residential suitability.</p>
        </div>
    </section>
        
    <section class="content-section" id="transit-utilization">
        <h1>Public Transit Utilization in Morris County</h1>
        <div class="image-container">
            <div class="image-wrapper">
                <img src="Public_Transit_Utilization.png" alt="Public Transit Utilization in Morris County" class="public-transit">
                <div class="image-caption">Public Transit Utilization Choropleth Map</div>
            </div>
        </div>

        <!-- Description -->
        <div class="description">
            <p> The Public Transportation Utilization in Morris County choropleth map illustrates the proportion of workers aged 16 and older who commute via public transportation across census tracts. The analysis is based on data from the American Community Survey (ACS) 5-Year Estimates, specifically utilizing two variables: total workers (B08101_001) and workers commuting by public transit (B08101_025). The commuting percentage was calculated for each tract and visualized using graduated shading to represent varying levels of public transit utilization.

To account for data reliability, the Coefficient of Variation (CV) was employed as a measure of precision. Census tracts with a CV greater than 40% were flagged with hatched patterns to denote lower reliability, while tracts with missing data were indicated in gray. The resulting map provides a clear spatial representation of transit usage, with darker shades corresponding to higher rates of public transportation use and lighter shades indicating lower rates. </p>
        </div>
    </section>

    <section class="content-section" id="walking-buffers">
        <h1>15 Minutes Walking Buffers from Schools and Transit Stops in Morris County</h1>
        <div class="image-container">   
            <div class="image-wrapper">
                <img src="Complete_Analysis.png" alt="15 Minutes Walking Buffers from Schools and Transit Stops in Morris County" class="complete-analysis">
                <div class="image-caption">Walking Buffer Analysis from Schools and Transit Stops</div>
            </div>
        </div>   
        
        <!-- Description -->
        <div class="description">
            This map presents a detailed spatial analysis of accessibility in Morris County by delineating 15-minute walking buffers around transit stops and schools. The top-left panel displays areas within a 15-minute walk of transit stops, shown in blue, while the top-right panel highlights equivalent walking buffers from school locations, depicted in green. The bottom-left panel overlays these two datasets to identify zones with concurrent access to both transit and educational facilities. The bottom-right panel integrates all layers into a comprehensive visualization, illustrating the spatial distribution of transit stops, schools, and their respective accessibility zones. This combined view enables the identification of areas with high accessibility coverage as well as gaps in access.
        </div>
    </section>
    
    <section class="content-section" id="top-locations">
        <h1>Top 10 Locations for Accessibility in Morris County</h1>
        <div class="image-container">     
            <div class="image-wrapper">
                <img src="Top_10.png" alt="Top 10 Locations for Accessibility in Morris County" class="top-10">
                <div class="image-caption">Top 10 Census Tracts with Highest Accessibility Scores</div>
            </div>
        </div>
        
        <!-- Description -->
        <div class="description">
            This map offers a comprehensive assessment of accessibility in Morris County by evaluating proximity to transit stops and schools at the census tract level. The Transit Coverage by Tract (top-left) and School Coverage by Tract (top-right) panels display the percentage of each tract falling within a 15-minute walking buffer of transit stops and schools, respectively. Darker red shades represent higher levels of coverage. The Combined Coverage Score (bottom-left) merges these two metrics into a single index to identify areas with the highest overall accessibility. The Top 10 Tracts for Accessibility (bottom-right) highlights the ten census tracts with the highest combined scores, marking them in red and assigning numerical labels for easy identification.
        </div>
    </section>
 
    <section class="content-section" id="interactive-map">
        <h1>Morris County Interactive Map</h1>
        <!-- Map Section -->
        <div class="map-container">
            <iframe src="morris_county_comprehensive_analysis.html" title="Interactive Map"></iframe>
        </div>
    </section>
    
    <!-- Back to top button -->
    <div class="back-to-top" id="backToTop">↑</div>
    
    <script>
        // Progress bar
        window.onscroll = function() {
            let winScroll = document.body.scrollTop || document.documentElement.scrollTop;
            let height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            let scrolled = (winScroll / height) * 100;
            document.getElementById("progressBar").style.width = scrolled + "%";
            
            // Show back to top button when scrolled down
            if (winScroll > 300) {
                document.getElementById("backToTop").classList.add("visible");
            } else {
                document.getElementById("backToTop").classList.remove("visible");
            }
        };
        
        // Back to top functionality
        document.getElementById("backToTop").addEventListener("click", function() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });
        
        // Add smooth scrolling to navigation links
        document.querySelectorAll('.navigation a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                document.querySelector(targetId).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
        
        // Add animation to images when they come into view
        const observerOptions = {
            threshold: 0.1
        };
        
        const observer = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = "1";
                    entry.target.style.transform = "translateY(0)";
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);
        
        document.querySelectorAll('.image-wrapper').forEach(img => {
            img.style.opacity = "0";
            img.style.transform = "translateY(20px)";
            img.style.transition = "opacity 0.5s ease, transform 0.5s ease";
            observer.observe(img);
        });
    </script>
</body>
</html>
