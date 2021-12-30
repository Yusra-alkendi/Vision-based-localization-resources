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

If you find this paper useful in your research, please consider citing us:
```
@ARTICLE{9438708,  author={Alkendi, Yusra and Seneviratne, Lakmal and Zweiri, Yahya},  journal={IEEE Access}, title={State of the Art in Vision-Based Localization Techniques for Autonomous Navigation Systems}, year={2021},  volume={9},  number={},  pages={76847-76874},  doi={10.1109/ACCESS.2021.3082778}}) 
```


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
- S.Poddar,R.Kottath,andV.Karar, “[Motion estimation made easy: Evolution and trends in visual odometry]( https://link.springer.com/chapter/10.1007/978-3-030-03000-1_13),” in Recent Advances in Computer Vision. Cham, Switzerland: Springer, 2019, pp. 305–331. 
- C. G. Harris and J. M. Pike, “[3D positional integration from image sequences]( https://www.sciencedirect.com/science/article/abs/pii/0262885688900030),” Image Vis. Comput., vol. 6, no. 2, pp. 87–90, May 1988. 
- R. Munguia and A. Grau, "[Monocular SLAM for visual odometry]( https://ieeexplore.ieee.org/document/4447564),"  in Proc. IEEE Int. Symp. Intell. Signal Process., Oct. 2007, pp. 1–6. 
- 
## A. MOTION ESTIMATION <a name="part1"/>
-G.Balamurugan,J.Valarmathi,and V.P.S. Naidu,”[Survey on UAV navigation in GPS denied environments]( https://ieeexplore.ieee.org/document/7955787),” in Proc. Int. Conf. Signal Process., Commun., Power Embedded Syst. (SCOPES), Oct. 2016, pp. 198–204. 
  ### A.1 3D TO 3D ALGORITHM <a name="part2"/>
-  D. Scaramuzza and F. Fraundorfer, "[Visual odometry Part I: The first 30 years and fundamentals](https://ieeexplore.ieee.org/abstract/document/6096039)," IEEE Robot. Autom. Mag., vol. 18, no. 4, pp. 80–92, Dec. 2011.
  ### A.2 3D TO 2D ALGORITHM <a name="part3"/>
- L. Kneip, D. Scaramuzza, and R. Siegwart, “[A novel parametrization of the perspective-three-point problem for a direct computation of absolute camera position and orientation]( https://ieeexplore.ieee.org/document/5995464),” in Proc. IEEE Comput. Soc. Conf. Comput. Vis. Pattern Recognit., Jun. 2011, pp. 2969–2976. 

  ### A.3 2D TO 2D ALGORITHM <a name="part4"/>
- H. C. Longuet-Higgins, “[A computer algorithm for reconstructing a scene from two projections]( https://cseweb.ucsd.edu/classes/fa01/cse291/hclh/SceneReconstruction.pdf),” in Readings in Computer Vision: Issues, Problem, Principles, and Paradigms. San Mateo, CA, USA: Morgan Kaufmann, 1981, pp. 61–62. 
- D. Nister, "[An efficient solution to the five-point relative pose problem]( https://www.rose-hulman.edu/class/cs/csse461/handouts/Day37/SINGLES2.pdf)," IEEE Trans. Pattern Anal. Mach. Intell., vol. 26, no. 6, pp. 756–770, Jun. 2004.
- D. Nistér, O. Naroditsky, and J. Bergen, "[Visual odometry for ground vehicle applications]( https://onlinelibrary.wiley.com/doi/abs/10.1002/rob.20103)," J. Field Robot., vol. 23, no. 1, pp. 3–20, 2006. 
- K. Yousif, A. Bab-Hadiashar, and R. Hoseinnezhad, “[An overview to visual odometry and visual SLAM: Applications to mobile robotics]( https://link.springer.com/article/10.1007/s40903-015-0032-7),” Intell. Ind. Syst., vol. 1, no. 4, pp. 289–311, Dec. 2015.
- M.O.A.Aqel,M.H.Marhaban,M.I.Saripan,andN.B.Ismail, “[Review of visual odometry: Types, approaches, challenges, and applications]( https://springerplus.springeropen.com/articles/10.1186/s40064-016-3573-7),” SpringerPlus, vol. 5, no. 1, pp. 1–26, Dec. 2016.

 ## B. KEY DESIGN CHOICES<a name="part5"/>
- R.Gonzalez,F.Rodriguez,J.L.Guzman,C.Pradalier,andR.Siegwart, "[Combined visual odometry and visual compass for off-road mobile robots localization]( https://www.cambridge.org/core/journals/robotica/article/abs/combined-visual-odometry-and-visual-compass-for-offroad-mobile-robots-localization/DB00A7FB6012CF4E56951B669533C4F0)," Robotica, vol. 30, no. 6, pp. 865–878, Oct. 2012.
- D.ScaramuzzaandR.Siegwart, "[Appearance-guided monocular omnidirectional visual odometry for outdoor ground vehicles]( https://ieeexplore.ieee.org/abstract/document/4625958)," IEEE Trans. Robot., vol. 24, no. 5, pp. 1015–1026, Oct. 2008. 
- T.A.Ciarfuglia,G.Costante,P.Valigi,andE.Ricci,"[Evaluation of nongeometric methods for visual odometry]( https://www.sciencedirect.com/science/article/abs/pii/S0921889014001511)," Robot. Auton. Syst., vol. 62, no. 12, pp. 1717–1730, Dec. 2014, doi: 10.1016/j.robot.2014.08.001. 
- V. Guizilini and F. Ramos, "[Visual odometry learning for unmanned aerial vehicles]( https://ieeexplore.ieee.org/document/5979706)," in Proc. IEEE Int. Conf. Robot. Automat., May 2011, pp. 6213–6220.

  ### B.1 CONVENTIONAL – APPEARANCE-BASED VO<a name="part6"/>
- L. Frédéric, "[The visual compass: Performance and limitations of an appearance-based method]( http://onlinelibrary.wiley.com/doi/10.1002/rob.21514/abstract)," J. Field Robot., vol. 33, no. 1, pp. 1–17, 2006. [Online]. Available: http://onlinelibrary.wiley.com/doi/10.1002/rob.21514/abstract 

   #### B.1.1. Regional-based method<a name="part7"/>
 - N. Nourani-Vatani, J. Roberts, and M. V. Srinivasan, ‘‘[Practical visual odometry for car-like vehicles]( https://ieeexplore.ieee.org/document/5152403),’’ in Proc. IEEE Int. Conf. Robot. Automat., May 2009, pp. 3551–3557.
 - Y. Yu, C. Pradalier, and G. Zong, ‘‘[Appearance-based monocular visual odometry for ground vehicles]( https://ieeexplore.ieee.org/document/6027050),’’ in Proc. IEEE/ASME Int. Conf. Adv. Intell. Mechatronics (AIM), Jul. 2011, pp. 862–867. 
 - M. O. A. Aqel, M. H. Marhaban, M. I. Saripan, and N. B. Ismail, ‘‘[Adaptive-search template matching technique based on vehicle accel- eration for monocular visual odometry system]( https://onlinelibrary.wiley.com/doi/abs/10.1002/tee.22299),’’ IEEJ Trans. Electr. Electron. Eng., vol. 11, no. 6, pp. 739–752, Nov. 2016. 
 - I. Comport, E. Malis, and P. Rives, ‘‘[Accurate quadrifocal tracking for robust 3D visual odometry]( https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.331.9823&rep=rep1&type=pdf),’’ in Proc. IEEE Int. Conf. Robot. Automat., Apr. 2007, pp. 40–45.
 - A. I. Comport, E. Malis, and P. Rives, ‘‘[Real-time quadrifocal visual odometry]( https://hal.inria.fr/hal-00766839/document),’’ Int. J. Robot. Res., vol. 29, nos. 2–3, pp. 245–266, Feb. 2010. 
 - S. Lovegrove, A. J. Davison, and J. Ibañez-Guzmán, ‘‘[Accurate visual odometry from a rear parking camera]( https://www.doc.ic.ac.uk/~ajd/Publications/lovegrove_etal_iv2011.pdf),’’ in Proc. IEEE Intell. Vehicles Symp. (IV), Jun. 2011, pp. 788–793. 
 - D. Caruso, J. Engel, and D. Cremers, ‘‘[Large-scale direct SLAM for omnidirectional cameras]( https://ieeexplore.ieee.org/document/7353366),’’ in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Sep. 2015, pp. 141–148.
- J. Engel, V. Koltun, and D. Cremers, ‘‘[Direct sparse odometry]( https://ieeexplore.ieee.org/abstract/document/7898369),’’ IEEE Trans. Pattern Anal. Mach. Intell., vol. 40, no. 3, pp. 611–625, Mar. 2018. 

   #### B.1.2. Optical Flow-based method<a name="part8"/>
   
- D.V.García,L.F.Rojo,A.G.Aparicio,L.P.Castelló,andO.R.García, ‘‘[Visual odometry through appearance- and feature-based method with omnidirectional images]( https://www.hindawi.com/journals/jr/2012/797063/),’’ J. Robot., vol. 2012, pp. 1–13, Sep. 2012. 
- T.Brox,A.Bruhn,N.Papenberg,andJ.Weickert,‘‘[High accuracy optical flow estimation based on a theory for warping]( https://link.springer.com/chapter/10.1007/978-3-540-24673-2_3),’’ in Proc. Eur. Conf. Comput. Vis. Berlin, Germany: Springer, 2004, pp. 25–36. 
- Bruhn and J. Weickert, ‘‘[Towards ultimate motion estimation: Combining highest accuracy with real-time performance]( https://ieeexplore.ieee.org/document/1541328),’’ in Proc. IEEE Int. Conf. Comput. Vis., vol. 1, Oct. 2005, pp. 749–755.
- Y.-H. Kim, A. M. Martínez, and A. C. Kak, ‘‘[Robust motion estimation under varying illumination]( https://engineering.purdue.edu/RVL/Publications/Kim05Robust.pdf ),’’ Image Vis. Comput., vol. 23, no. 4, pp. 365–375, Apr. 2005.
- M.J.BlackandP.Anandan,‘‘[The robust estimation of multiple motions: Parametric and piecewise-smooth flow fields]( https://www.semanticscholar.org/paper/The-Robust-Estimation-of-Multiple-Motions%3A-and-Flow-Black-Anandan/eee90c038f43370a29b07e46f38dfe6527143a2c),’’ Comput. Vis. Image Understand., vol. 63, no. 1, pp. 75–104, Jan. 1996. 
- E. J. Corey and W.-G. Su, ‘‘[Relaxing the brightness constancy assump- tion in computing optical flow]( https://dspace.mit.edu/handle/1721.1/6477),’’ Tetrahedron Lett., vol. 28, no. 44, pp. 5241–5244, 1987.
- J. Campbell, R. Sukthankar, I. Nourbakhsh, and A. Pahwa, ‘‘[A robust visual odometry and precipice detection system using consumer-grade monocular vision]( https://ieeexplore.ieee.org/document/1570639),’’ in Proc. IEEE Int. Conf. Robot. Automat., Apr. 2005, pp. 3421–3427. 
- M. Hyslop and J. S. Humbert, ‘‘[Autonomous navigation in three- dimensional urban environments using wide-field integration of optic flow]( https://arc.aiaa.org/doi/10.2514/1.43778),’’ J. Guid., Control, Dyn., vol. 33, no. 1, pp. 147–159, Jan. 2010.
- V. Grabe, H. H. Bülthoff, and P. R. Giordano, ‘‘[On-board velocity estima- tion and closed-loop control of a quadrotor UAV based on optical flow]( https://ieeexplore.ieee.org/document/6225328),’’ in Proc. IEEE Int. Conf. Robot. Automat., May 2012, pp. 491–497. 
- V. Grabe, H. H. Bulthoff, and P. R. Giordano, ‘‘[Robust optical-flow based self-motion estimation for a quadrotor UAV]( https://ieeexplore.ieee.org/document/6386234?reload=true&arnumber=6386234),’’ in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst., Oct. 2012, pp. 2153–2159. 
- T. Low and G. Wyeth, ‘‘[Obstacle detection using optical flow](),’’ in Proc. Australas. Conf. Robot. Automat. (ACRA), 2005, pp. 1–10. 
- C. Kerl, J. Sturm, and D. Cremers, ‘‘[Robust odometry estimation for RGB-D cameras]( https://ieeexplore.ieee.org/document/6631104),’’ Revista Gestão, Inovação Tecnologias, vol. 3, no. 5, pp. 427–436, 2014. 
- I. Dryanovski, R. G. Valenti, and J. Xiao, ‘‘[Fast visual odometry and mapping from RGB-D data]( https://ieeexplore.ieee.org/document/6630889),’’ in Proc. IEEE Int. Conf. Robot. Automat., May 2013, pp. 2305–2310. 
- S.LiandD.Lee,‘‘[Fast visual odometry using intensity-assisted iterative closest point]( https://ieeexplore.ieee.org/abstract/document/7407366),’’ IEEE Robot. Autom. Lett., vol. 1, no. 2, pp. 992–999, Jul. 2016. 

   
  ### B.2 CONVENTIONAL – FEATURE-BASED VO<a name="part9"/>
- A. de la Escalera, E. Izquierdo, D. Martín, B. Musleh, F. García, and J. M. Armingol, ‘‘[Stereo visual odometry in urban environments based on detecting ground features]( http://www.sciencedirect.com/ science/article/pii/S0921889015303183),’’ Robot. Auton. Syst., vol. 80, pp. 1–10, Jun. 2016. [Online]. Available: http://www.sciencedirect.com/ science/article/pii/S0921889015303183 
- O. Saurer, P. Vasseur, R. Boutteau, C. Demonceaux, M. Pollefeys, and F. Fraundorfer, ‘‘[Homography based egomotion estimation with a com- mon direction]( https://hal.archives-ouvertes.fr/hal-01466853/document),’’ IEEE Trans. Pattern Anal. Mach. Intell., vol. 39, no. 2, pp. 327–341, Feb. 2017. 
- B. Guan, P. Vasseur, C. Demonceaux, and F. Fraundorfer, ‘‘[Visual odometry using a homography formulation with decoupled rotation and transla- tion estimation using minimal solutions]( https://ieeexplore.ieee.org/document/8460747),’’ in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2018, pp. 2320–2327. 
- J. Shi and C. Tomasi, ‘‘[Good features to track]( https://ieeexplore.ieee.org/document/323794),’’ in Proc. IEEE Conf. Comput. Vis. Pattern Recognit., 1994, pp. 593–600. [Online]. Available: https://ieeexplore.ieee.org/document/323794, doi: 10.1109/ CVPR.1994.323794. 
- J. Matas, O. Chum, M. Urban, and T. Pajdla, ‘‘[Robust wide-baseline stereo from maximally stable extremal regions]( https://www.sciencedirect.com/science/article/abs/pii/S0262885604000435),’’ Image Vis. Comput., vol. 22, no. 10, pp. 761–767, Sep. 2004. 
- T. Lindeberg, ‘‘[Feature detection with automatic scale selection]( https://link.springer.com/article/10.1023/A:1008045108935),’’ Int. J. Comput. Vis., vol. 30, no. 2, pp. 79–116, 1998. 
- D.G.Lowe,‘‘[Distinctive image features from scale-invariant key points]( https://link.springer.com/article/10.1023/B:VISI.0000029664.99615.94),’’ Int. J. Comput. Vis., vol. 60, no. 2, pp. 91–110, Nov. 2004. 
- E.Mair,G.D.Hager,D.Burschka,M.Suppa,andG.Hirzinger,‘‘[Adaptive and generic corner detection based on the accelerated segment test]( https://dl.acm.org/doi/10.5555/1888028.1888043),’’ in Proc. Eur. Conf. Comput. Vis. Berlin, Germany: Springer, 2010, pp. 183–196. 
- M.Calonder,V.Lepetit,M.Özuysal,T.Trzcinski,C.Strecha,andP.Fua, ‘‘[BRIEF: Computing a local binary descriptor very fast]( https://www.tugraz.at/fileadmin/user_upload/Institute/ICG/Images/team_lepetit/publications/calonder_pami11.pdf),’’ IEEE Trans. Pattern Anal. Mach. Intell., vol. 34, no. 7, pp. 1281–1298, Jul. 2012. 
- H. Bay, A. Ess, T. Tuytelaars, and L. Van Gool, ‘‘[Speeded-up robust features (SURF)]( https://www.sciencedirect.com/science/article/abs/pii/S1077314207001555),’’ Comput. Vis. Image Understand., vol. 110, no. 3, pp. 346–359, Jun. 2008. 
- D. G. Lowe, ‘‘[Object recognition from local scale-invariant features]( https://ieeexplore.ieee.org/document/790410),’’ in Proc. 7th IEEE Int. Conf. Comput. Vis., vol. 2, Sep. 1999, pp. 1150–1157 
- E.Rublee,V.Rabaud,K.Konolige,andG.Bradski,‘‘[ORB: An efficient alternative to SIFT or SURF]( https://ieeexplore.ieee.org/document/6126544),’’ in Proc. Int. Conf. Comput. Vis., Nov. 2011, pp. 2564–2571. 
- S. Leutenegger, M. Chli, and R. Y. Siegwart, ‘‘[BRISK: Binary robust invariant scalable keypoints]( https://ieeexplore.ieee.org/document/6126542),’’ in Proc. Int. Conf. Comput. Vis. (ICCV), 2011, pp. 2548–2555. 
- E. Salahat and M. Qasaimeh, ‘‘[Recent advances in features extraction and description algorithms: A comprehensive survey]( https://arxiv.org/abs/1703.06376),’’ in Proc. IEEE Int. Conf. Ind. Technol. (ICIT), Mar. 2017, pp. 1059–1063. 
- L.-P. Morency and R. Gupta, ‘‘[Robust real-time egomotion from stereo images]( https://ieeexplore.ieee.org/abstract/document/1246781),’’ in Proc. Int. Conf. Image Process., vol. 2, 2003, pp. 719–722. 
- D.Scaramuzza,A.Martinelli,andR.Siegwart,‘‘[A flexible technique for accurate omnidirectional camera calibration and structure from motion]( http://rpg.ifi.uzh.ch/docs/ICVS06_scaramuzza.pdf),’’ in Proc. 4th IEEE Int. Conf. Comput. Vis. Syst. (ICVS), Jan. 2006, p. 45. 
- B. Kitt, F. Moosmann, and C. Stiller, ‘‘[Moving on to dynamic environ- ments: Visual odometry using feature classification]( https://ieeexplore.ieee.org/abstract/document/5650517),’’ in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst., Oct. 2010, pp. 5551–5556. 
- B. Kitt, A. Geiger, and H. Lategahn, ‘‘[Visual odometry based on stereo image sequences with RANSAC-based outlier rejection scheme],’’ in Proc. IEEE Intell. Vehicles Symp., Jun. 2010, pp. 486–492. 
- I. Cvišić and I. Petrović, ‘‘[Stereo odometry based on careful feature selection and tracking]( https://ieeexplore.ieee.org/document/7324219),’’ in Proc. Eur. Conf. Mobile Robots (ECMR), Sep. 2015, p. 5. 
- L. De-Maeztu, U. Elordi, M. Nieto, J. Barandiaran, and O. Otaegui, “[A temporally consistent grid-based visual odometry framework for multi-core architectures]( https://dl.acm.org/doi/abs/10.1007/s11554-014-0425-y),” J. Real-Time Image Process., vol. 10, no. 4, pp. 759–769, Dec. 2015. 
- H. Badino, A. Yamamoto, and T. Kanade, “[Visual odometry by multi- frame feature integration]( https://www.ri.cmu.edu/pub_files/2013/12/badino_cvad13.pdf),” in Proc. IEEE Int. Conf. Comput. Vis. Work- shops, Dec. 2013, pp. 222–229. 
- I.KrešoandS.Šegvić, “[Improving the egomotion estimation by correcting the calibration bias]( https://www.scitepress.org/papers/2015/53161/53161.pdf),” in Proc. 10th Int. Conf. Comput. Vis. Theory Appl., 2015, pp. 347–356. 
- H. Rebecq, T. Horstschaefer, G. Gallego, and D. Scaramuzza, “[EVO: A geometric approach to event-based 6-DOF parallel tracking and map- ping in real time]( https://ieeexplore.ieee.org/document/7797445),’’ IEEE Robot. Autom. Lett., vol. 2, no. 2, pp. 593–600, Apr. 2017. 

  ### B.3 CONVENTIONAL – HYBRID-BASED VO<a name="part10"/>
- C. Forster, M. Pizzoli, and D. Scaramuzza, “[SVO: Fast semi-direct monocular visual odometry]( https://ieeexplore.ieee.org/document/6906584),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2014, pp. 15–22. 
- H.Silva,A.Bernardino,andE.Silva, “Probabilistic egomotion for stereo visual odometry]( https://vislab.isr.tecnico.ulisboa.pt/publications/15-IRS-HSilva.pdf),” J. Intell. Robot. Syst., vol. 77, no. 2, pp. 265–280, Feb. 2015. 
- J. Feng, C. Zhang, B. Sun, and Y. Song, “[A fusion algorithm of visual odometry based on feature-based method and direct method]( https://ieeexplore.ieee.org/document/8243070),” in Proc. Chin. Automat. Congr. (CAC), Oct. 2017, pp. 1854–1859. 
- H. Alismail, M. Kaess, B. Browning, and S. Lucey, “[Direct visual odom- etry in low light using binary descriptors]( https://www.cs.cmu.edu/~kaess/pub/Alismail17ral.pdf),” IEEE Robot. Autom. Lett., vol. 2, no. 2, pp. 444–451, Apr. 2017. 

  ### B.4 NON-CONVENTIONAL – MACHINE LEARNING-BASED VO<a name="part11"/>
- R. Roberts, H. Nguyen, N. Krishnamurthi, and T. Balch, “[Memory-based learning for visual odometry]( https://ieeexplore.ieee.org/document/4543185),” in Proc. IEEE Int. Conf. Robot. Automat., May 2008, pp. 47–52. 
- R. Roberts, C. Potthast, and F. Dellaert, “[Learning general optical flow subspaces for egomotion estimation and detection of motion anomalies]( https://ieeexplore.ieee.org/document/5206538),” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. Workshops (CVPR Workshops), Jun. 2009, pp. 57–64. 
- K.-W. Wan, Z. Li, and W.-Y. Yau, “[Learning visual odometry for unmanned aerial vehicles]( https://ieeexplore.ieee.org/document/8124556),” in Proc. IEEE 2nd Int. Conf. Signal Image Process. (ICSIP), Aug. 2017, pp. 316–320. 
- V.GuiziliniandF.Ramos, “[Semi-parametric models for visual odometry]( https://ieeexplore.ieee.org/document/6224775),” in Proc. IEEE Int. Conf. Robot. Automat., May 2012, pp. 3482–3489.
- V. Guizilini and F. Ramos, ‘‘Semi-parametric learning for visual odometry,’’ Int. J. Robot. Res., vol. 32, no. 5, pp. 526–546, Apr. 2013, doi: 10.1177/0278364912472245. 
- P. Gemeiner, P. Einramhof, and M. Vincze, “[Simultaneous motion and structure estimation by fusion of inertial and vision data]( https://journals.sagepub.com/doi/10.1177/0278364907080058),” Int. J. Robot. Res., vol. 26, no. 6, pp. 591–605, Jun. 2007. 
- L. Porzi, E. Ricci, T. A. Ciarfuglia, and M. Zanin, “[Visual-inertial tracking on Android for augmented reality applications]( https://ieeexplore.ieee.org/document/6348402),” in Proc. IEEE Workshop Environ. Energy Struct. Monitor. Syst. (EESMS), Sep. 2012, pp. 35–41. 
- K. Konda and R. Memisevic, “[Unsupervised learning of depth and motion]( https://arxiv.org/abs/1312.3429),” 2013, arXiv:1312.3429. [Online]. Available: http://arxiv. org/abs/1312.3429 
- V. Peretroukhin, L. Clement, and J. Kelly, “[Inferring sun direction to improve visual odometry: A deep learning approach]( https://journals.sagepub.com/doi/10.1177/0278364917749732),” Int. J. Robot. Res., vol. 37, no. 9, pp. 996–1016, Aug. 2018. 
- V. Mohanty, S. Agrawal, S. Datta, A. Ghosh, V. Dutt Sharma, and D. Chakravarty, “[DeepVO: A deep learning approach for monocu- lar visual odometry]( https://www.cs.ox.ac.uk/files/9026/DeepVO.pdf),” 2016, arXiv:1611.06069. [Online]. Available: http://arxiv.org/abs/1611.06069 
- L. Clement and J. Kelly, “[How to train a CAT: Learning canonical appearance transformations for direct visual localization under illumina- tion change]( https://arxiv.org/pdf/1709.03009.pdf),” IEEE Robot. Autom. Lett., vol. 3, no. 3, pp. 2447–2454, Jul. 2018. 
- J.Jiao,J.Jiao,Y.Mo,W.Liu,andZ.Deng, “[MagicVO:Anend-to-end hybrid CNN and bi-LSTM method for monocular visual odometry]( https://ieeexplore.ieee.org/document/8753500),” IEEE Access, vol. 7, pp. 94118–94127, 2019. 
- Q. Liu, R. Li, H. Hu, and D. Gu, “[Using unsupervised deep learn- ing technique for monocular visual odometry]( https://ieeexplore.ieee.org/document/8632844),’” IEEE Access, vol. 7, pp. 18076–18088, 2019. 
- H.Wang,X.Ban,F.Ding,Y.Xiao,andJ.Zhou, “[Monocular VO based on deep siamese convolutional neural network]( https://www.hindawi.com/journals/complexity/2020/6367273/),” Complexity, vol. 2020, pp. 1–13, Mar. 2020. 

 ## C. RECENT VO-BASED STUDIES<a name="partvo"/>
- W. Zhou, H. Fu, and X. An, “[A classification-based visual odometry approach]( https://ieeexplore.ieee.org/document/7783793),” in Proc. 8th Int. Conf. Intell. Hum.-Mach. Syst. Cybern. (IHMSC), vol. 2, Aug. 2016, pp. 85–89. 
- P. V. K. Borges and S. Vidas, “[Practical infrared visual odometry]( https://ieeexplore.ieee.org/document/7399731),”  IEEE Trans. Intell. Transp. Syst., vol. 17, no. 8, pp. 2205–2213, Aug. 2016. 
- I. Vanhamel, I. Pratikakis, and H. Sahli, “[Multiscale gradient water- sheds of color images]( https://ieeexplore.ieee.org/document/1208310),” IEEE Trans. Image Process., vol. 12, no. 6, pp. 617–626, Jun. 2003.
- B. Kueng, E. Mueggler, G. Gallego, and D. Scaramuzza, “[Low-latency visual odometry using event-based feature tracks]( https://ieeexplore.ieee.org/document/7758089),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Oct. 2016, pp. 16–23. 
- P. Liu, L. Heng, T. Sattler, A. Geiger, and M. Pollefeys, “[Direct visual odometry for a fisheye-stereo camera]( http://www.cvlibs.net/publications/Liu2017IROS.pdf),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Sep. 2017, pp. 1746–1752.
- L. Heng and B. Choi, “[Semi-direct visual odometry for a fisheye- stereo camera]( https://ieeexplore.ieee.org/document/7759600),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Oct. 2016, pp. 4077–4084. 
- R.Kottath,D.P.Yalamandala,S.Poddar,A.P.Bhondekar,andV.Karar, “[Inertia constrained visual odometry for navigational applications]( https://ieeexplore.ieee.org/document/8313714),” in Proc. 4th Int. Conf. Image Inf. Process. (ICIIP), Dec. 2017, pp. 1–4. 
- Y.Almalioglu,M.R.U.Saputra,P.P.B.D.Gusmao,A.Markham,and N. Trigoni, “[GANVO: Unsupervised deep monocular visual odometry and depth estimation with generative adversarial networks]( https://arxiv.org/abs/1809.05786),” in Proc. Int. Conf. Robot. Automat. (ICRA), May 2019, pp. 5474–5480. 
- M. Menze and A. Geiger, “[Object scene flow for autonomous vehicles]( https://ieeexplore.ieee.org/document/7298925),’’ in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2015, pp. 3061–3070.
- T. Zhou, M. Brown, N. Snavely, and D. G. Lowe, “[Unsupervised learning of depth and ego-motion from video]( https://arxiv.org/abs/1704.07813),” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jul. 2017, pp. 1851–1858. 
- C.Godard,O.M.Aodha,andG.J.Brostow, “[Unsupervisedmonocular depth estimation with left-right consistency]( https://arxiv.org/abs/1609.03677),” in Proc. IEEE Conf. Com- put. Vis. Pattern Recognit. (CVPR), Jul. 2017, pp. 270–279. 
- Z.YinandJ.Shi, “[GeoNet:Unsupervisedlearningofdensedepth,optical flow and camera pose]( https://arxiv.org/abs/1803.02276),” in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit., Jun. 2018, pp. 1983–1992. 
- R. Mahjourian, M. Wicke, and A. Angelova, “[Unsupervised learning of depth and ego-motion from monocular video using 3D geometric constraints]( https://arxiv.org/abs/1802.05522),” in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit., Jun. 2018, pp. 5667–5675. 
- A. Valada, N. Radwan, and W. Burgard, “[Deep auxiliary learning for visual localization and odometry]( https://arxiv.org/abs/1803.03642),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2018, pp. 6939–6946.
- J. Shotton, B. Glocker, C. Zach, S. Izadi, A. Criminisi, and A. Fitzgibbon, “[Scene coordinate regression forests for camera relocalization in RGB-D images]( https://openaccess.thecvf.com/content_cvpr_2013/papers/Shotton_Scene_Coordinate_Regression_2013_CVPR_paper.pdf),” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit., Jun. 2013, pp. 2930–2937. 
- Kendall, M. Grimes, and R. Cipolla, “[PoseNet: A convolutional network for real-time 6-DOF camera relocalization]( https://arxiv.org/abs/1505.07427),” in Proc. IEEE Int. Conf. Comput. Vis. (ICCV), Dec. 2015, pp. 2938–2946.
- S. Wang, R. Clark, H. Wen, and N. Trigoni, “[DeepVO: Towards end- to-end visual odometry with deep recurrent convolutional neural net- works]( https://www.cs.ox.ac.uk/files/9026/DeepVO.pdf),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2017, pp. 2043–2050. 
- I. Melekhov, J. Ylioinas, J. Kannala, and E. Rahtu, “[Relative cam- era pose estimation using convolutional neural networks]( https://arxiv.org/abs/1702.01381),” 2017, arXiv:1702.01381. [Online]. Available: https://arxiv.org/abs/1702.01381 
- A. Nicolai, R. Skeele, C. Eriksen, and G. A. Hollinger, “[Deep learning for laser based odometry estimation]( http://research.engr.oregonstate.edu/rdml/sites/research.engr.oregonstate.edu.rdml/files/final_deep_learning_lidar_odometry.pdf),” in Proc. RSS Workshop Limits Potentials Deep Learn. Robot., vol. 184, 2016, pp. 1–7. 
- A.Geiger,P.Lenz,andR.Urtasun, “[Are we ready for autonomous driving? The KITTI vision benchmark suite]( https://ieeexplore.ieee.org/document/6248074),” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit., Jun. 2012, pp. 3354–3361. 
- A.Geiger,J.Ziegler,andC.Stiller, “[StereoScan: Dense 3D reconstruction in real-time]( http://www.cvlibs.net/publications/Geiger2011IV.pdf),’’ in Proc. IEEE Intell. Vehicles Symp. (IV), Jun. 2011, pp. 963–968. 
- C. Jaramillo, L. Yang, J. P. Muñoz, Y. Taguchi, and J. Xiao, “[Visual odometry with a single-camera stereo omnidirectional system]( https://link.springer.com/article/10.1007/s00138-019-01041-9),” Mach. Vis. Appl., vol. 30, nos. 7–8, pp. 1145–1155, Oct. 2019. 
- L.Wang,Y.Shan,S.Li,andT.Kosaki, “[Estimating pose of omnidirectional camera by convolutional neural network]( https://ieeexplore.ieee.org/document/9015287),’’ in Proc. IEEE 8th Global Conf. Consum. Electron. (GCCE), Oct. 2019, pp. 201–202. 
- W. Dai, Y. Zhang, D. Sun, N. Hovakimyan, and P. Li, “[Multi-spectral visual odometry without explicit stereo matching]( https://arxiv.org/abs/1908.08814),” in Proc. Int. Conf. 3D Vis. (3DV), Sep. 2019, pp. 443–452.
- R. Mur-Artal and J. D. Tardós, “[ORB-SLAM2: An open-source SLAM system for monocular, stereo, and RGB-D cameras]( https://arxiv.org/abs/1610.06475),” IEEE Trans. Robot., vol. 33, no. 5, pp. 1255–1262, Oct. 2017. 
- S. Li, X. Wang, Y. Cao, F. Xue, Z. Yan, and H. Zha, “[Self-supervised deep visual odometry with online adaptation]( https://arxiv.org/abs/2005.06136), “ in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2020, pp. 6338–6347.
- H. Zhan, C. S. Weerasekera, J.-W. Bian, and I. Reid, “[Visual odometry revisited: What should be learnt?]( https://arxiv.org/abs/1909.09803)” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2020, pp. 4203–4210. 
- G. Zhai, L. Liu, L. Zhang, Y. Liu, and Y. Jiang, “[PoseConvGRU: A monocular approach for visual ego-motion estimation by learning]( https://www.sciencedirect.com/science/article/abs/pii/S003132031930487X),” Pattern Recognit., vol. 102, Jun. 2020, Art.no.107187, doi: 10.1016/j.patcog.2019.107187. 
- J.-L. Blanco-Claraco, F.-Á. Moreno-Dueñas, and J. González-Jiménez, “[The Málaga urban dataset: High-rate stereo and LiDAR in a realistic urban scenario]( https://journals.sagepub.com/doi/10.1177/0278364913507326),”  Int. J. Robot. Res., vol. 33, no. 2, pp. 207–214, Feb. 2014. 
- R.Mur-Artal,J.M.M.Montiel,andJ.D.Tardos, “[ORB-SLAM:Aversa- tile and accurate monocular SLAM system]( https://arxiv.org/abs/1502.00956),” IEEE Trans. Robot., vol. 31, no. 5, pp. 1147–1163, Oct. 2015. 
- M. R. U. Saputra, P. P. B. de Gusmao, S. Wang, A. Markham, and N. Trigoni, “[Learning monocular visual odometry through geometry- aware curriculum learning]( https://arxiv.org/abs/1903.10543),” in Proc. Int. Conf. Robot. Automat. (ICRA), May 2019, pp. 3549–3555. 
- J. Huang, S. Yang, T.-J. Mu, and S.-M. Hu, “[ClusterVO: Clustering moving instances and estimating visual odometry for self and surround- ings]( https://arxiv.org/abs/2003.12980),” in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2020, pp. 2165–2174. 
- K. M. Judd and J. D. Gammell, “[The oxford multimotion dataset: Multiple SE(3) motions with ground truth]( https://arxiv.org/abs/1901.01445),” IEEE Robot. Autom. Lett., vol. 4, no. 2, pp. 800–807, Apr. 2019. 
- I.A.Barsan,P.Liu,M.Pollefeys,andA.Geiger, “[Robust dense mapping for large-scale dynamic environments]( https://arxiv.org/abs/1905.02781),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2018, pp. 7510–7517. 
- P. Li and T. Qin, “[Stereo vision-based semantic 3D object and ego- motion tracking for autonomous driving]( https://arxiv.org/abs/1807.02062),” in Proc. Eur. Conf. Comput. Vis. (ECCV), 2018, pp. 646–661.
- J. Huang, S. Yang, Z. Zhao, Y.-K. Lai, and S. Hu, “[ClusterSLAM: A SLAM backend for simultaneous rigid body clustering and motion esti- mation]( https://openaccess.thecvf.com/content_ICCV_2019/papers/Huang_ClusterSLAM_A_SLAM_Backend_for_Simultaneous_Rigid_Body_Clustering_and_ICCV_2019_paper.pdf),” in Proc. IEEE/CVF Int. Conf. Comput. Vis. (ICCV), Oct. 2019, pp. 5874–5883. 

# 2. VISUAL INERTIAL ODOMETRY VIO <a name="Visual-Inertial-Odometry"/>
- J.-C. Piao and S.-D. Kim, “[Adaptive monocular visual–inertial SLAM for real-time augmented reality applications in mobile devices]( https://www.mdpi.com/1424-8220/17/11/2567),” Sensors, vol. 17, no. 11, p. 2567, Nov. 2017.

## A. DEGREE OF DATA FUSION <a name="partA"/>
### A.1 LOOSELY-COUPLED VIO <a name="partA1"/>
- J. Tardif, M. George, M. Laverne, A. Kelly, and A. Stentz, “[A new approach to vision-aided inertial navigation]( https://ieeexplore.ieee.org/document/5651059),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst., 2010, pp. 4161–4168. [Online]. Available: https://ieeexplore.ieee.org/document/5651059, doi: 10.1109/IROS.2010. 5651059. 
- Sirtkaya, B. Seymen, and A. A. Alatan, “[Loosely coupled Kalman filtering for fusion of visual odometry and inertial navigation]( https://ieeexplore.ieee.org/document/6641281),” in Proc. 16th Int. Conf. Inf. Fusion, 2013, pp. 219–226.
- D. Scaramuzza et al., “[Vision-controlled micro flying robots: From system design to autonomous navigation and mapping in GPS-denied environments]( https://ieeexplore.ieee.org/document/6880770),” IEEE Robot. Autom. Mag., vol. 21, no. 3, pp. 26–40, Sep. 2014. 
- Y. Liu, R. Xiong, Y. Wang, H. Huang, X. Xie, X. Liu, and G. Zhang, “[Stereo visual-inertial odometry with multiple Kalman filters ensemble]( https://ieeexplore.ieee.org/document/7480432),” IEEE Trans. Ind. Electron., vol. 63, no. 10, pp. 6205–6216, Oct. 2016. 
-K. Konolige, M. Agrawal, and J. Sola, “[Large-scale visual odometry for rough terrain]( https://link.springer.com/chapter/10.1007/978-3-642-14743-2_18),” in Robotics Research. Berlin, Germany: Springer, 2010, pp. 201–212. 
-N. S. Gopaul, J. Wang, and B. Hu, “[Loosely coupled visual odometry aided inertial navigation system using discrete extended Kalman filter with pairwise time correlated measurements]( https://ieeexplore.ieee.org/document/8075140),” in Proc. Forum Cooperat. Positioning Service (CPGPS), May 2017, pp. 283–288. 

### A.2 SEMI-TIGHTLY COUPLED VIO <a name="partA2"/>
- S. Weiss, M. W. Achtelik, S. Lynen, M. Chli, and R. Siegwart, “[Real- time onboard visual-inertial state estimation and self-calibration of MAVs in unknown environments]( https://ieeexplore.ieee.org/document/6225147),” in Proc. IEEE Int. Conf. Robot. Automat., May 2012, pp. 957–964. 
- Y. Ling, M. Kuse, and S. Shen, “[Edge alignment-based visual–inertial fusion for tracking of aggressive motions]( https://link.springer.com/article/10.1007/s10514-017-9642-0),” Auton. Robots, vol. 42, no. 3, pp. 513–528, Mar. 2018, doi: 10.1007/s10514-017-9642-0.

### A.3 TIGHTLY-COUPLED VIO <a name="partA3"/>

- A. I. Mourikis and S. I. Roumeliotis, “[A multi-state constraint Kalman filter for vision-aided inertial navigation]( https://ieeexplore.ieee.org/document/4209642),” in Proc. IEEE Int. Conf. Robot. Automat., Apr. 2007, pp. 3565–3572. 
- M. Bloesch, S. Omari, M. Hutter, and R. Siegwart, “[Robust visual inertial odometry using a direct EKF-based approach]( https://ieeexplore.ieee.org/document/7353389),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Sep. 2015, pp. 298–304.
- M. Bloesch, M. Burri, S. Omari, M. Hutter, and R. Siegwart, “[Iterated extended Kalman filter based visual-inertial odometry using direct photometric feedback]( https://www.research-collection.ethz.ch/handle/20.500.11850/263423),” Int. J. Robot. Res., vol. 36, no. 10, pp. 1053–1072, 2017. [Online]. Available: https://journals.sagepub.com/ doi/abs/10.1177/0278364917728574, doi: 10.1177/0278364917728574. 
- T. Qin, P. Li, and S. Shen, “[VINS-mono: A robust and versatile monoc- ular visual-inertial state estimator]( https://arxiv.org/abs/1708.03852),” IEEE Trans. Robot., vol. 34, no. 4, pp. 1004–1020, Aug. 2018, doi: 10.1109/TRO.2018.2853729.
- S. Leutenegger, S. Lynen, M. Bosse, R. Siegwart, and P. Furgale, “[Keyframe-based visual–inertial odometry using nonlinear optimization]( http://www.roboticsproceedings.org/rss09/p37.pdf),” Int. J. Robot. Res., vol. 34, no. 3, pp. 314–334, Mar. 2015, doi: 10.1177/0278364914554813.

## B. TYPE OF DATA FUSION <a name="partA4"/>
### B.1 FILTERING-BASED VIO <a name="partA5"/>
#### B.1.1 EXTENDED AND UNSCENTED KALMAN FILTERS <a name="partA6"/>
- F. Zheng, G. Tsai, Z. Zhang, S. Liu, C.-C. Chu, and H. Hu, “[Trifo- VIO: Robust and efficient stereo visual inertial odometry using points and lines]( https://ieeexplore.ieee.org/document/8594354),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Oct. 2018, pp. 3686–3693.
- M. Bloesch, S. Omari, M. Hutter, and R. Siegwart, “[Robust visual inertial odometry using a direct EKF-based approach]( https://ieeexplore.ieee.org/document/7353389),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Sep. 2015, pp. 298–304.
- J. Civera, O. G. Grasa, A. J. Davison, and J. M. M. Montiel, “[1-point RANSAC for EKF-based structure from motion]( https://ieeexplore.ieee.org/document/5354410),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst., 2009, pp. 3498–3504. [Online]. Available: https://ieeexplore.ieee.org/document/5354410, doi: 10.1109/IROS.2009.5354410. 
- M. Bloesch, M. Burri, S. Omari, M. Hutter, and R. Siegwart, “[Iterated extended Kalman filter based visual-inertial odometry using direct photometric feedback]( https://www.research-collection.ethz.ch/handle/20.500.11850/263423),” Int. J. Robot. Res., vol. 36, no. 10, pp. 1053–1072, 2017. [Online]. Available: https://journals.sagepub.com/ doi/abs/10.1177/0278364917728574, doi: 10.1177/0278364917728574. 
- Hardt-Stremayr and S. Weiss, “[Monocular visual-inertial odometry in low-textured environments with smooth gradients: A fully dense direct filtering approach]( https://ieeexplore.ieee.org/document/9196881),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2020, pp. 7837–7843. 
- G. Loianno, M. Watterson, and V. Kumar, “[Visual inertial odometry for quadrotors on SE(3)]( https://ieeexplore.ieee.org/document/7487292),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2016, pp. 1544–1551.
- S. Shen, Y. Mulgaonkar, N. Michael, and V. Kumar, “[Vision-based state estimation and trajectory control towards high-speed flight with a quadrotor]( http://www.roboticsproceedings.org/rss09/p32.pdf),” in Proc. Robot., Sci. Syst. (RSS), Jun. 2013. 
- J. Kelly and G. S. Sukhatme, “[Visual-inertial simultaneous localization, mapping and sensor-to-sensor self-calibration]( https://ieeexplore.ieee.org/document/5423178),” in Proc. IEEE Int. Symp. Comput. Intell. Robot. Automat. (CIRA), Dec. 2009, pp. 360–368.
- M. Brossard, S. Bonnabel, and J.-P. Condomines, “[Unscented Kalman filtering on lie groups]( https://hal.archives-ouvertes.fr/hal-01489204v3),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Sep. 2017, pp. 2485–2491. 
- G. Hu, W. Wang, Y. Zhong, B. Gao, and C. Gu, “[A new direct filter- ing approach to INS/GNSS integration]( https://www.sciencedirect.com/science/article/pii/S1270963817316498?casa_token=WZcC-c90P-oAAAAA:4UZ4Ao68WzgFXYxN4xBUBJBRB1TcU40ixHdG2ledY5fg4g-HktrcQoU-dUVWoHpkBeVBb7a2Fw),” Aerosp. Sci. Technol., vol. 77, pp. 755–764, Jun. 2018. 
- G.Hu,L.Ni,B.Gao,X.Zhu,W.Wang,andY.Zhong, “[Modelpredictive based unscented Kalman filter for hypersonic vehicle navigation with INS/GNSS integration]( https://ieeexplore.ieee.org/document/8945140),” IEEE Access, vol. 8, pp. 4814–4823, 2020. 
- Shen, Y. Zhang, J. Tang, H. Cao, and J. Liu, “[Dual-optimization for a MEMS-INS/GPS system during GPS outages based on the cubature Kalman filter and neural networks]( https://ur.booksc.me/book/77277211/92bcc0),” Mech. Syst. Signal Process., vol. 133, Nov. 2019, Art. no. 106222. 





#### B.1.2 MULTI-STATE CONSTRAINT KALMAN FILTER <a name="partA7"/>
- M.LiandA.I.Mourikis,‘‘High-precision,consistentEKF-basedvisual- inertial odometry,’’ Int. J. Robot. Res., vol. 32, no. 6, pp. 690–711, May 2013. ![image](https://user-images.githubusercontent.com/87903019/147775472-d4a9b62d-8017-4a09-8793-3b6ffd50a9cc.png)
- A. I. Mourikis and S. I. Roumeliotis, “[A multi-state constraint Kalman filter for vision-aided inertial navigation]( https://ieeexplore.ieee.org/document/4209642),” in Proc. IEEE Int. Conf. Robot. Automat., Apr. 2007, pp. 3565–3572. 
### B.2 OPTIMIZATION-BASED VIO <a name="part8"/>
- C. Forster, L. Carlone, F. Dellaert, and D. Scaramuzza, “[On-manifold preintegration for real-time visual-inertial odometry]( http://rpg.ifi.uzh.ch/docs/TRO16_forster.pdf),” IEEE Trans. Robot., vol. 33, no. 1, pp. 1–21, Feb. 2017.
- S. Leutenegger, S. Lynen, M. Bosse, R. Siegwart, and P. Furgale, “[Keyframe-based visual–inertial odometry using nonlinear optimization]( http://www.roboticsproceedings.org/rss09/p37.pdf),” Int. J. Robot. Res., vol. 34, no. 3, pp. 314–334, Mar. 2015, doi: 10.1177/0278364914554813. 
- R. Mur-Artal and J. D. Tardós, “[Visual-inertial monocular SLAM with map reuse]( https://ieeexplore.ieee.org/document/7817784),” IEEE Robot. Autom. Lett., vol. 2, no. 2, pp. 796–803, Apr. 2017. 
- T. Lupton and S. Sukkarieh, “[Visual-inertial-aided navigation for high- dynamic motion in built environments without initial conditions]( https://ieeexplore.ieee.org/document/6092505),” IEEE Trans. Robot., vol. 28, no. 1, pp. 61–76, Feb. 2012.
- S. Shen, N. Michael, and V. Kumar, “[Tightly-coupled monocular visual-inertial fusion for autonomous flight of rotorcraft MAVs]( https://ieeexplore.ieee.org/document/7139939),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), 2015, pp. 5303–5310. [Online]. Available: https://ieeexplore.ieee.org/document/7139939, doi: 10.1109/ICRA.2015.7139939. 
- Y. Liu, Z. Chen, W. Zheng, H. Wang, and J. Liu, “[Monocular visual- inertial SLAM: Continuous preintegration and reliable initialization]( https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5712814/),” Sensors, vol. 17, no. 11, p. 2613, Nov. 2017. [Online]. Available: https://www.mdpi.com/1424-8220/17/11/2613 
- Z. Yang and S. Shen, “[Monocular visual–inertial state estimation with online initialization and camera–IMU extrinsic calibration]( https://ieeexplore.ieee.org/document/7463059),” IEEE Trans. Autom. Sci. Eng., vol. 14, no. 1, pp. 39–51, Jan. 2017.
- T. Qin, P. Li, and S. Shen, “[VINS-mono: A robust and versatile monoc- ular visual-inertial state estimator]( https://arxiv.org/abs/1708.03852),” IEEE Trans. Robot., vol. 34, no. 4, pp. 1004–1020, Aug. 2018, doi: 10.1109/TRO.2018.2853729.
- P. Geneva, K. Eckenhoff, and G. Huang, “[A linear-complexity EKF for visual-inertial navigation with loop closures]( https://ieeexplore.ieee.org/document/8793836),” in Proc. Int. Conf. Robot. Automat. (ICRA), May 2019, pp. 3535–3541. 
- H. Rebecq, T. Horstschaefer, and D. Scaramuzza, “[Real-time visual- inertial odometry for event cameras using keyframe-based nonlinear optimization]( https://www.zora.uzh.ch/id/eprint/139471/1/BMVC17_Rebecq.pdf),” Tech. Rep., 2017.
- E. Mueggler, G. Gallego, H. Rebecq, and D. Scaramuzza, “[Continuous- time visual-inertial odometry for event cameras]( https://ieeexplore.ieee.org/abstract/document/8432102?casa_token=99UXUwtXu04AAAAA:o5Qob9hZJu9oLQpeBshuPkzr5-diQKscKGeTX2y5EWdtiFp3tb6GpkSbynjg-L5HfixcawFmfw),” IEEE Trans. Robot., vol. 34, no. 6, pp. 1425–1440, Dec. 2018. 

## C. RECENT VOI-BASED STUDIES <a name="partvio"/>
- A. I. Mourikis and S. I. Roumeliotis, “[A multi-state constraint Kalman filter for vision-aided inertial navigation]( https://ieeexplore.ieee.org/document/4209642),” in Proc. IEEE Int. Conf. Robot. Automat., Apr. 2007, pp. 3565–3572. 
- M. Bloesch, S. Omari, M. Hutter, and R. Siegwart, “[Robust visual inertial odometry using a direct EKF-based approach]( https://ieeexplore.ieee.org/document/7353389),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Sep. 2015, pp. 298–304.
- S. Leutenegger, S. Lynen, M. Bosse, R. Siegwart, and P. Furgale, “[Keyframe-based visual–inertial odometry using nonlinear optimization]( http://www.roboticsproceedings.org/rss09/p37.pdf),” Int. J. Robot. Res., vol. 34, no. 3, pp. 314–334, Mar. 2015, doi: 10.1177/0278364914554813. 
- V.Usenko,J.Engel,J.Stückler,andD.Cremers, “[Directvisual-inertial odometry with stereo cameras]( https://jakobengel.github.io/pdf/usenko16icra.pdf),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2016, pp. 1885–1892. 
- M. Burri, J. Nikolic, P. Gohl, T. Schneider, J. Rehder, S. Omari, M. W. Achtelik, and R. Siegwart, “[The EuRoC micro aerial vehicle datasets]( https://journals.sagepub.com/doi/abs/10.1177/0278364915620033),” Int. J. Robot. Res., vol. 35, no. 10, pp. 1157–1163, Sep. 2016. 
- C. Forster, L. Carlone, F. Dellaert, and D. Scaramuzza, “[On-manifold preintegration for real-time visual-inertial odometry]( http://rpg.ifi.uzh.ch/docs/TRO16_forster.pdf),” IEEE Trans. Robot., vol. 33, no. 1, pp. 1–21, Feb. 2017. 
- M.Schwaab,D.Plaia,D.Gaida,andY.Manoli, “[Tightlycoupledfusion of direct stereo visual odometry and inertial sensor measurements using an iterated information filter]( https://ieeexplore.ieee.org/document/8171505),” in Proc. DGON Inertial Sensors Syst. (ISS), 2017, pp. 1–20. 
- X. Zheng, Z. Moratto, M. Li, and A. I. Mourikis, “[Photometric patch- based visual-inertial odometry]( https://ieeexplore.ieee.org/document/7989372),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2017, pp. 3264–3271.
- M. Bloesch, M. Burri, S. Omari, M. Hutter, and R. Siegwart, “[Iterated extended Kalman filter based visual-inertial odometry using direct photometric feedback]( https://www.research-collection.ethz.ch/handle/20.500.11850/263423),” Int. J. Robot. Res., vol. 36, no. 10, pp. 1053–1072, 2017. [Online]. Available: https://journals.sagepub.com/ doi/abs/10.1177/0278364917728574, doi: 10.1177/0278364917728574. 
- D. Caruso, A. Eudes, M. Sanfourche, D. Vissière, and G. Le Besnerais, “[A robust indoor/outdoor navigation filter fusing data from vision and magneto-inertial measurement unit]( https://www.mdpi.com/1424-8220/17/12/2795),” Sensors, vol. 17, no. 12, p. 2795, Dec. 2017. [Online]. Available: https://www.mdpi.com/1424- 8220/17/12/2795 
- L. HaoChih and D. Francois, “[Loosely coupled stereo inertial odometry on low-cost system]( https://www.semanticscholar.org/paper/Loosely-Coupled-Stereo-Inertial-Odometry-on-System-HaoChih-Francois/2ad0adf9094d145d630356cf8664e5f442d2fc52),” Tech. Rep., 2017.
- Y. Ling, M. Kuse, and S. Shen, “[Edge alignment-based visual–inertial fusion for tracking of aggressive motions]( https://link.springer.com/article/10.1007/s10514-017-9642-0),” Auton. Robots, vol. 42, no. 3, pp. 513–528, Mar. 2018, doi: 10.1007/s10514-017-9642-0. 
- Y. He, J. Zhao, Y. Guo, W. He, and K. Yuan, “[PL-VIO: Tightly-coupled monocular visual–inertial odometry using point and line features]( https://www.mdpi.com/1424-8220/18/4/1159),” Sen- sors, vol. 18, no. 4, p. 1159, Apr. 2018.
- B. Pfrommer, N. Sanket, K. Daniilidis, and J. Cleveland, “[Pen- nCOSYVIO: A challenging visual inertial odometry benchmark]( https://daniilidis-group.github.io/penncosyvio/docs/penncosyvio.pdf),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2017, pp. 3847–3854. 
- T. Qin, P. Li, and S. Shen, “[VINS-mono: A robust and versatile monoc- ular visual-inertial state estimator]( https://arxiv.org/abs/1708.03852),” IEEE Trans. Robot., vol. 34, no. 4, pp. 1004–1020, Aug. 2018, doi: 10.1109/TRO.2018.2853729.
- R. Mur-Artal and J. D. Tardós, “[Visual-inertial monocular SLAM with map reuse]( https://ieeexplore.ieee.org/document/7817784),” IEEE Robot. Autom. Lett., vol. 2, no. 2, pp. 796–803, Apr. 2017. 
- J. Song, Z. Liu, X. Liu, and J. Guo, “[Tightly coupled visual inertial odometry based on artificial landmarks]( https://ieeexplore.ieee.org/document/8812447),” in Proc. IEEE Int. Conf. Inf. Automat. (ICIA), Aug. 2018, pp. 63–70.
- L. Von Stumberg, V. Usenko, and D. Cremers, “[Direct sparse visual- inertial odometry using dynamic marginalization]( https://arxiv.org/abs/1804.05625),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2018, pp. 2510–2517. 
- S. Khattak, C. Papachristos, and K. Alexis, “[Keyframe-based direct thermal–inertial odometry]( https://arxiv.org/abs/1903.00798),” in Proc. Int. Conf. Robot. Automat. (ICRA), May 2019, pp. 3563–3569.
- S. Ma, X. Bai, Y. Wang, and R. Fang, “[Robust stereo visual-inertial odometry using nonlinear optimization]( https://pubmed.ncbi.nlm.nih.gov/31470677/),” Sensors, vol. 19, no. 17, p. 3747, Aug. 2019. 
- Sun, K. Mohta, B. Pfrommer, M. Watterson, S. Liu, Y. Mulgaonkar, C. J. Taylor, and V. Kumar, “[Robust stereo visual inertial odometry for fast autonomous flight]( https://ieeexplore.ieee.org/document/8258858),” IEEE Robot. Autom. Lett., vol. 3, no. 2, pp. 965–972, Apr. 2018. 
- G.Yang,L.Zhao,J.Mao,andX.Liu, “[Optimization-based,simplified stereo visual-inertial odometry with high-accuracy initialization]( https://ieeexplore.ieee.org/document/8657357),” IEEE Access, vol. 7, pp. 39054–39068, 2019. 
- C.Chen,H.Zhu,L.Wang,andY.Liu, “[A stereo visual-inertialSLAM approach for indoor mobile robots in unknown environments without occlusions]( https://ieeexplore.ieee.org/document/8937551),” IEEE Access, vol. 7, pp. 185408–185421, 2019. 
- J. Jiang, J. Yuan, X. Zhang, and X. Zhang, “[DVIO: An optimization- based tightly coupled direct visual-inertial odometry]( https://ieeexplore.ieee.org/document/9257176),” IEEE Trans. Ind. Electron., early access, Nov. 16, 2020, doi: 10.1109/TIE.2020.3036243. 
- Z. Zhang, P. Dong, J. Wang, and Y. Sun, “[Improving S-MSCKF with variational Bayesian adaptive nonlinear filter]( https://ieeexplore.ieee.org/document/9076179),” IEEE Sensors J., vol. 20, no. 16, pp. 9437–9448, Aug. 2020. 
- D.Schubert,T.Goll,N.Demmel,V.Usenko,J.Stuckler,andD.Cremers, “[The TUM VI benchmark for evaluating visual-inertial odometry]( https://arxiv.org/abs/1804.06120),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Oct. 2018, pp. 1680–1687. 
- S.ZhongandP.Chirarattananon, “[An efficient iterated EKF-based direct visual-inertial odometry for MAVs using a single plane primitive]( https://ieeexplore.ieee.org/document/9309401),” IEEE Robot. Autom. Lett., vol. 6, no. 2, pp. 486–493, Apr. 2021. 
- S.Sun,G.Cioffi,C. deVisser, and D.Scaramuzza, “[Autonomous quadrotor flight despite rotor failure with onboard vision sensors: Frames vs. events]( https://ieeexplore.ieee.org/abstract/document/9312462?casa_token=Fh__lAmBqfgAAAAA:bD-6q29Cxgf06mcZxmHCG7lSUY013Yy6On72uOCR-wOYycBd8XBswgZK83vKhxVeIE8dz6d0bw),” IEEE Robot. Autom. Lett., vol. 6, no. 2, pp. 580–587, Apr. 2021. 



# LOCALIZATION TECHNIQUES IN LOW-VISIBILITY ENVIRONMENTS <a name="part10"/>
- T. Mouats, N. Aouf, L. Chermak, and M. A. Richardson, “[Thermal stereo odometry for UAVs]( https://ieeexplore.ieee.org/document/7156062),” IEEE Sensors J., vol. 15, no. 11, pp. 6335–6347, Nov. 2015. 
- K. Alexis, “[Resilient autonomous exploration and mapping of under- ground mines using aerial robots]( https://ieeexplore.ieee.org/abstract/document/8981545),” in Proc. 19th Int. Conf. Adv. Robot. (ICAR), Dec. 2019, pp. 1–8.
- C. Papachristos, S. Khattak, F. Mascarich, and K. Alexis, “[Autonomous navigation and mapping in underground mines using aerial robots]( https://ieeexplore.ieee.org/document/8741532),” in Proc. IEEE Aerosp. Conf., Mar. 2019, pp. 1–8.
- J. Delaune, R. Hewitt, L. Lytle, C. Sorice, R. Thakker, and L. Matthies, “[Thermal-inertial odometry for autonomous flight throughout the night]( https://ieeexplore.ieee.org/document/8968238),” in Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), Nov. 2019, pp. 1122–1128. 
- C.Papachristos,S.Khattak,andK.Alexis, “[Autonomous exploration of visually-degraded environments using aerial robots]( https://ieeexplore.ieee.org/document/7991510),” in Proc. Int. Conf. Unmanned Aircr. Syst. (ICUAS), Jun. 2017, pp. 775–780. 
- Y.-S.ShinandA.Kim, “[Sparse depth enhanced direct thermal-infrared SLAM beyond the visible spectrum]( https://ieeexplore.ieee.org/document/8737772),” IEEE Robot. Autom. Lett., vol. 4, no. 3, pp. 2918–2925, Jul. 2019. 
- A. Djuricic and B. Jutzi, “[Supporting UAVS in low visibility condi- tions by multiple-pulse laser scanning devices]( https://ui.adsabs.harvard.edu/abs/2013ISPAr.XL1a..93D/abstract),” ISPRS-Int. Arch. Pho- togramm., Remote Sens. Spatial Inf. Sci., vol. 1, pp. 93–98, Apr. 2013. 
- M. A. Hogervorst and A. Toet, “[Evaluation of a color fused dual-band NVG]( https://ieeexplore.ieee.org/abstract/document/5203791),” in Proc. 12th Int. Conf. Inf. Fusion, 2009, pp. 1432–1438.
- A. Toet, M. J. de Jong, M. A. Hogervorst, and I. T. Hooge, “[Perceptual evaluation of color transformed multispectral imagery]( https://www.spiedigitallibrary.org/journals/optical-engineering/volume-53/issue-4/043101/Perceptual-evaluation-of-color-transformed-multispectral-imagery/10.1117/1.OE.53.4.043101.short?SSO=1),” Opt. Eng., vol. 53, no. 4, pp. 1–13, 2014, doi: 10.1117/1.OE.53.4.043101.
- D. P. Bavirisetti and R. Dhuli, “[Two-scale image fusion of visible and infrared images using saliency detection]( http://www.sciencedirect. com/science/article/pii/S1350449515300955),” Infr. Phys. Technol., vol. 76, pp. 52–64, May 2016. [Online]. Available: http://www.sciencedirect. com/science/article/pii/S1350449515300955 
- D. P. Bavirisetti and R. Dhuli, “[Fusion of infrared and visible sensor images based on anisotropic diffusion and Karhunen–Loeve transform]( https://ieeexplore.ieee.org/document/7264981),” IEEE Sensors J., vol. 16, no. 1, pp. 203–209, Jan. 2016.
- H. Li, H. Qiu, Z. Yu, and Y. Zhang, “[Infrared and visible image fusion scheme based on NSCT and low-level visual features]( https://www.hindawi.com/journals/js/2018/5754702/),” Infr. Phys. Technol., vol. 76, pp. 174–184, May 2016. [Online]. Available: http://www.sciencedirect.com/science/article/pii/S1350449515301146 
- J. Ma, C. Chen, C. Li, and J. Huang, “[Infrared and visible image fusion via gradient transfer and total variation minimization]( https://www.sciencedirect.com/science/article/abs/pii/S156625351630001X),” Inf. Fusion, vol. 31, pp. 100–109, Sep. 2016. [Online]. Available: http://www.sciencedirect. com/science/article/pii/S156625351630001X 
- Z. Zhou, B. Wang, S. Li, and M. Dong, “[Perceptual fusion of infrared and visible images through a hybrid multi-scale decom- position with Gaussian and bilateral filters]( https://www.sciencedirect.com/science/article/abs/pii/S1566253515001013),” Inf. Fusion, vol. 30, pp. 15–26, Jul. 2016. [Online]. Available: http://www.sciencedirect. com/science/article/pii/S1566253515001013 
- T. Shibata, M. Tanaka, and M. Okutomi, “[Versatile visible and near- infrared image fusion based on high visibility area selection]( https://www.spiedigitallibrary.org/journals/journal-of-electronic-imaging/volume-25/issue-1/013016/Versatile-visible-and-near-infrared-image-fusion-based-on-high/10.1117/1.JEI.25.1.013016.short),” J. Electron. Imag., vol. 25, no. 1, pp. 1–16, 2016, doi: 10.1117/1.JEI.25.1.013016. 
- N.Bhat,N.Saggu,Pragati,andS.Kumar, “[Generatingvisiblespectrum images from thermal infrared using conditional generative adversarial networks]( https://ieeexplore.ieee.org/document/9137895),” in Proc. 5th Int. Conf. Commun. Electron. Syst. (ICCES), Jun. 2020, pp. 1390–1394.
- J. Ma, W. Yu, P. Liang, C. Li, and J. Jiang, “[FusionGAN: A gen- erative adversarial network for infrared and visible image fusion]( http://www.sciencedirect.com/science/article/pii/S1566253518301143),” Inf. Fusion, vol. 48, pp.11–26, Aug. 2019. [Online]. Available: http://www.sciencedirect.com/science/article/pii/S1566253518301143 
- H.LiandX.-J.Wu, “[DenseFuse:Afusionapproachtoinfraredandvisi- ble images]( https://ieeexplore.ieee.org/document/8580578),”  IEEE Trans. Image Process., vol. 28, no. 5, pp. 2614–2623, May 2019.
- N. Mandischer, S. C. Eddine, M. Huesing, and B. Corves, “[Bots2ReC: Radar localization in low visibility indoor environments]( https://ieeexplore.ieee.org/document/8848981),” in Proc. IEEE Int. Symp. Saf., Secur., Rescue Robot. (SSRR), Sep. 2019, pp. 158–163.
- R. Gomez-Ojeda, Z. Zhang, J. Gonzalez-Jimenez, and D. Scaramuzza, “[Learning-based image enhancement for visual odometry in challenging HDR environments]( https://arxiv.org/abs/1707.01274),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2018, pp. 805–811. 
- S. Park, T. Schops, and M. Pollefeys, “[Illumination change robustness in direct visual SLAM]( https://ieeexplore.ieee.org/document/7989525),” in Proc. IEEE Int. Conf. Robot. Automat. (ICRA), May 2017, pp. 4523–4530.
- P. Kim, H. Lee, and H. J. Kim, “[Autonomous flight with robust visual odometry under dynamic lighting conditions]( https://link.springer.com/article/10.1007/s10514-018-9816-4),” Auton. Robots, vol. 43, no. 6, pp. 1605–1622, Aug. 2019.
- M.Sizintsev,A.Rajvanshi,H.-P.Chiu,K.Kaighn,S.Samarasekera,and D. P. Snyder, “[Multi-sensor fusion for motion estimation in visually- degraded environments]( https://ieeexplore.ieee.org/document/8848958),” in Proc. IEEE Int. Symp. Saf., Secur., Rescue Robot. (SSRR), Sep. 2019, pp. 7–14. 
- A.R.Vidal,H.Rebecq,T.Horstschaefer,andD.Scaramuzza, “[Ultimate SLAM? Combining events, images, and IMU for robust visual SLAM in HDR and high-speed scenarios]( http://rpg.ifi.uzh.ch/ultimateslam.html),” IEEE Robot. Autom. Lett., vol. 3, no. 2, pp. 994–1001, Apr. 2018. 

# The MAIN COMPONENTS OF THE VISUAL-LOCALIZATION <a name="part11"/>

![MAINCOMPONENTSOFVISUAL-LOCALIZATION](https://user-images.githubusercontent.com/87903019/126872863-4c44cdad-1e6f-49f2-8571-11292f67671a.png)




  


