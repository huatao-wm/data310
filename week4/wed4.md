### Wednesday Week 4

Using the Neural Style Transfer script we developed during today's class replace the content and style images with two images of your own selection. Synthesize the two images by applying the following elements from the exercise.

    Define content and style representations
    Extracting style and content
    Implementing the style transfer algorithm
    Apply regularization term on the high frequency components

Describe your implementation of neural style transfer to your content and style images. How did the application of the four steps from above produce your resulting work of art. Comment on what your work means in terms of your development as a data scientist at William & Mary with forethought to the future (please feel free to take as much artistic license as you wish when answering this last question).
Stretch goal: Using the the Deep Dream script, produce another version of your artwork.
For tomorrow, we will work on producing the script from the tensorflow exercise Text generation with an RNN during class in continued preparation for Project 4.

- the two images I used are movie posters of Imitation Game and Minority Report.  Both movies are data science/AI related.  
The Imitation Game is a biographic film about Alan Turing, and Minority Report takes setting in a future world of zero crime because of crime prediction technology.
  I chose these two pictures because I think it's cool to pick two elements that represent a different end
  of spectrum of time and this technology respectively.  One represents the past and the beginning of AI, while the other forshadows a potential future that may become 
  reality.  
- I ran the code two times, flipping the choices of "content_path" and "style_path" pictures.  
- Here are the two original pictures & other pictures: [pictures](wed4_images.md)
- To my surprise, I much prefer the fast track pictures for both different settings because the fast track pictures look most creative and art-sy.  
The more I train, increase epoch, and optimize, the more it looks more "normal" and close to what the original pictures look like.
  I think pictures that come out of settings of "content_path=minority report" and "style_path=imitation game" are better than the other setting's pictures
  and the reason may be that Imitation Game poster pictures are better fit to be a style picture rather than content picture due to the patterns of Enigma machines
  in the background.  On the other hand, Minority Report picture does not have patterns in the picture.
- My personal favorite is the fast-track picture of "content_path=minority report" because it looks like a piece of art.  