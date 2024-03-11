### Repo for making a image

## ***This is the final meme I got***
![](https://github.com/yanwanngwang/stats220/blob/d67658b330611858f456261a10f694084b335492/my_meme.png)

1. ## **Start of the project**

# *As I read through the instruction for project1 I have a idea of make a meme of cat 🐱 (really love cat forevr)*
# *I start to search some cat image which can be used*
  # **The following shows the intial image**
![](https://vcahospitals.com/-/media/2/vca/images/pet-health-library/cat-breeds/ragdoll.ashx?h=275&iar=0&w=400&hash=D03391C5339EA99019B6EB08AA13587D)
![](https://www.thesprucepets.com/thmb/17UY4UpiMekV7WpeXDziXsnt7q4=/1646x0/filters:no_upscale():strip_icc()/GettyImages-145577979-d97e955b5d8043fd96747447451f78b7.jpg)
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTAzwP5imWi1yNhEVDAb8Z5FbCo65f6xlpOIw&usqp=CAU)
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcShqzKIVEf7cCormRC2LVEo2QYp_fKkqmGTJg&usqp=CAU)

2. ## **Making meme**

# *I decided to make a meme with four cats to show different mental states during the semester*

3. ## **Code Function  I used for this project**

 * image_read()
 * image_annotate()
 * image_scale()
 * image_blank()
 * c()
 * image_append()
 * image_mosaic()
 * %>%

## ***R code for the whole process***

library(magick)
#laod the first image
first_cat <-image_read("inspo_meme.jpg")%>%
  image_scale(500)
#image_annotate was used to set up a background text box that contain text, color and the location of text
text_1 <-image_blank(width = 500,
            height = 400,)%>%
  image_annotate(text = "FIRST DAY OF SCHOOL",
                 boxcolor = "#FFFFFF",
                 color = "#FF00FF",
                 size = 30,
                 font = 'Comic Scans',
                 gravity="north")%>%
  image_annotate(text = "Grace Pretty",
                 boxcolor = "#FFFFFF",
                 color = "#FF00FF",
                 size = 20,
                 font = 'Comic Sacns',
                 gravity="south")
#use code c() make them as two vectors and use image_mosaic let the background text box join the image
L1<- c(first_cat, text_1)%>%
  image_mosaic()
#repeat the above notes to make the second meme
after_cat <- image_read("inspo_meme2.jpg")%>%
  image_scale(500)
  text_2 <-image_blank(width=500,
              height=400,)%>%
 image_annotate(text = "AFTER TWO WEEKS",
                boxcolor = "#FFFFFF",
                color = "#FF00FF",
                size = 30,
                font = 'Comic Scans',
                gravity="north")%>%
  image_annotate(text = "TIRED MESS",
                 boxcolor = "#FFFFFF",
                 color = "#FF00FF",
                 size = 20,
                 font = 'Comic Scans',
                 gravity="south")
R1 <-c(after_cat,text_2)%>%
  image_mosaic()
#repeat the above codes to make the thrid meme
E_cat <- image_read("inspo_meme3.jpg")%>%
  image_scale(500)
text_3 <-image_blank(width=500,
                     height=400,)%>%
  image_annotate(text = "DURING WEEKEND",
                 boxcolor = "#FFFFFF",
                 color = "#FF00FF",
                 size = 30,
                 font = 'Comic Scans',
                 gravity="north")%>%
  image_annotate(text = "Extraverted",
                 boxcolor = "#FFFFFF",
                 color = "#FF00FF",
                 size = 20,
                 font = 'Comic Scans',
                 gravity="south")
L2 <-c(E_cat,text_3)%>%
  image_mosaic()
#repeat the above code for the forth meme
I_cat <-image_read("inspo_meme4.jpg")%>%
  image_scale(500)
text_4 <-image_blank(width=500,
                     height=400,)%>%
  image_annotate(text = "DURING CLASS",
                 boxcolor = "#FFFFFF",
                 color = "#FF00FF",
                 size = 30,
                 font = 'Comic Scans',
                 gravity="north")%>%
  image_annotate(text = "Introverted",
                 boxcolor = "#FFFFFF",
                 color = "#FF00FF",
                 size = 20,
                 font = 'Comic Scans',
                 gravity="south")
R2 <-c(I_cat,text_4)%>%
  image_mosaic()

#combine meme using image_append and stack=false means side by side
First_row <- c(L1, R1)%>%
  image_append(stack= FALSE)
Second_row <-c(L2,R2)%>%
  image_append(stack=FALSE)
#combine meme using stack =true means on top of each other
my_meme <-c(First_row,Second_row)%>%
  image_append(stack=TRUE)

#save the meme as image file
image_write(my_meme,"my_meme.png")

# FOR gif use,save each meme as a image file
cat_1 <-image_write(L1,"cat_1.jpg")
cat_2 <-image_write(R1,"cat_2.jpg")
cat_3 <-image_write(L2,"cat_3.jpg")
cat_4 <-image_write(R2,"cat_4.jpg")
