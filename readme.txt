.tmpl configuration to remove visibility of initial loading screen via pygbag and autorun program without user input

***You can replace the colors with whatever color you'd like (transparent is also an option).***

---------------------------------------------------------------------------------------------------------------------------------

1. # screen pixels (real, hardware)
WIDTH=1024  # {{cookiecutter.width}}
HEIGHT=600  # {{cookiecutter.height}}

to

# screen pixels (real, hardware)
WIDTH=0  # {{cookiecutter.width}}
HEIGHT=0  # {{cookiecutter.height}}

Note: WIDTH=1024 -> WIDTH=0 / HEIGHT =600 -> HEIGHT =0

---------------------------------------------------------------------------------------------------------------------------------

2.  import embed


    platform.document.body.style.background = "#7f7f7f"

    import pygame

to

    import embed


    platform.document.body.style.background = "#000000"

    import pygame

Note: #7f7f7f -> #000000

---------------------------------------------------------------------------------------------------------------------------------

3. DELETED all of this text:

    # test/wait if user media interaction required
    if not platform.window.MM.UME:

        # now make a prompt
        fnt = pygame.sysfont.SysFont("freesans",  uy(80) )
        prompt = fnt.render("Ready to start !", True, "blue")
        pg_bar(track.len)
        screen.blit(prompt, ( marginx+ ux(80), marginy - uy(10) ) )
        compose()
        print("""
        * Waiting for media user engagement : please click/touch page *
    """)
        while not platform.window.MM.UME:
            await asyncio.sleep(.1)

---------------------------------------------------------------------------------------------------------------------------------

4.     <title>{{cookiecutter.title}}</title>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="viewport" content="height=device-height, initial-scale=1.0">
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-capable" content="yes"/>

    <link rel="prefetch" href="{{cookiecutter.cdn}}cpythonrc.py">
    <link rel="prefetch" href="{{cookiecutter.cdn}}vt/xterm.js">
    <link rel="prefetch" href="{{cookiecutter.cdn}}vt/xterm-addon-image.js">

    <link rel="icon" type="image/png" href="favicon.png" sizes="16x16">

to 

    <title>{{cookiecutter.title}}</title>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="viewport" content="height=device-height, initial-scale=1.0">
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-capable" content="yes"/>

    <link rel="prefetch" href="{{cookiecutter.cdn}}cpythonrc.py">
    <link rel="prefetch" href="{{cookiecutter.cdn}}vt/xterm.js">
    <link rel="prefetch" href="{{cookiecutter.cdn}}vt/xterm-addon-image.js">

    <link rel="icon" type="image/png" href="favicon.png" sizes="0x0">

Note: sizes="16x16" -> sizes="0x0"

---------------------------------------------------------------------------------------------------------------------------------

5.     <style>
        #status {
            display: inline-block;
            vertical-align: top;
            margin-top: 20px;
            margin-left: 30px;
            font-weight: bold;
            color: rgb(120, 120, 120);
        }

        #progress {
            height: 20px;
            width: 300px;
        }

to

<style>
        #status {
            display: inline-block;
            vertical-align: top;
            margin-top: 20px;
            margin-left: 30px;
            font-weight: bold;
            color: rgb(0, 0, 0);
        }

        #progress {
            height: 0px;
            width: 0px;
        }



Note: color: rgb(120, 120, 120) to color: rgb(0, 0, 0) & height: 20px; -> height: 0px; & width: 300px; -> width:0px;

---------------------------------------------------------------------------------------------------------------------------------

6. div.emscripten { text-align: center; }
        div.emscripten_border { border: 1px solid black; }
        div.thick_border { border: 4px solid black; }

        /* the canvas *must not* have any border or padding, or mouse coords will be wrong */
        /* average size of droid screen 470dp x 320dp  */
        canvas.emscripten {
            border: 0px none;
            background-color: transparent;
            width: 100%;
            height: 100%;
            z-index: 5;

to

  div.emscripten { text-align: center; }
        div.emscripten_border { border: 1px solid black; }
        div.thick_border { border: 4px solid black; }

        /* the canvas *must not* have any border or padding, or mouse coords will be wrong */
        /* average size of droid screen 470dp x 320dp  */
        canvas.emscripten {
            border: 0px none;
            background-color: black;
            width: 100%;
            height: 100%;
            z-index: 5;



Note: background-color: transparent; -> background-color: black;

---------------------------------------------------------------------------------------------------------------------------------

7. body {
            font-family: arial;
            margin: 0;
            padding: none;
            background-color:powderblue;

to

  body {
            font-family: arial;
            margin: 0;
            padding: none;
            background-color: black;



Note: background-color:powderblue; -> background-color: black;

---------------------------------------------------------------------------------------------------------------------------------

8.   <iframe id="iframe" class="framed" name="iframe"
width="470px" height="90%"
allowtransparency="true"
style="z-index: 10;"
style="background: #FFFFFF;"
frameborder="1"
                allowfullscreen="true"
                webkitallowfullscreen="true"
                msallowfullscreen="true"
                mozallowfullscreen="true"
                sandbox="allow-same-origin allow-top-navigation allow-scripts allow-pointer-lock"
                allow="autoplay; fullscreen *; geolocation; microphone; camera; midi; monetization; xr-spatial-tracking; gamepad; gyroscope; accelerometer; xr; cross-origin-isolated"
                src="{{cookiecutter.cdn}}empty.html"
                scrolling="yes">
            </iframe>

to

<iframe id="iframe" class="framed" name="iframe"
width="470px" height="90%"
allowtransparency="true"
style="z-index: 10;"
style="background: #000000;"
frameborder="1"
                allowfullscreen="true"
                webkitallowfullscreen="true"
                msallowfullscreen="true"
                mozallowfullscreen="true"
                sandbox="allow-same-origin allow-top-navigation allow-scripts allow-pointer-lock"
                allow="autoplay; fullscreen *; geolocation; microphone; camera; midi; monetization; xr-spatial-tracking; gamepad; gyroscope; accelerometer; xr; cross-origin-isolated"
                src="{{cookiecutter.cdn}}empty.html"
                scrolling="yes">
            </iframe>



Note: style="background: #FFFFFF;" -> style="background: #000000;"

---------------------------------------------------------------------------------------------------------------------------------

Note: Below are other color variables I didn't edit because I wanted a black background. You can edit these ones if you wanted the background to be a different color.


  # now make a prompt
    fnt = pygame.sysfont.SysFont("freesans",  uy(80) )

    def ui_callback(pkg, error=None):
        nonlocal fnt
        if error:
            prompt = fnt.render(f"{error}", True, "black")
        else:
            prompt = fnt.render(f"Setting [{pkg}] up", True, "black")
        pg_bar(track.len)
        screen.blit(prompt, ( marginx+ ux(80), marginy - uy(10) ) )
        compose()

2. 

        div.emscripten { text-align: center; }
        div.emscripten_border { border: 1px solid black; }
        div.thick_border { border: 4px solid black; }

3. 
        .trinfo{
           position:relative;
           right:0px;
           border: 1px solid black;
        }

        .framed{
           position:relative;
           top:150px;
           right:10px;
           border: 1px solid black;
        }
    </style>
