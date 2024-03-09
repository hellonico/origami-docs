# Original
![](original.png)
# NoOP
*Load with:*
```
{:class origami.Filters$NoOP}
```
*Result:*

![](NoOP.png)
# Annotate
*Load with:*
```
{:class origami.filters.Annotate, :color "255.0,255.0,255.0,0.0", :fontSize 3.0, :point "50.0,50.0", :text "hello", :thickness 3}
```
*Result:*

![](Annotate.png)
# BackgroundSubstractor
*Load with:*
```
{:class origami.filters.BackgroundSubstractor}
```
*Result:*

![](BackgroundSubstractor.png)
# BitwiseRed
*Load with:*
```
{:class origami.filters.BitwiseRed}
```
*Result:*

![](BitwiseRed.png)
# Canny
*Load with:*
```
{:class origami.filters.Canny, :inverted true, :threshold1 100, :threshold2 200}
```
*Result:*

![](Canny.png)
# ClojureFilter
*Load with:*
```
{:class origami.filters.ClojureFilter, :fn "(fn[mat] mat)"}
```
*Result:*

![](ClojureFilter.png)
# ColorFilter
*Load with:*
```
{:class origami.filters.ColorFilter, :high 20, :low 0}
```
*Result:*

![](ColorFilter.png)
# Blue
*Load with:*
```
{:class origami.filters.ColorFilter$Blue, :high 240, :low 200}
```
*Result:*

![](Blue.png)
# Pink
*Load with:*
```
{:class origami.filters.ColorFilter$Pink, :high 320, :low 300}
```
*Result:*

![](Pink.png)
# Red
*Load with:*
```
{:class origami.filters.ColorFilter$Red, :high 20, :low 0}
```
*Result:*

![](Red.png)
# ColorMap
*Load with:*
```
{:class origami.filters.ColorMap}
```
*Result:*

![](ColorMap.png)
# Autumn
*Load with:*
```
{:class origami.filters.ColorMap$Autumn}
```
*Result:*

![](Autumn.png)
# Bone
*Load with:*
```
{:class origami.filters.ColorMap$Bone}
```
*Result:*

![](Bone.png)
# Cividis
*Load with:*
```
{:class origami.filters.ColorMap$Cividis}
```
*Result:*

![](Cividis.png)
# Cool
*Load with:*
```
{:class origami.filters.ColorMap$Cool}
```
*Result:*

![](Cool.png)
# HSV
*Load with:*
```
{:class origami.filters.ColorMap$HSV}
```
*Result:*

![](HSV.png)
# Hot
*Load with:*
```
{:class origami.filters.ColorMap$Hot}
```
*Result:*

![](Hot.png)
# Jet
*Load with:*
```
{:class origami.filters.ColorMap$Jet}
```
*Result:*

![](Jet.png)
# Magma
*Load with:*
```
{:class origami.filters.ColorMap$Magma}
```
*Result:*

![](Magma.png)
# Ocean
*Load with:*
```
{:class origami.filters.ColorMap$Ocean}
```
*Result:*

![](Ocean.png)
# Parula
*Load with:*
```
{:class origami.filters.ColorMap$Parula}
```
*Result:*

![](Parula.png)
# Pink
*Load with:*
```
{:class origami.filters.ColorMap$Pink}
```
*Result:*

![](Pink.png)
# Rainbow
*Load with:*
```
{:class origami.filters.ColorMap$Rainbow}
```
*Result:*

![](Rainbow.png)
# Spring
*Load with:*
```
{:class origami.filters.ColorMap$Spring}
```
*Result:*

![](Spring.png)
# Summer
*Load with:*
```
{:class origami.filters.ColorMap$Summer}
```
*Result:*

![](Summer.png)
# Turbo
*Load with:*
```
{:class origami.filters.ColorMap$Turbo}
```
*Result:*

![](Turbo.png)
# Twilight
*Load with:*
```
{:class origami.filters.ColorMap$Twilight}
```
*Result:*

