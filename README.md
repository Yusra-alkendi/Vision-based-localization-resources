# Vision-based-Localization-Resources



## Table of Contents  
* [SURVEY PAPER](#Survey_Paper)  
* [GENERAL OVERVIEW OF LOCALIZATION TECHNIQUES](#GeneralOverviewofLocalizationTechniques)  
  * [Related Survey Papers on Visual Odometry](#RelatedSurveyPapersonVisualOdometry)  
  * [Related Survey Papers on Visual Inertial Odometry](#RelatedSurveyPapersonVisualInertialOdometry)  
* [VISUAL ODOMETRY VO](#Visual-Odometry)
  * [MOTION ESTIMATION](#part1)
    * [3D TO 3D ALGORITHM](#part2)
    * [3D TO 2D ALGORITHM](#part3)
    * [2D TO 2D ALGORITHM](#part4)
  * [KEY DESIGN CHOICES](#part5)
    * [CONVENTIONAL – APPEARANCE-BASED VO](#part6)
      * [Regional-based method](#part7)
      * [Optical Flow-based method](#part8)
    * [CONVENTIONAL – FEATURE-BASED VO](#part9)
    * [CONVENTIONAL – HYBRID-BASED VO](#part10)
    * [NON-CONVENTIONAL – MACHINE LEARNING-BASED VO](#part11)
  * [RECENT VO-BASED STUDIES](#partvo)
  
  
* [VISUAL INERTIAL ODOMETRY VIO](#Visual-Inertial-Odometry)  
  * [DEGREE OF DATA FUSION](#partA)
    * [LOOSELY-COUPLED VIO](#partA1)
    * [SEMI-TIGHTLY COUPLED VIO](#partA2)
    * [TIGHTLY-COUPLED VIO](#partA3)
  * [TYPE OF DATA FUSION](#partA4)
    * [FILTERING-BASED VIO](#partA5)
      * [EXTENDED AND UNSCENTED KALMAN FILTERS](#partA6)
      * [MULTI-STATE CONSTRAINT KALMAN FILTER](#partA7)
    * [OPTIMIZATION-BASED VIO](#part8)
  * [RECENT VOI-BASED STUDIES](#partvio)


* [LOCALIZATION TECHNIQUES IN LOW-VISIBILITY ENVIRONMENTS](#part10)

* [The MAIN COMPONENTS OF THE VISUAL-LOCALIZATION](#part11)

# SURVEY PAPER <a name="Survey_Paper"/>
Y. Alkendi, L. Seneviratne and Y. Zweiri, "[State of the Art in Vision-Based Localization Techniques for Autonomous Navigation Systems](https://ieeexplore.ieee.org/abstract/document/9438708)," in IEEE Access, vol. 9, pp. 76847-76874, 2021, doi: 10.1109/ACCESS.2021.3082778.   

# GENERAL OVERVIEW OF LOCALIZATION TECHNIQUES <a name="GeneralOverviewofLocalizationTechniques"/>
- S. A. S. Mohamed, M.-H. Haghbayan, T. Westerlund, J. Heikkonen, H. Tenhunen, and J. Plosila, "[A survey on odometry for autonomous navigation systems](https://ieeexplore.ieee.org/document/8764393)", IEEE Access, vol. 7, pp. 97466–97486, 2019.
## Related Survey Papers on Visual Odometry <a name="RelatedSurveyPapersonVisualOdometry"/>
-  D. Scaramuzza and F. Fraundorfer, "[Visual odometry Part I: The first 30 years and fundamentals](https://ieeexplore.ieee.org/abstract/document/6096039)," IEEE Robot. Autom. Mag., vol. 18, no. 4, pp. 80–92, Dec. 2011.
-  F. Fraundorfer and D. Scaramuzza,"[Visual odometry: PartII : Matching, robustness, optimization, and applications](https://ieeexplore.ieee.org/document/6153423)," IEEE Robot. Autom. Mag., vol. 19, no. 2, pp. 78–90, Jun. 2012.
-  M.O.A.Aqel,M.H.Marhaban,M.I.Saripan,andN.B.Ismail,"[Review of visual odometry: Types, approaches, challenges, and applications](https://springerplus.springeropen.com/articles/10.1186/s40064-016-3573-7)," SpringerPlus, vol. 5, no. 1, pp. 1–26, Dec. 2016.
-  S.Poddar,R.Kottath,andV.Karar,"[Motion estimation made easy: Evolution and trends in visual odometry](https://link.springer.com/chapter/10.1007/978-3-030-03000-1_13)," in Recent Advances in Computer Vision. Cham, Switzerland: Springer, 2019, pp. 305–331.
## Related Survey Papers on Visual Inertial Odometry <a name="RelatedSurveyPapersonVisualInertialOdometry"/>
- J.Gui,D.Gu,S.Wang,andH.Hu, "[A review of visual inertial odometry from filtering and optimisation perspectives](https://www.tandfonline.com/doi/abs/10.1080/01691864.2015.1057616)," Adv. Robot., vol. 29, no. 20, pp. 1289–1301, Oct. 2015.
- M.Shan,Y.Bi,H.Qin,J.Li,Z.Gao,F.Lin,andB.M.Chen,"[A brief survey of visual odometry for micro aerial vehicles](https://ieeexplore.ieee.org/document/7793198)," in Proc. 42nd Annu. Conf. IEEE Ind. Electron. Soc. (IECON), Oct. 2016, pp. 6049–6054.
- G. Huang, "[Visual-inertial navigation: A concise review](https://arxiv.org/abs/1906.02650)," in Proc. Int. Conf. Robot. Automat. (ICRA), May 2019, pp. 9572–9582.



# 1. VISUAL ODOMETRY VO <a name="Visual-Odometry"/>
## A. MOTION ESTIMATION <a name="part1"/>
  ### A.1 3D TO 3D ALGORITHM <a name="part2"/>
  ### A.2 3D TO 2D ALGORITHM <a name="part3"/>
  ### A.3 2D TO 2D ALGORITHM <a name="part4"/>
 ## B. KEY DESIGN CHOICES<a name="part5"/>
  ### B.1 CONVENTIONAL – APPEARANCE-BASED VO<a name="part6"/>
   #### B.1.1. Regional-based method<a name="part7"/>
   #### B.1.2. Optical Flow-based method<a name="part8"/>
  ### B.2 CONVENTIONAL – FEATURE-BASED VO<a name="part9"/>
  ### B.3 CONVENTIONAL – HYBRID-BASED VO<a name="part10"/>
  ### B.4 NON-CONVENTIONAL – MACHINE LEARNING-BASED VO<a name="part11"/>
 ## C. RECENT VO-BASED STUDIES<a name="partvo"/>
 

# 2. VISUAL INERTIAL ODOMETRY VIO <a name="Visual-Inertial-Odometry"/>

## A. DEGREE OF DATA FUSION <a name="partA"/>
### A.1 LOOSELY-COUPLED VIO <a name="partA1"/>
### A.2 SEMI-TIGHTLY COUPLED VIO <a name="partA2"/>
### A.3 TIGHTLY-COUPLED VIO <a name="partA3"/>
## B. TYPE OF DATA FUSION <a name="partA4"/>
### B.1 FILTERING-BASED VIO <a name="partA5"/>
#### B.1.1 EXTENDED AND UNSCENTED KALMAN FILTERS <a name="partA6"/>
#### B.1.2 MULTI-STATE CONSTRAINT KALMAN FILTER <a name="partA7"/>
### B.2 OPTIMIZATION-BASED VIO <a name="part8"/>
## C. RECENT VOI-BASED STUDIES <a name="partvio"/>



# LOCALIZATION TECHNIQUES IN LOW-VISIBILITY ENVIRONMENTS <a name="part10"/>

# The MAIN COMPONENTS OF THE VISUAL-LOCALIZATION <a name="part11"/>

![MAINCOMPONENTSOFVISUAL-LOCALIZATION](https://user-images.githubusercontent.com/87903019/126872863-4c44cdad-1e6f-49f2-8571-11292f67671a.png)




  


