# Undergraduate-Research-1
## Abstract
Yakima Valley, located in south-central Washington in the Columbia Plateau Regional Aquifer System (CPRAS), plays an essential role in agricultural activity: around one-third of the state’s vineyards. The area’s aquifer and land subsidence measurements have not been closely monitored or recorded in recent years. That leads to the question of the extent of the land subsidence of uplift due to the irrigation (i.e., groundwater use) and climate change (frequent droughts) that the Yakima Valley has experienced since 2017.  Land subsidence was detected by Interferometric Synthetic Aperture Radar (InSAR) by Sentinel-1 from 2017 to 2022. Minpy algorithm and SBAS are used to select interferometric pairs and analyze the deformation time series. The InSAR time series reveals the Yakima Valley has experienced land subsidence of up to 10 cm since 2017. The lithology in the area and the groundwater level measurements are encouraged to monitor the irrigation and determine the likelihood of the subsurface’s inelastic compaction.
## Introduction
Yakima Valley (Fig. 1) is situated in south-central Washington in the Columbia Plateau Regional Aquifer System (CPRAS) and holds a position of paramount importance in the agricultural industry: around one-third of the state’s vineyards (“Yakima Valley AVA,” 2023; Burns et al., 2011; Norman et al., 2004; Nation, 2009). This region relies heavily on its local aquifers, along with the Yakima River, which bisects the appellation for irrigation water supplies (“Yakima Valley AVA,” 2023). 

The geological framework underlying Yakima Valley comprises the Columbia River Basalt Group (CRBG), which erupted between 17 and 5.5 Ma (Reidel et al., 2003), coupled with overlying basin-fill sediments or overburden. Overburden is deposits of undifferentiated unconsolidated to semi-consolidated sedimentary materials spanning from the Miocene to Holocene epochs (Burns et al., 2011). Burns et al. (2011) also modeled the thickness of the overburden unit, which revealed the presence of significant, thick overburden strata within the valley.

A generalized geologic model has been established, which categorizes geological units within the region, including Overburden and five formations: Saddle Mountains Basalt, Mabton Interbed, Wanapum Basalt, Vantage Interbed, Grande Ronde Basalt, and Older Bedrock (Burns et al., 2011; Nation, 2009). As  ​​ Amelung et al. (1999) suggested, clay thickness controls the extent and magnitude of subsidence. However, the stratigraphy of the overburden is not studied or recorded thoroughly. 

Furthermore, Yakima Valley resides within the Yakima Fold and Thrust Belt (YFTB), an ongoing deformation series of faults and folds spanning northern Oregon and south-central Washington. The Folding and faulting of the basalt formations in the western part of the Columbia Basin, known as YFTB, originated concurrently with the CRGB eruptions. It has played a crucial role in shaping the topography of the Yakima Valley and the surrounding landscape (McCaffrey et al., 2016). Faults in the study area have the potential to act as a barrier to groundwater flow, leading to land subsidence. 