![](Twilight.png)
# TwilightShifted
*Load with:*
```
{:class origami.filters.ColorMap$TwilightShifted}
```
*Result:*

![](TwilightShifted.png)
# Viridis
*Load with:*
```
{:class origami.filters.ColorMap$Viridis}
```
*Result:*

![](Viridis.png)
# Winter
*Load with:*
```
{:class origami.filters.ColorMap$Winter}
```
*Result:*

![](Winter.png)
# Contours
*Load with:*
```
{:class origami.filters.Contours, :color "256.0,150.0,0.0,0.0", :linetype 8, :offset "0.0,0.0", :thickness 2, :threshold 100}
```
*Result:*

![](Contours.png)
# CoolCanny
*Load with:*
```
{:class origami.filters.CoolCanny, :inverted false}
```
*Result:*

![](CoolCanny.png)
# Decolor
*Load with:*
```
{:class origami.filters.Decolor, :gray true}
```
*Result:*

![](Decolor.png)
# DetailEnhance
*Load with:*
```
{:class origami.filters.DetailEnhance, :sigma_r 0.15, :sigma_s 10.0}
```
*Result:*

![](DetailEnhance.png)
# DynamicAnnotate
*Load with:*
```
{:class origami.filters.DynamicAnnotate, :color "255.0,255.0,255.0,0.0", :fontSize 3.0, :point "50.0,50.0", :text "(str (java.util.Date.))", :thickness 3}
```
*Result:*

![](DynamicAnnotate.png)
# EdgePreserving
*Load with:*
```
{:class origami.filters.EdgePreserving, :flags 1, :sigma_r 0.4, :sigma_s 60.0}
```
*Result:*

![](EdgePreserving.png)
# FPS
*Load with:*
```
{:class origami.filters.FPS}
```
*Result:*

![](FPS.png)
# FastDenoising
*Load with:*
```
{:class origami.filters.FastDenoising}
```
*Result:*

![](FastDenoising.png)
# Fisheye
*Load with:*
```
{:cX 300.0, :cY 540.0, :class origami.filters.Fisheye, :fishVal 600.0}
```
*Result:*

![](Fisheye.png)
# Gray
*Load with:*
```
{:class origami.filters.Gray}
```
*Result:*

![](Gray.png)
# Grayscale
*Load with:*
```
{:class origami.filters.Grayscale}
```
*Result:*

![](Grayscale.png)
# GreenLantern
*Load with:*
```
{:class origami.filters.GreenLantern}
```
*Result:*

![](GreenLantern.png)
# HOG
*Load with:*
```
{:class origami.filters.HOG}
```
*Result:*

![](HOG.png)
# HttpGet
*Load with:*
```
{:class origami.filters.HttpGet, :interval -1, :url nil}
```
*Result:*

![](HttpGet.png)
# Gotham
*Load with:*
```
{:class origami.filters.HueSaturationValue$Gotham}
```
*Result:*

![](Gotham.png)
# Lomo
*Load with:*
```
{:class origami.filters.HueSaturationValue$Lomo}
```
*Result:*

![](Lomo.png)
# Nashville
*Load with:*
```
{:class origami.filters.HueSaturationValue$Nashville}
```
*Result:*

![](Nashville.png)
# Pink
*Load with:*
```
{:class origami.filters.HueSaturationValue$Pink}
```
*Result:*

![](Pink.png)
# Illumination
*Load with:*
```
{:alpha 3.0, :beta 0.4, :class origami.filters.Illumination}
```
*Result:*

![](Illumination.png)
# Level
*Load with:*
```
{:class origami.filters.Level, :n 100}
```
*Result:*

![](Level.png)
# Mosaic
*Load with:*
```
{:class origami.filters.Mosaic}
```
*Result:*

![](Mosaic.png)
# NoOPFilter
*Load with:*
```
{:class origami.filters.NoOPFilter}
```
*Result:*

