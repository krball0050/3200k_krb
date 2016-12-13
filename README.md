#This is my class repository for my python project
@author: kayla
"""

from mpl_toolkits.basemap import Basemap
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
##http://qingkaikong.blogspot.com/2016/06/nice-python-basemap-background.html
##http://server.arcgisonline.com/arcgis/rest/services
##EPSG Number for Eastern Georgia is 2239: 
##http://spatialreference.org/ref/epsg/?search=4269&srtext=Search
fig= plt.figure
mymap = Basemap(llcrnrlon=-84.109135,llcrnrlat=34.146535,urcrnrlon=-83.823032,urcrnrlat=34.381792, epsg=2239)
mymap.arcgisimage(service='ESRI_StreetMap_World_2D', xpixels = 4000, verbose= True)
# This section imports the sample sites from the csv 
samplesites = np.genfromtxt("coordinates.csv",
                         delimiter=',', 
                         dtype=[('lat', np.float32), ('lon', np.float32)], 
                         usecols=(0, 1))
x, y = mymap(samplesites['lon'], samplesites['lat'])
mymap.plot(x, y, 
            'o',color='#FF4000',markersize=8, label= "Sample Sites")   
#https://github.com/matplotlib/matplotlib/blob/master/lib/matplotlib/legend.py 
plt.legend(loc= 2, numpoints= 1)  
#drawmapscale takes atleast the location where you want the scalebar, the location it is measuring, and the length of the scalebar
#    default length is km
mymap.drawmapscale( -83.872787, 34.167158,-83.768442, 34.195325,5, barstyle= 'fancy', units="mi")

plt.title('Lake Lanier Chlorophyll-a Monitoring', fontsize= 16, weight= 'bold')
plt.savefig('c:/Users/kayla/Desktop/pythonproject/nolabels.tif')
plt.clf()
![nolabels](https://cloud.githubusercontent.com/assets/22508936/21123069/6790c0e0-c0a4-11e6-8c26-0845eb86b17a.png)


#html color cordes
# http://html-color-codes.info/color-names/
#Line and Marker Styles:
#    http://matplotlib.org/1.5.3/api/pyplot_api.html#matplotlib.pyplot.plot
#Pandas and Dataframe:
#    http://pandas.pydata.org/pandas-docs/version/0.18.1/generated/pandas.DataFrame.plot.html

#2013 Growing Standard Comparison
data = np.genfromtxt("2013standard.csv", delimiter=',', dtype = float)
df= pd.DataFrame.from_csv("2013standard.csv", parse_dates=False)
df.Lanier_Bridge.plot(marker= "o",color="r", lw= 3)
df.Growing_Season_Results.plot(style=":",marker= "o",color="#000000", lw= 4)
plt.xticks(rotation=80)
plt.xlabel("Monitoring Sites",fontweight="bold")
plt.ylabel("ug/L", fontweight="bold")
plt.grid()
lgd=plt.legend(loc='center left', bbox_to_anchor=(1.0, 0.5))
plt.title("2013 Growing Standard Comparison", fontsize=14, fontweight="bold")
plt.savefig('c:/Users/kayla/Desktop/pythonproject/2013standard.tif',
            bbox_extra_artists=(lgd,), bbox_inches='tight')

#2014 Monthly Levels
data = np.genfromtxt("2014llmmonthly.csv", delimiter=',', dtype = float)
df= pd.DataFrame.from_csv("2014llmmonthly.csv", parse_dates=False)
df.April.plot(marker= "o",color="r", lw= 3)
df.May.plot(style= "",marker= "o",color="#FFA500", lw= 3)
df.June.plot(style= "-.",marker= "o",color="g", lw= 3)
df.July.plot( marker= "o",color="b", lw= 3)
df.August.plot(marker= "o",color="#800080", lw= 3)
df.September.plot(style= "-.",marker= "o", color="#8B4513", lw= 3)
df.October.plot(style=":",marker= "o",color="#000000", lw= 4)
plt.xticks(rotation=80)
plt.xlabel("Monitoring Sites",fontweight="bold")
plt.ylabel("ug/L", fontweight="bold")
plt.grid()
lgd=plt.legend(loc='center left', bbox_to_anchor=(1.0, 0.5))
plt.title("2014 Monthly Chlorophyll-a Levels", fontsize=14, fontweight="bold")
plt.savefig('c:/Users/kayla/Desktop/pythonproject/2014monthly.tif',
            bbox_extra_artists=(lgd,), bbox_inches='tight')
plt.clf()

#2015 Monthly Levels
data = np.genfromtxt("2015llmmonthly.csv", delimiter=',', dtype = float)
df= pd.DataFrame.from_csv("2015llmmonthly.csv", parse_dates=False)
df.April.plot(marker= "o",color="r", lw= 3)
df.May.plot(style= "",marker= "o",color="#FFA500", lw= 3)
df.June.plot(style= "-.",marker= "o",color="g", lw= 3)
df.July.plot( marker= "o",color="b", lw= 3)
df.August.plot(marker= "o",color="#800080", lw= 3)
df.September.plot(style= "-.",marker= "o", color="#8B4513", lw= 3)
df.October.plot(style=":",marker= "o",color="#000000", lw= 4)
plt.xticks(rotation=80)
plt.xlabel("Monitoring Sites",fontweight="bold")
plt.ylabel("ug/L", fontweight="bold")
plt.grid()
lgd=plt.legend(loc='center left', bbox_to_anchor=(1.0, 0.5))
plt.title("2015 Monthly Chlorophyll-a Levels", fontsize=14, fontweight="bold")
#This makes sure that the image saved includes the entire plot components and not just the graph
plt.savefig('c:/Users/kayla/Desktop/pythonproject/2015monthly.tif',bbox_extra_artists=(lgd,), bbox_inches='tight')
plt.clf()

# Yearly Averages
data = np.genfromtxt("years.csv", delimiter=',', dtype = float)
df= pd.DataFrame.from_csv("years.csv", parse_dates=False)
df.Year_2010.plot(marker= "o",color="r", lw= 3)
df.Year_2011.plot(style= "",marker= "o",color="#FFA500", lw= 3)
df.Year_2012.plot(style= "-.",marker= "o",color="g", lw= 3)
df.Year_2013.plot( marker= "o",color="b", lw= 3)
df.Year_2014.plot(marker= "o",color="#800080", lw= 3)
df.Year_2015.plot(style= "-.",marker= "o", color="#8B4513", lw= 3)
df.Year_2016.plot(style=":",marker= "o",color="#000000", lw= 4)
plt.xticks(rotation=80)
plt.xlabel("Monitoring Sites",fontweight="bold")
plt.ylabel("ug/L", fontweight="bold")
plt.grid()
lgd=plt.legend(loc='center left', bbox_to_anchor=(1.0, 0.5))
plt.title("2010-2016 Average Chlorophyll-a Levels", fontsize=14, 
          fontweight="bold")
plt.savefig('c:/Users/kayla/Desktop/pythonproject/years.tif',
            bbox_extra_artists=(lgd,), bbox_inches='tight')
plt.clf()

#Little River Embayment
##http://qingkaikong.blogspot.com/2016/06/nice-python-basemap-background.html
##http://server.arcgisonline.com/arcgis/rest/services
##EPSG Number for Eastern Georgia is 2239: 
##http://spatialreference.org/ref/epsg/?search=4269&srtext=Search
fig= plt.figure
mymap = Basemap(llcrnrlon=-84.109135,llcrnrlat=34.146535,urcrnrlon=-83.823032,urcrnrlat=34.381792, epsg=2239)
##http://qingkaikong.blogspot.com/2016/06/nice-python-basemap-background.html
##http://server.arcgisonline.com/arcgis/rest/services
##EPSG Number for Eastern Georgia is 2239: 
##http://spatialreference.org/ref/epsg/?search=4269&srtext=Search
mymap.arcgisimage(service='ESRI_StreetMap_World_2D', xpixels = 4000, verbose= True)
# This section imports the sample sites from the csv 
samplesites = np.genfromtxt("coordinates.csv",
                         delimiter=',', 
                         dtype=[('lat', np.float32), ('lon', np.float32)], 
                         usecols=(0, 1))
x, y = mymap(samplesites['lon'], samplesites['lat'])
mymap.plot(x, y, 
            'o',color='#FF4000',markersize=8, label= "Sample Sites")   
#https://github.com/matplotlib/matplotlib/blob/master/lib/matplotlib/legend.py 
plt.legend(loc= 2, numpoints= 1)  
#drawmapscale takes atleast the location where you want the scalebar, the location it is measuring, and the length of the scalebar
#    default length is km
mymap.drawmapscale( -83.872787, 34.167158,-83.768442, 34.195325,5, barstyle= 'fancy', units="mi")
##https://github.com/matplotlib/matplotlib/blob/master/lib/matplotlib/legend.py 
plt.legend(loc= 2, numpoints= 1)  
#drawmapscale takes atleast the location where you want the scalebar, the location it is measuring, and the length of the scalebar
#    default length is km
mymap.drawmapscale( -83.872787, 34.167158,-83.768442, 34.195325,5, barstyle= 'fancy', units="mi")
plt.title('Lake Lanier Chlorophyll-a Monitoring', fontsize= 16, weight= 'bold')
####http://basemaptutorial.readthedocs.io/en/latest/locator.html
littleriverlat= 34.3537
littleriverlon= -83.8415
x10,y10 = mymap(littleriverlon, littleriverlat)     
plt.annotate('Little River',xy=(x10,y10),fontsize=8, textcoords= 'data')
plt.savefig('c:/Users/kayla/Desktop/pythonproject/littleriverlabel.tif')
plt.clf()

#Little River Embayment
data = np.genfromtxt("LittleRiverEmbayment.csv", delimiter=',', dtype = float)
df= pd.DataFrame.from_csv("LittleRiverEmbayment.csv", parse_dates=False)
df.Chlorophyll.plot(marker= "o",color="r", lw= 3)
plt.xticks(rotation=80)
plt.xlabel("Years",fontweight="bold")
plt.ylabel("ug/L", fontweight="bold")
plt.grid()
lgd=plt.legend(loc='center left', bbox_to_anchor=(1.0, 0.5))
plt.title("Little River Embayment", fontsize=14, fontweight="bold")
littleriverlon= -83.8415
x10,y10 = mymap(littleriverlon, littleriverlat)     
plt.annotate('Little River',xy=(x10,y10),fontsize=8, textcoords= 'data')
plt.savefig('c:/Users/kayla/Desktop/pythonproject/littleriverembayment2.tif',
            bbox_extra_artists=(lgd,), bbox_inches='tight')


#Map with Labels
#
#fig= plt.figure
#
#mymap = Basemap(llcrnrlon=-84.109135,llcrnrlat=34.146535,urcrnrlon=-83.823032,urcrnrlat=34.381792, epsg=2239)
###http://qingkaikong.blogspot.com/2016/06/nice-python-basemap-background.html
###http://server.arcgisonline.com/arcgis/rest/services
###EPSG Number for Eastern Georgia is 2239: 
###http://spatialreference.org/ref/epsg/?search=4269&srtext=Search
#mymap.arcgisimage(service='ESRI_StreetMap_World_2D', xpixels = 4000, verbose= True)
## This section imports the sample sites from the csv 
#samplesites = np.genfromtxt("coordinates.csv",
#                         delimiter=',', 
#                         dtype=[('lat', np.float32), ('lon', np.float32)], 
#                         usecols=(0, 1))
#x, y = mymap(samplesites['lon'], samplesites['lat'])
#mymap.plot(x, y, 
#            'o',color='#FF4000',markersize=8, label= "Sample Sites")   
##https://github.com/matplotlib/matplotlib/blob/master/lib/matplotlib/legend.py 
#plt.legend(loc= 2, numpoints= 1)  
##drawmapscale takes atleast the location where you want the scalebar, the location it is measuring, and the length of the scalebar
##    default length is km
#mymap.drawmapscale( -83.872787, 34.167158,-83.768442, 34.195325,5, barstyle= 'fancy', units="mi")
#
#plt.title('Lake Lanier Chlorophyll-a Monitoring', fontsize= 16, weight= 'bold')
#####annotate
#####https://github.com/BillMills/python-mapping
#dampoollat= 34.1642
#dampoollon= -84.0707
#x2,y2 = mymap(dampoollon, dampoollat)     
#plt.annotate('Dam Pool',xy=(x2,y2),fontsize=8, textcoords= 'data')
#
#midlakelat= 34.2009
#midlakelon= -83.9848
#x3,y3 = mymap(midlakelon, midlakelat)     
#plt.annotate('Mid Lake',xy=(x3,y3),fontsize=8, textcoords= 'data')
#
#BrownsBridgelat= 34.2619
#BrownsBridgelon= -83.9503
#x4,y4 = mymap(BrownsBridgelon, BrownsBridgelat)     
#plt.annotate('Browns Bridge',xy=(x4,y4),fontsize=8, textcoords= 'data')
#
#LanierBridgelat= 34.3227
#LanierBridgelon= -83.8799
#x5,y5 = mymap(LanierBridgelon, LanierBridgelat)     
#plt.annotate('Lanier Bridge',xy=(x5,y5),fontsize=8, textcoords= 'data')
##
#BolingBridgelat= 34.3125
#BolingBridgelon= -83.9500
#x6,y6 = mymap(BolingBridgelon, BolingBridgelat)     
#plt.annotate('Boling Bridge',xy=(x6,y6),fontsize=8, textcoords= 'data',
# horizontalalignment='left')
#
#flatcreeklat= 34.2616
#flatcreeklon= -83.9164
#x7,y7 = mymap(flatcreeklon, flatcreeklat)     
#plt.annotate('Flat Creek',xy=(x7,y7),fontsize=8, textcoords= 'data')
#
#baluscreeklat= 34.2508
#baluscreeklon= -83.9250
#x8,y8 = mymap(baluscreeklon, baluscreeklat)     
#plt.annotate('Balus Creek',xy=(x8,y8),fontsize=8, textcoords= 'data')
#
#mudcreeklat= 34.2304
#mudcreeklon= -83.9269
#x9,y9 = mymap(mudcreeklon, mudcreeklat)     
#plt.annotate('Mud Creek',xy=(x9,y9),fontsize=8, textcoords= 'data')
#
#littleriverlat= 34.3537
#littleriverlon= -83.8415
#x10,y10 = mymap(littleriverlon, littleriverlat)     
#plt.annotate('Little River',xy=(x10,y10),fontsize=8, textcoords= 'data')
#
#sixmilelat= 34.2337
#sixmilelon= -84.0276
#x11,y11 = mymap(sixmilelon, sixmilelat)     
#plt.annotate('Six Mile',xy=(x11,y11),fontsize=8, textcoords= 'data')
#
#plt.savefig('c:/Users/kayla/Desktop/pythonproject/labels.tif')
#plt.clf()
