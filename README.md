# wplot
Windows ploting (wplot) Software

wplot

wplot is a quick and easy to use Windows GUI software program for quickly creating and analyzing data plots.
Create plots with millions of data points in seconds. 

Once the data is plotted you can easily use the many tools to explore your plot in great detail by zooming in/out,scrolling your plot and much more.

Mutiple objects (data files/sets) can be plotted and overlaid.

Objects can be individually hidden/viewed as the plot is studied.

wplot does NOT generate data. wplot reads data points from file(s) and generates varied plots based on that data.
A single Windows 700K ish executable. Simple installation. Just download executable file and run. 
wplot is 100% FREE to use. No restrictions of any kind. 

There are a few .dpt command file examples in the examples folders.  Just download the examples folder contents and then type "wplot xxx.dpt" to see that particular plot example.

This is an experiment for me. I have used free software for years and felt the need to give back. 
I wrote this plotting program years ago because all of the tools out there were too slow and could not 
handle a million or two data points quickly. Other tools would not let me change the vertical or horizontal
scaling and other aspects of the plot on the fly. 
I used this program in my line of work mostly for analyzing milli-second and micro-second timing situations. 
I would plot the acquired data and then zoom in and use the tools to determine event timing to improve 
my processes. It eventually became my goto tool for plotting data in many different sorts of situations. 
My hope is that other people will find this tool useful as well.

If you find this program worthwhile and feel like donating, that would be a first :-)


