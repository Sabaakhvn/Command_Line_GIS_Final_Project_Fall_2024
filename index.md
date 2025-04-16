<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Side-by-Side Images with Arrow</title>
    <style>
        /* Set the background to a bright gray gradient palette */
        body {
            background: linear-gradient(135deg, #F5F5F5, #DDDDDD);
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
            gap: 20px;
            margin: 20px 0;
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
            <p>For my project on identifying the optimal location to purchase a home in New Jersey, I utilized multiple datasets sourced from the New Jersey Geographic Information Network (NJGIN) and the American Community Survey (ACS). The primary dataset, containing information on median income, home values, and residential property taxes at the census tract level, was obtained from NJGIN. This GeoJSON served as the foundational layer for spatial analysis and was enriched with additional demographic variables from the ACS, including population and commuting statistics, through table joins and data aggregation.

To further enhance the analysis, I aggregated race-related variables from the ACS into the median income, home value, and residential property tax dataset. These variables included racial groups such as American Indian and Alaska Native (B02001_004E), Asian (B02001_005E), Native Hawaiian and Other Pacific Islander (B02001_006E), and Other Race (B02001_007E). This integration allowed for a more comprehensive understanding of demographic distributions and their potential impact on housing and economic factors at the census tract level.

Datasets detailing school point locations, bus stops by transit line, and rail stations were also sourced from NJGIN to assess accessibility and quality-of-life factors. These datasets, updated as recently as 2023 and 2024 and provided in shapefile and GeoJSON format, were spatially joined to census tracts to integrate information on public transportation and proximity to schools.

From the ACS, I incorporated variables such as the total number of workers over 16 years old (B08101_001) and the number of workers commuting via public transportation (B08101_025) to evaluate commuting patterns and accessibility. Additionally, I calculated population density by deriving the area of each census tract in square miles from its geometry and dividing the total population by this area. This metric provided deeper insights into population distribution across tracts and its relationship with other socioeconomic factors.

As part of the final interactive map, I created heatmaps to visually represent median income and population density across the Morris County. These heatmaps provided an intuitive way to identify spatial patterns and disparities, helping to highlight areas that align with the project's criteria for optimal residential locations.</p>
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
            <p> The "Public Transportation Utilization in Morris County" choropleth map visualizes the percentage of workers aged 16 and older who commute via public transportation across census tracts. Using data from the American Community Survey (ACS) 5-Year Estimates, two variables were analyzed: Total Workers (B08101_001) and Public Transit Commuters (B08101_025). The percentage of public transit commuters was calculated and mapped, with tracts shaded according to utilization levels. To ensure data reliability, the Coefficient of Variation (CV) was used as a precision measure, with tracts having a CV above 40% flagged with hatched patterns to indicate lower reliability. Census tracts with missing data were distinctly marked in gray. The choropleth map effectively highlights variations in public transit usage, with darker shades indicating higher utilization rates and lighter shades representing lower percentages. </p>
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
            This map provides a comprehensive spatial analysis of accessibility in Morris County by examining 15-minute walking buffers from transit stops and schools. The top-left panel shows areas within a 15-minute walk of transit stops (highlighted in blue), while the top-right panel displays similar walking buffers from schools (marked in green). The bottom-left panel combines these buffers, visualizing areas with overlapping accessibility to both transit and schools. Finally, the bottom-right panel integrates all data layers into a complete analysis, clearly illustrating transit stops, schools, and their respective buffers to identify regions with strong accessibility coverage and gaps. 
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
            This map provides a comprehensive analysis of accessibility coverage in Morris County, focusing on transit stops and schools at the census tract level. The Transit Coverage by Tract (top-left) and School Coverage by Tract (top-right) panels depict the percentage of each tract within a 15-minute walking buffer from transit stops and schools, respectively, with darker red shades indicating higher coverage. The Combined Coverage Score (bottom-left) integrates both transit and school coverage into a single metric, highlighting areas with the best overall accessibility. Finally, the Top 10 Tracts for Accessibility (bottom-right) identifies the ten census tracts with the highest combined scores, marking them in red and numbering them for clarity. 
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