![](NoOPFilter.png)
# PencilSketch
*Load with:*
```
{:class origami.filters.PencilSketch}
```
*Result:*

![](PencilSketch.png)
# Resize
*Load with:*
```
{:class origami.filters.Resize, :factor -1.0, :height -1.0, :width -1.0}
```
*Result:*

![](Resize.png)
# Rotate180
*Load with:*
```
{:class origami.filters.Rotate$Rotate180, :rotateAngle 1}
```
*Result:*

![](Rotate180.png)
# Rotate270
*Load with:*
```
{:class origami.filters.Rotate$Rotate270, :rotateAngle 2}
```
*Result:*

![](Rotate270.png)
# Rotate90
*Load with:*
```
{:class origami.filters.Rotate$Rotate90, :rotateAngle 0}
```
*Result:*

![](Rotate90.png)
# Stilyze
*Load with:*
```
{:class origami.filters.Stilyze, :sigma_r 0.07, :sigma_s 60.0}
```
*Result:*

![](Stilyze.png)
# Thresh
*Load with:*
```
{:class origami.filters.Thresh}
```
*Result:*

![](Thresh.png)
# Zoom
*Load with:*
```
{:class origami.filters.Zoom}
```
*Result:*

![](Zoom.png)
# Cartoon
*Load with:*
```
{:blockSize 9, :c 2, :class origami.filters.cartoon.Cartoon, :d 13, :ksize 7, :maxValue 255.0, :sigmaColor 13, :sigmaSpace 7}
```
*Result:*

![](Cartoon.png)
# Cartoon2
*Load with:*
```
{:class origami.filters.cartoon.Cartoon2}
```
*Result:*

![](Cartoon2.png)
# LUTCartoon
*Load with:*
```
{:class origami.filters.cartoon.LUTCartoon}
```
*Result:*

![](LUTCartoon.png)
# Manga
*Load with:*
```
{:class origami.filters.cartoon.Manga}
```
*Result:*

![](Manga.png)
# Haar
*Load with:*
```
{:class origami.filters.detect.Haar, :color "255.0,255.0,255.0,0.0", :text "Gatos", :type "haar.frontalcatface"}
```
*Result:*

![](Haar.png)
# EnhanceImageBrightness
*Load with:*
```
{:alpha 2.0, :beta 50.0, :class origami.filters.dip.EnhanceImageBrightness}
```
*Result:*

![](EnhanceImageBrightness.png)
# EnhanceImageContrast
*Load with:*
```
{:class origami.filters.dip.EnhanceImageContrast}
```
*Result:*

![](EnhanceImageContrast.png)
# EnhanceImageSharpness
*Load with:*
```
{:class origami.filters.dip.EnhanceImageSharpness}
```
*Result:*

![](EnhanceImageSharpness.png)
# ErodingDilating
*Load with:*
```
{:class origami.filters.dip.ErodingDilating}
```
*Result:*

![](ErodingDilating.png)
# GaussianFilter
*Load with:*
```
{:class origami.filters.dip.GaussianFilter, :sigmaX 0, :size "11.0,11.0"}
```
*Result:*

![](GaussianFilter.png)
# GlyphDetector
*Load with:*
```
{:chosenGlyphOffset 0.0, :chosenGlyphPosition nil, :class origami.filters.doge.GlyphDetector, :foundRect true, :frameSize #object[org.opencv.core.Size 0x2b235a1c "307x231"]}
```
*Result:*

![](GlyphDetector.png)
# LeviColorFilter
*Load with:*
```
{:class origami.filters.doge.LeviColorFilter, :color "RED", :threshold 164.0}
```
*Result:*

![](LeviColorFilter.png)
# Gray
*Load with:*
```
{:class origami.filters.instagram.Sepia$Gray}
```
*Result:*

![](Gray.png)
# Red
*Load with:*
```
{:class origami.filters.instagram.Sepia$Red}
```
*Result:*