```

  wplot  Version 1.33
  
  Usage: wplot <cmdOpts>  cmd_file  or  data file
  
  <cmdOpts>  
     -t    <title>    :: window title
     -x    <xtype>    :: xtime xint xfloat ... 
     -s    <dottype>  :: dots line bars ... 
     -c    <colspec>  :: x:y ex 2:4 use cols 2 and 4
     -T    <objTitle> :: object title
     -p    <colseps>  :: data file column seperators
     -P    <fileName> :: print to filename and exit
     -h               :: help 
  
  Try:  'wplot -h > wplot.hlp'  then 'wplot wplot.hlp'

  NOTE: This version of wplot has seps now set to a space.  Older versions had default
        seps as space AND tab. So if you want space AND tab use 'seps st' command.

  wplot is 100% FREE to use.  No restrictions of any kind.  This Software is provided
  as is, without any express or implied warranties of any kind.  Donations welcome.
  If you find this program worthwhile, feel free to donate what you feel is fair
  by using this link:  https://paypal.me/dhkConsulting
  or https://www.paypal.com/donate/?hosted_button_id=ZJP8C9C6SD6WE
  Feedback is also welcome at: ibjoepat@yahoo.com
  
  wplot reads a command file for information about how to format the plot and where
  to read the plot data from.  All data files are text files. wplot does not read
  binary data files. If your data file has x data in col 1 and your y data in
  column 2 and you can use the default formatting, you can skip the
  cmd_file and have wplot read the data file directly. Typical lines in the
  data file would be something like:
  '934, 345' or '12:04:20.234 97' or '89.34 4495.234' or '10/05/2034_04:12:45 87.93'
  Command line parameters can be used to override the default cols and formating.


  Cmd file:

     ';' , '#' and '.'  start a comment line ( ie. ignored )

     Commands:

     The following should be set before any 'plot' cmds.

                     default x axis data type is xfloat
     xtime         - x axis data type (expects HH:MM:SS.123 in data file)
     xtimemilli    - x axis data type (expects HH:MM:SS.123 in data file)
     xfloat        - x axis data type (expects 123[.xxxx] in data file )
     xint          - x axis data type (expects 123 in data file )
     xdate         - x axis data type (expects mm-/dd-/yy(yy) 
                      or mm-/dd-/yy(yy)_HH:MM:SS in data file)
                      '_' can be ' ' if ' ' not in seperators. ie. 'seps c'
                      display format will always be mm/dd/yyyy.
                      stored as secs (so col x <mods> will be secs).
     xdate_2       - x axis data type (expects dd-/mm-/yy(yy) 
     xdate_3       - x axis data type (expects yy(yy)-/mm-/dd) 
     title  <text> - text put in window title bar.
     wxsize  <val> - initial window x size ( must set both ).
     wysize  <val> - initial window y size ( must set both ).
     full          - initial window will be fullscreen.
     bgcolor <val> - set background color( see Color Info ).
     lbcolor <val> - set grid label color( see Color Info ).
     gdcolor <val> - set grid lines color( see Color Info ).
     seps    <str> - ( data file col seperator(s);ex: 'sc-' s is ' ' c is ',' '-' is '-' )
                     ( default seperator is 's' ie. space )
                     ( special chars are 's':space;'t':tab;'c':comma)
                     ( single character seperator is MUCH faster for big files.)

     These should be set after any x cmds ( above ).
     xmax    <val> - set an x axis larger than found in data files.
     ymax    <val> - set an y axis larger than found in data files.
     xmin    <val> - set an x axis smaller than found in data files.
     ymin    <val> - set an y axis smaller than found in data files.
     ysig    <val> - set y significant digits for display.
     xborder <val> - set x axis border to value( or can be '%'val).
     yborder <val> - set y axis border to value( or can be '%'val).

     xgridlines <val> - set number of x axis grid lines.
     ygridlines <val> - set number of y axis grid lines.
     no_warn_order    - no out of order warnings.

     print <fname>    - print plot;should be after all 'plot' cmds.
                        prints to default print device.
                        <fname> for print to file.
     stop        - stop processing command file.
     exit        - exit program; use for batch printing.
     usage       - output usage text to stdout and exit.

     plot <filename> <options>  - one 'plot' command for each object.
        <options>  in any order :
  
            seps <str>            ( data col seperator(s); see 'seps' above )
            line lines polygon    ( object type ) 
            dots                  ( object type; can have sizecol )
            hline vline bars      ( object type )
            hspike vspike         ( object type; use sizecol to set length )
            labels                ( object type; needs labelcol; can have colorcol )
            lt<:a#:w#:s#:ovh>     ( apply to labels; lt options can be: 
                                    a-text angle (0-360) s-font size  (0-800) 
                                    w-remove leading/trailing spaces from text (0-1).
                                    o-text align : determine text anchor point.
                                        where v and h are letters of the following:
                                        r-right l-left c-center   or h-auto horizontal 
                                        b-bottom t-top e-baseline or v-auto vertical 
            fat thick thin square ( modify line )
            linedot               ( modify line,v|hspike)
            hatch                 ( modify polygon, bars)
            small medium  large   ( apply to dots )
            solid dash dotdash    ( apply to line; only thin lines)
            %<percentage>         ( apply to bars; bar width percentage)
            bt<:c#:a#:p#:g#:s#>   ( apply to bars; turn on bar titles)
                                    <bt text options> can be c-color (see Color Info)
                                    a-text angle (0-360) g-significant digits (0-5)
                                    s-font size  (0-800) p-txt vertical pos (0-100) ) 
            1-32/xRRGGBB/_HHSSLL  ( for color )
            title or t <text>     ( title of this plot object.
            x<mod>:y<mod>         ( col nums for x,y data. 1 based;no spaces) def 1:2
                                    <mod> can be *i, /i, +i or -i where i is a float.
                                      allows each x or y item to be modified by i.
                                    If x is set to 0 then internal counter is used
                                      for x.  Allows only y data in file.
            opt                   ( x,y data above is optional. No Warn/Err msg if missing )
            zhide                 ( if all y data is 0 then set object to NOT visable )
            sizecol <num>         ( col num in file for size info. )
            colorcol <num>        ( col num in file for color info. )
            labelcol <num>        ( col num in file for label text. )
            hide  off  show       ( object visable/not visable. )

     Notes: 
     Columns in data file <filename> must be separated by SPACEs
     or use the 'seps' option to change seperator(s).
     No ','s allowed in <filename> column data. (ie. 12,300 must be 12300).
     Z order of objects is determined by the order of 'plot' commands.

     If <filename> starts with a ':<tag>' then data lines follow in this cmd file
     beginning at line w/label ':<tag>' until EOF or line with "end" is encountered.
     For speed do not use ':<tag>' for large amounts of data. Use seperate data file(s).

     The lt:ovh determines what point on text is used to anchor the text.
     The auto h&v options auto pick anchor point; useful when data is above and
     below the zero line. Auto v for 0 angle text and h used for 90 degree ...
     Sadly bt font sizes differs from lt font sizes due to the way bars are drawn.


   Color Info:
       xRRGGBB is RGB color definition;  _HHSSLL is HSL color definition.
       To view the predefined 1-32 colors run program and use menu view->colors.
       See color RGB values; run program; menu view->colorwheel press OK.

   Polygon:  A blank line in the data file will complete a polygon and start another.
             ie. a 'plot' obj can have multiple polygons in it.

  Example:
  
  
  xtimemilli
  plot test2.dat line thin 7  t test2_line dash
  plot data1 1:4 dots large  title  'bid dots'
  plot data1 1:5/10 dots medium  x40A056  t ask_dots
  plot :limitdata 1:2 line dash 4 t limits



  ======================================================================
  
  User interface: 
  
    Buttons:  Mouse over button and read status line for definition.
  
    Mouse:
       left button      -  pan screen
       Ctrl left button -  show crossHair at cursor.
                           status line updated with X,Y Pos. information.
       Shift left button-  zoom in with selection rectangle
       left double click-  make mouse loc center of window.

       right button     -  hide/show objects and show object titles dialog
                              select object to toggle show/hide.
                              ctrl + select object-  object properties
                                 change object properties dialog.
                           (Good way for new user to see examples of
                            all object types listed above.
                            Try it:Ctrl-right button then Ctrl-click on obj.)
       shft right btn   -  object titles and # points in object.
       wheel            -  zoom In/Out  w/Ctrl key - x axis only.
       wheel            -  zoom In/Out  w/Shft key - y axis only.
       Ctrl               -  cursor X:Y tooltip shows obj name.

       If there is a data point under the cursor and 'toggle Size Circles' is on
         then the 'sizecol' info will show up on the status line.

    Keys:
    
       Insert           -  zoom in
       Delete           -  zoom out
       Home             -  full view
       Up/Down Arrow    -  move up/down
       Left/Right Arrow -  move left/right
  
       Ctrl + L/R Arrow -  move left/right big
       Alt  + L/R Arrow -  move left/right little
  
       Ctrl + Insert    -  zoom  in X axis only
       Ctrl + Delete    -  zoom out X axis only
       Shft + Insert    -  zoom  in Y axis only
       Shft + Delete    -  zoom out Y axis only
  
       Page Up/Down     -  move up/down big
  
       Ctrl + C         -  put x coord ( ie. time ) where cursor is onto
                               clipboard  in  '/HH:MM:SS' format.

       Vi type marks:
           save    location ( view )  'm' + letter  ( '0' - 'Z' )
           restore location ( view )  ''' + letter  ( '0' - 'Z' )



title example cmd file.
xint  
xborder %3  

#
# if you had a file called 'plot.data' and wanted to plot data.
#
#     filename   fields    title     object   color
#                                     type
#plot plot.data   1:2*3     t hour     line       1
#Plot plot.data   1:3       t zone5    linedot    2 
#plot plot.data   1:4/100   t zone3    line  square 3

plot :diag      1:2   t diagonal   line fat    4 linedot 
plot :diag      1:2   t diagsquare line square 5 
# local start here; diag line showing dots at coordinates

:diag 
1   1
26  26
51  51
76  76
101 101
126 126
151 151
176 176
201 201
end

plot :polygon    1:2         title polygon   poly  x004600
plot :polygon    1-35:2+120  title p2        poly  hatch x6C0000

:polygon 
60  19
100  9
130 69
60  19
end

plot :triangle    1/2:2*1.5   title triangle   line  8

:triangle 
50  50
150 50
100 150
50  50
end

plot :bar   1:2   t bars  bars lineDot  fat  10

:bar  
20  130
170 120
end
plot :hline  0:1   t horz_Line  hline x208820 
:hline
205
end 
plot :barw   1:2   t 'wide bars' bars  %8  15
plot :barw   1+10:2-10  t barTxt  bars  bt:c6:s150  %15  x408080 hatch
plot :barw   1+20:2-15  t bt2     bars  bt:c3:s150:a0  %18  x206060

:barw  
135  43
181 95
end

plot :txt 1:2 t tdots dots 15 colorcol 3 large
plot :txt 1:2 t txt labels lt:s120 12 labelcol 1 colorcol 3
:txt
75  214  12
96  214  16
118 214  21
end

plot :text 1:2 t txt2 labels lt:s60:oel:a35 26 labelcol 3 seps c
:text
140, 160, A line with steps
end

plot :dots  1:2  t dots  dots x006400 medium sizecol 3

:dots 
40  110  10
50   90  45
150  80  60
end

plot :spikes 1:2   t vert_spikes vspike colorcol 4 sizecol 3/10 fat  linedot
plot :spikes 1+100:2 t vspike2   vspike colorcol 4 sizecol 3/8  thin linedot

:spikes 
03 170  100  10
10 170 -250 13
17 170 -180 12
23 170  350 16
end





```
