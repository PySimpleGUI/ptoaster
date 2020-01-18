# ptoaster

## A Python Based "Toaster Notifier"
## Displays a toaster-style window anywhere on your screen with fade-in/fade-out

![ptoaster](https://user-images.githubusercontent.com/46163555/72669402-48db5980-39ff-11ea-8d8c-5ba5dcd7b4db.gif)


Uses multi-processing so that the window is **completely independent** from any other windows you may have open in your application.


## Requirements

`ptoaster` uses PySimpleGUI to display the small windows.  You will need to install [PySimpleGUI](http://www.PySimpleGUI.org) if it is not installed for you when you pip installed `ptoaster`

One of these will install it for you.
```
pip install PySimpleGUI
pip3 install PySimpleGUI
```


## Icons

`ptoaster` includes a number of icons in the code itself.  

If no icon is supplied, then the "Success" icon is used.

![toaster (2)](https://user-images.githubusercontent.com/46163555/72669483-14b46880-3a00-11ea-826d-2a18c96c4694.jpg)

![toaster (6)](https://user-images.githubusercontent.com/46163555/72669480-141bd200-3a00-11ea-9c4f-36bbae6f8ef1.jpg)

![toaster (7)](https://user-images.githubusercontent.com/46163555/72669481-14b46880-3a00-11ea-9610-695d8d26abd0.jpg)

![toaster (1)](https://user-images.githubusercontent.com/46163555/72669482-14b46880-3a00-11ea-8fec-f4202ecfc146.jpg)


![toaster (3)](https://user-images.githubusercontent.com/46163555/72669484-14b46880-3a00-11ea-8a9d-ffcdf1eb15c8.jpg)

![toaster (4)](https://user-images.githubusercontent.com/46163555/72669485-154cff00-3a00-11ea-9651-861764de871a.jpg)


![toaster (5)](https://user-images.githubusercontent.com/46163555/72669479-141bd200-3a00-11ea-935a-ec6ee95e4057.jpg)

![toaster](https://user-images.githubusercontent.com/46163555/72669628-4fb79b80-3a02-11ea-93fd-bf08e5280730.jpg)


## Using

`ptoaster` enables you to display a toaster notification window without the need for your program to stop execution while it's being displayed.  In other words, the call is a non-blocking call that immediately returns back to your program and the window display will be performed in paralell with your application.

There are only 2 required parameters, the title and the message. `ptoaster.notify(title, message)`


The full call signature for `notify` is:

```python
def notify(title, message, icon=icon_success, display_duration_in_ms=DEFAULT_DISPLAY_DURATION_IN_MILLISECONDS,
           fade_in_duration=DEFAULT_FADE_IN_DURATION, alpha=0.9, location=None):
    """
    Displays a "notification window", default location is the bottom right corner of your display.
    
    Notification window has - an icon, a title, and a message
    
    The window will slowly fade in and out if desired.  Clicking on the window will cause it to move
    through the end the current "phase". For example, if the window was fading in and it was clicked,
    then it would immediately stop fading in and instead be fully visible.  It's a way for the user
    to quickly dismiss the window.

    :param title: (str) Text to be shown at the top of the window in a larger font
    :param message: (str) Text message that makes up the majority of the window
    :param icon: Union[bytes, str] A base64 encoded PNG/GIF image or PNG/GIF filename that will be displayed in the window
    :param display_duration_in_ms: (int) Number of milliseconds to show the window
    :param fade_in_duration: (int) Number of milliseconds to fade window in and out
    :param alpha: (float) Alpha channel. 0 - invisible 1 - fully visible
    :param location: Tuple[int, int] Location on the screen to display the window
    :return: (Any) The Process ID returned from calling multiprocessing.Process
    """
```

### Sample Program

```python
import ptoaster

# IMPORTANT - you need to make sure you call notify from the main program
if __name__ == '__main__':
    ptoaster.notify('Your Title', 'Your message... this is the most simple call possible.')
    ptoaster.notify('Upper Left', 'This one will show up in the upper left corner of the screen', 
                     location=(0,0), fade_in_duration=0)
```

## Limitations / Future Additions

At the moment, the size of the text and the width of the window are somewhat hard coded.  The height of the window can vary however.

A next logical step in expanding the capabilities will be to allow for changing the fonts, the width of the window, wtc.

The decision was made to keep things simple for this initial release.  Better to get seomthing basic that works well shipped than something fancy and not quiite operational that never ships.

## Hungry for more?

If you want more examples like this one to help in creating your GUI, then be sure and check out the many programs found at http://Demos.PySimpleGUI.org. 

![logo500](https://user-images.githubusercontent.com/46163555/71866174-62150980-30d3-11ea-8a27-451849cd88ed.png)
