# Digital Image Fundamentals

### Elements of Visual Perception
Although the field of digital image processing is built on a foundation of mathematics, human intuition and analysis often play a role in the choice of one technique versus another, and this choice often is made based on subjective, visual judgments. Thus, developing an understanding of basic characteristics of human visual perception as a first step in our journey through this book is appropriate. In particular, our interest is in the elementary mechanics of how images are formed and perceived by humans. We are interested in learning the physical limitations of human vision in terms of factors that also are used in our work with digital images. Factors such as how human and electronic imaging devices compare in terms of resolution and ability to adapt to changes in illumination are not only interesting, they are also important from a practical point of view.

### Structure of the Human Eye
The eye is nearly a sphere (with a diameter of about 20 mm) enclosed by three membranes: the cornea and sclera outer cover; the choroid; and the retina.

The cornea is a tough, transparent tissue that covers the anterior surface of the eye. Continuous with the cornea, the sclera is an opaque membrane that encloses the remainder of the optic globe.

![](https://cdn.discordapp.com/attachments/845561994022879264/889458424801275955/unknown.png)

### IMAGE FORMATION IN THE EYE
In an ordinary photographic camera, the lens has a fixed focal length. Focusing at various distances is achieved by varying the distance between the lens and the imaging plane, where the film (or imaging chip in the case of a digital camera) is located. In the human eye, the converse is true; the distance between the center of the lens and the imaging sensor (the retina) is fixed, and the focal length needed to achieve proper focus is obtained by varying the shape of the lens. The fibers in the ciliary body accomplish this by flattening or thickening the lens for distant or near objects, respectively. The distance between the center of the lens and the retina along the visual axis is approximately 17 mm. The range of focal lengths is approximately 14 mm to 17 mm, the latter taking place when the eye is relaxed and focused at distances greater than about 3 m. The geometry in Fig. 2.3 illustrates how to obtain the dimensions of an image formed on the retina. For example, suppose that a person is looking at a tree 15 m high at a distance of 100 m. Letting h denote the height of that object in the retinal image, the geometry of Fig. 2.3 yields 15 100 17 = h or h = 2 5. mm. As indicated earlier in this section, the retinal image is focused primarily on the region of the fovea. Perception then takes place by the relative excitation of light receptors, which transform radiant energy into electrical impulses that ultimately are decoded by the brain.

### BRIGHTNESS ADAPTATION AND DISCRIMINATION 
![](https://cdn.discordapp.com/attachments/845561994022879264/889459953801261096/unknown.png)

### Light and the Electromagnetic Spectrum
The electromagnetic spectrum can be expressed in terms of wavelength, frequency, or energy. Wavelength (l) and frequency (n) are related by the expression 

![](https://cdn.discordapp.com/attachments/845561994022879264/889464964530724864/unknown.png)

where c is the speed of light (2 998 108 . * m/s).

The energy of the various components of the electromagnetic spectrum is given by the expression
![](https://cdn.discordapp.com/attachments/845561994022879264/889465259520294912/unknown.png)

where h is Planck’s constant. The units of wavelength are meters, with the terms microns (denoted mm and equal to 10−6 m) and nanometers (denoted nm and equal to 10−9 m) being used just as frequently. Frequency is measured in Hertz (Hz), with one Hz being equal to one cycle of a sinusoidal wave per second. A commonly used unit of energy is the electron-volt.

##### Monochromatic Light
Light that is void of color is called monochromatic (or achromatic) light. The only attribute of monochromatic light is its intensity. Because the intensity of monochromatic light is perceived to vary from black to grays and finally to white, the term gray level is used commonly to denote monochromatic intensity. The range of values of monochromatic light from black to white is usually called the gray scale, and monochromatic images are frequently referred to as grayscale images.

##### Chromatic Light
Chromatic (color) light spans the electromagnetic energy spectrum from approximately 0.43 to 0.79 mm, as noted previously. In addition to frequency, three other quantities are used to describe a chromatic light source: radiance, luminance, and brightness. 
 Luminance, measured in lumens (lm), gives a measure of the amount of energy an observer perceives from a light source. For example, light emitted from a source operating in the far infrared region of the spectrum could have significant energy (radiance), but an observer would hardly perceive it; its luminance would be almost zero. Finally, as discussed in Section 2.1, brightness is a subjective descriptor of light perception that is practically impossible to measure. It embodies the achromatic notion of intensity and is one of the key factors in describing color sensation.

##### A Simple Image Formation Model
An example of digital image acquisition. (a) Illumination (energy) source. (b) A scene. (c) Imaging system. (d) Projection of the scene onto the image plane. (e) Digitized image.

![](https://cdn.discordapp.com/attachments/845561994022879264/889576044816916530/unknown.png)

Function f xy ( , ) is characterized by two components: (1) the amount of source illumination incident on the scene being viewed, and (2) the amount of illumination reflected by the objects in the scene. Appropriately, these are called the illumination and reflectance components, and are denoted by ixy ( , ) and rxy ( , ), respectively. The two functions combine as a product to form f xy ( , ):

![](https://cdn.discordapp.com/attachments/845561994022879264/889576519909928990/unknown.png)

Thus, reflectance is bounded by 0 (total absorption) and 1 (total reflectance). The nature of ixy ( , ) is determined by the illumination source, and r(x , y)  is determined by the characteristics of the imaged objects. 

#### REPRESENTING DIGITAL IMAGES
![](https://cdn.discordapp.com/attachments/845561994022879264/889585392989384724/unknown.png)
![](https://cdn.discordapp.com/attachments/845561994022879264/889585454607892530/unknown.png)