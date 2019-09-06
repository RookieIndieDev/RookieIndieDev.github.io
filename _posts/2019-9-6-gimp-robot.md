Today I decided I wanted to mess around with some ML. I wanted to try and make an image classifier for this game character from the game Don't Starve Together, maybe for future use with a RL agent. (That isn't the focus of this post though)
So I recorded myself playing the game for maybe 30 minutes. I converted all the frames of the video into single images. The total images is 8162 images (Some 15.4 GB!). Now there is no way I am going to sit around crop out of the character 
I want to create my dataset for training. So I decided to have a G1ANT Robot do that for me! 


Here's the G1ANT Script file for my robot:

```
	addon ui version 4.101.0.0
	addon core version 4.101.0.0
	addon language version 4.103.0.0

	♥savedirectory= ‴E:\GeneralDev\DST\Data\Cropped\‴
	♥filename=game0000
	♥iteration = ⟦integer⟧0

	call StartGimp
	while ⊂♥iteration < 8162⊃
	    ♥iteration = ♥iteration + 1
	    call OpenAndCropImages fileno ♥iteration
	end

	procedure StartGimp
	keyboard ⋘WIN⋙gimp⋘ENTER⋙
	waitfor.ui ‴/ui[@name='GNU Image Manipulation Program']/descendant::ui[@id='MenuBar']/ui[@name='System']‴
	end

	procedure OpenAndCropImages fileno
	    ♥clipboard = ‴E:\GeneralDev\DST\Data\♥filename♥fileno.png‴
	    keyboard ⋘ALT+F⋙
	    keyboard ⋘DOWN 4⋙
	    keyboard ⋘ENTER⋙
	    delay 1
	    keyboard ⋘CTRL+V⋙
	    delay 1
	    keyboard ⋘ENTER⋙
	    delay 1
	    keyboard ⋘ALT+S⋙
	    keyboard ⋘ENTER⋙
	    keyboard ⋘ALT+D⋙
	    keyboard ⋘ENTER⋙
	    delay 3
	    keyboard ⋘ALT+BS⋙
	    keyboard ⋘SHIFT+CTRL+E⋙
	    delay 10
	    keyboard ♥savedirectory+♥filename+♥fileno
	    keyboard ⋘ENTER⋙
	    delay 5
	    keyboard ⋘ENTER⋙
	    delay 2
	    keyboard ⋘CTRL+W⋙
	    keyboard ⋘LEFT⋙
	    keyboard ⋘ENTER⋙
	end
```

