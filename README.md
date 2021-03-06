# tstools
Tools for MPEG-TS streams.
To compile use cmake for windows or linux.

More details in the Wiki.

## qt tools
viewTS : display the timestamp of a ts stream.

To compile first import in Qt top level CMakeLists.txt.
Only windows is working for the moment.

![alt text](https://github.com/OlivierLeBozec/tstools/blob/master/screenshots/pcrjitter.png)

![alt text](https://github.com/OlivierLeBozec/tstools/blob/master/screenshots/pcrptsdts.png)

![alt text](https://github.com/OlivierLeBozec/tstools/blob/master/screenshots/ptspcr.png)

## tsmap
NAME
    ./tsmap - list mpeg ts content
    Version 1.0

SYNOPSIS
    ./tsmap FILE [-pidlist -pidmap]

DESCRIPTION
    List mpeg information about the FILE. Without using PSI-SI tables

    -pidlist
       list of the pid in the file

    -pidmap
       map of the pid in the file

## tscheck
NAME
    ./tscheck - check timestamp
    Version 1.0

SYNOPSIS
    ./tscheck FILE -pid <PID> [...]

DESCRIPTION
    Display specified timestamp operation

    -pidpcr <PID>
           set pcr pid

    -pidpts <PID>
           set pts pid

    -piddts <PID>
           set dts pid

Following commands are available only at least one PID is specified

    -dump
           dump timestamp

    -dur
           get duration of the stream

    -rate
           get bitrate of pid

    -delta
           diff between same consecutive timestamp for pcr, pts or dts

    -jitter
           display jitter for pcr

    -diff
           diff between 2 timestamps : pts - pcr, dts - pts or pts - dts

## tscut
   tscut - cut mpeg ts content
   Version 1.0

SYNOPSIS
   /home/olivier/tstools/tscut FILE [-split <nb packet>]

DESCRIPTION
   cut ts stream

    -split <nb packets>
          cut file every nb packets

## Tested examples:
    ./tsmap ./ts/audio.ts -pidlist -pidmap

    ./tscheck ./ts/audio.ts -pidpcr 305 -dur -rate
    ./tscheck ./ts/audio.ts -pidpcr 305 -dump
    ./tscheck ./ts/audio.ts -pidpts 305 -dump
    ./tscheck ./ts/audio.ts -pidpcr 305 -pidpts 305 -diff
    ./tscheck ./ts/audio.ts -pidpcr 305 -jitter
    ./tscheck ./ts/audio.ts -pidpcr 305 -delta

    ./tscheck ./ts/video.ts -pidpcr 601 -dump
    ./tscheck ./ts/video.ts -piddts 601 -dump
    ./tscheck ./ts/video.ts -pidpcr 601 -pidpts 601 -diff
    ./tscheck ./ts/video.ts -pidpcr 601 -pidpts 301 -diff
    ./tscheck ./ts/video.ts -piddts 601 -pidpts 601 -diff