These considerations prompt the following questions: Is the Yakima Valley experiencing subsidence, uplift, or oscillation? And, do the observed deformations elicit concerns among farmers or residents in the region?

 ![Alt text](https://github.com/Benz-Poobua/Undergraduate-Research-1/blob/main/aoi.png)
Figure 1. The Yakima Valley is the area of interest (AOI), represented by the red rectangle. This area is bounded by Ahtanum Ridge and Horse Heaven Hill Ridge.
## Methodology
We utilized InSAR with the Sentinel-1 (C-band) satellite to detect land subsidence in the Yakima Valley. Data from 2017 to 2022 was gathered from ascending frames accessed through the Vertex Data Portal maintained by the Alaska SAR Facility (ASF). Two advanced algorithms were utilized for stacking and time-series analysis. The Short Baseline Subsets (SBAS) filter was employed to select interferogram pairs based on two criteria: a perpendicular baseline of less than 100 m and a temporal baseline ranging from 24 to 60 days, resulting in the selection of 153 interferogram pairs (Fig. 2). Additionally, the Miami INsar Time-series software in PYthon (MintPy) provided by OpenSARlab was employed to construct time series and perform stacking within the designated area. 

 ![Alt text](https://github.com/Benz-Poobua/Undergraduate-Research-1/blob/main/sbas.png)
Figure 2. The interferogram pairs are selected using SBAS. 

After defining and downloading the study area, our initial step involved obtaining the UID and API key to access the Climate Data Store (CDS), which hosts a database of atmospheric pressure crucial for tropospheric delay correction. Following this, we established the reference point using MinPy's default approach, wherein the algorithm automatically selected a pixel with the highest spatial coherence in the stack. Subsequently, we applied inversion to the small baseline network, enabling the calculation of the time series for the unwrapped phase concerning the first acquisition. To refine the data, we addressed interferograms by correcting tropospheric delay from ERA5 and DEM errors, incorporating phase deramping to eliminate long-wavelength component noise. The detailed procedure of this algorithm (Fig. 3) was thoroughly documented by Yunjun et al. (2019). In the MinPy sign convention, negative phase values indicate subsidence, while positive values signify uplift.

![Alt text](https://github.com/Benz-Poobua/Undergraduate-Research-1/blob/main/minpy.png)
Figure 3. The algorithm of MinPy by Yunjun et al. (2019)
## Result
The time series of interferograms was derived from the preceding steps, revealing temporal variations in phase differences across 153 selected interferograms. A subset of these, showcasing both land subsidence and uplift in the area, is available in the Supplementary Data section (Fig. S1-S7). These interferograms represent phase data from December 2016 to 2022, indicating dynamic changes in the region over time. The stacked interferogram (Fig. 4) visualizes the velocity in the line of sight (LOS) direction, highlighting a subsidence trend in the Yakima Valley or irrigation region. Additionally, examining a specific point (46.40327, -120.46686) in the stacked interferogram reveals a linear trend (Fig. 5) in displacement with a velocity or slope of -1.43 cm/yr (subsidence). The distribution of area displacement around the trend line suggests both uplift and subsidence, influenced by seasonal factors such as precipitation, discharge, and recharge time. The graph indicates that the Yakima Valley has experienced subsidence of up to 10 cm since 2017.

![Alt text](https://github.com/Benz-Poobua/Undergraduate-Research-1/blob/main/stacking.png)
Figure 4. The stacked interferogram was obtained from the selected time frame. The Yakima Valley is decorrelated by agricultural activities. 

![Alt text](https://github.com/Benz-Poobua/Undergraduate-Research-1/blob/main/trend.png)
Figure 5. The selected point (46.40327, -120.46686) displays the subsidence trend. For the sign convention, negative values mean the increase in range in the LOS direction. Positive values represent the decrease in range in the LOS direction. 
## Discussion
The Yakima Valley has exhibited subsidence of up to 10 cm since 2017; however, interferograms in the region display decorrelation linked to agricultural activities, resulting in numerous missing pixels. Additionally, potential noise introduced by snow accumulation near Mt. Adams can impact interferogram quality. Furthermore, crucial geotechnical data, including the stratigraphy of the shallow subsurface and groundwater levels in a time-series format, are currently unavailable. As a result, establishing a correlation between groundwater dynamics and ground deformation remains challenging. Detailed records of subsurface stratigraphy, particularly concerning factors like clay thickness, suggest the area's vulnerability to inelastic compaction, as observed by Amelung et al. (1999). Implementing groundwater level monitoring can help establish thresholds for irrigation use, preventing the region from groundwater overdraft and the associated risk of excessive stress on pre-consolidation stress.

## Conclusion
The Yakima Valley has experienced prolonged subsidence, up to 10 cm since 2017, as revealed by Sentinel-1 InSAR. Groundwater usage is suspected to be a contributing factor to this ground deformation. However, it is essential to gather supporting evidence, including data on groundwater levels and subsurface geology, to verify this claim. Consequently, the hypothesis suggesting permanent compaction in the Yakima Valley's subsurface remains inconclusive.

While the subsidence mechanism in the Yakima Valley remains unclear, the persistent nature of the subsidence signals a need for close monitoring of agricultural activities, particularly in vineyards. Further geotechnical surveys, including assessments of groundwater levels and shallow subsurface geology, are essential to understand the situation comprehensively. This approach will contribute to a more informed assessment of potential risks and mitigation strategies.

## Acknowledgement
I sincerely appreciate Professor David Schmidt (dasc@uw.edu) for his exceptional guidance and steadfast support throughout my research endeavor. Serving as my research supervisor, Prof. Schmidt has enriched my understanding of InSAR's theoretical complexities and shared invaluable insights and advice regarding the project, dataset, and data interpretation. His expertise and mentorship have played a pivotal role in shaping my research trajectory, and I am genuinely grateful for the opportunities to learn and develop under his guidance.

## References
Amelung, F., Galloway, D. L., Bell, J. W., Zebker, H. A., & Laczniak, R. J. (1999). Sensing the ups and downs of Las Vegas: InSAR reveals structural control of land subsidence and aquifer-system deformation. Geology, 27(6), 483-486.

Burns, E. R., Morgan, D. S., Peavler, R. S., & Kahle, S. C. (2011). Three-dimensional model of the geologic framework for the Columbia Plateau Regional Aquifer System, Idaho, Oregon, and Washington (No. 2010-5246). US Geological Survey.

McCaffrey, R., King, R. W., Wells, R. E., Lancaster, M., & Miller, M. M. (2016). Contemporary deformation in the Yakima fold and thrust belt estimated with GPS. Geophysical Journal International, 207(1), 1-11.

Nation, Y. (2009). Hydrogeologic framework of the Yakima River basin aquifer system, Washington.

Norman, D. K., Busacca, A. J., & Teissere, R. (2004). Geology of the Yakima Valley Wine Country--a Geologic Field Trip Guide from Stevenson to Zillah, Washington. Washington State Department of Natural Resources, Division of Geology and Earth Resources.

Reidel, S. P., Martin, B. S., & Petcovic, H. L. (2003). The Columbia River flood basalts and the Yakima fold belt.

Yakima Valley AVA. Washington State Wine Commission. (2023, September 8). https://www.washingtonwine.org/resource/yakima-valley-ava/ 

Yunjun, Zhang, Heresh Fattahi, and Falk Amelung. "Small baseline InSAR time series analysis: Unwrapping error correction and noise reduction." Computers & Geosciences 133 (2019): 104331.