![](Red.png)
# Blue
*Load with:*
```
{:alpha 0.8, :beta 0.2, :class origami.filters.instagram.SunGlasses$Blue, :color "255.0,0.0,0.0,0.0", :gamma 0.0}
```
*Result:*

![](Blue.png)
# Green
*Load with:*
```
{:alpha 0.8, :beta 0.2, :class origami.filters.instagram.SunGlasses$Green, :color "0.0,255.0,0.0,0.0", :gamma 0.0}
```
*Result:*

![](Green.png)
# Purple
*Load with:*
```
{:alpha 0.8, :beta 0.2, :class origami.filters.instagram.SunGlasses$Purple, :color "128.0,0.0,128.0,0.0", :gamma 0.0}
```
*Result:*

![](Purple.png)
# Red
*Load with:*
```
{:alpha 0.8, :beta 0.2, :class origami.filters.instagram.SunGlasses$Red, :color "0.0,0.0,255.0,0.0", :gamma 0.0}
```
*Result:*

![](Red.png)
# Salmon
*Load with:*
```
{:alpha 0.8, :beta 0.2, :class origami.filters.instagram.SunGlasses$Salmon, :color "114.0,128.0,250.0,0.0", :gamma 0.0}
```
*Result:*

![](Salmon.png)
# Turquoise
*Load with:*
```
{:alpha 0.8, :beta 0.2, :class origami.filters.instagram.SunGlasses$Turquoise, :color "208.0,224.0,64.0,0.0", :gamma 0.0}
```
*Result:*

![](Turquoise.png)
# Yellow
*Load with:*
```
{:alpha 0.8, :beta 0.2, :class origami.filters.instagram.SunGlasses$Yellow, :color "0.0,255.0,255.0,0.0", :gamma 0.0}
```
*Result:*

![](Yellow.png)
# Vintage
*Load with:*
```
{:class origami.filters.instagram.Vintage}
```
*Result:*

![](Vintage.png)
# ALTMRetinex
*Load with:*
```
{:class origami.filters.isaac.ALTMRetinex}
```
*Result:*

![](ALTMRetinex.png)
# DarkChannelPriorDehaze
*Load with:*
```
{:class origami.filters.isaac.DarkChannelPriorDehaze}
```
*Result:*

![](DarkChannelPriorDehaze.png)
# FusionEnhance
*Load with:*
```
{:class origami.filters.isaac.FusionEnhance}
```
*Result:*

![](FusionEnhance.png)
# OptimizeContrastEnhance
*Load with:*
```
{:class origami.filters.isaac.OptimizeContrastEnhance}
```
*Result:*

![](OptimizeContrastEnhance.png)
# RemoveBlackScatter
*Load with:*
```
{:class origami.filters.isaac.RemoveBlackScatter}
```
*Result:*

![](RemoveBlackScatter.png)
# ChannelGains
*Load with:*
```
{:blue 1.0, :class origami.filters.xphoto.ChannelGains, :green 1.0, :red 1.0}
```
*Result:*

![](ChannelGains.png)
# DtcDenoising
*Load with:*
```
{:class origami.filters.xphoto.DtcDenoising, :psize 6, :sigma 21.0}
```
*Result:*

![](DtcDenoising.png)
# GrayWorldWB
*Load with:*
```
{:class origami.filters.xphoto.GrayWorldWB, :saturationThreshold 0.9}
```
*Result:*

![](GrayWorldWB.png)
# OilPainting
*Load with:*
```
{:class origami.filters.xphoto.OilPainting, :code 45, :ratio 1, :size 10}
```
*Result:*

![](OilPainting.png)
# SimpleWB
*Load with:*
```
{:class origami.filters.xphoto.SimpleWB, :inputMax 255.0, :inputMin 0.0, :outputMax 255.0, :outputMin 0.0, :p 1.0}
```
*Result:*

![](SimpleWB.png)
