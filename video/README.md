# MEDIAEVAL VIDEO PROCESS

## Requirements

* Ubuntu 14.x LTS OS

## Libraries used

* Opencv3.0 with contrib module - ( https://github.com/Itseez/opencv/ and https://github.com/itseez/opencv_contrib )
* Libconfig ( https://github.com/hyperrealm/libconfig )
* Boost ( http://www.boost.org/ )
* Pthreads
* TBB ( https://www.threadingbuildingblocks.org/ )

## Usage

No need to install the libraries, all of them are included in lib folder.

```
export LD_LIBRARY_PATH=/home/.../path_to_executable/lib/:$LD_LIBRARY_PATH
 
./mediaeval_video [arguments]  

```
  
|Options:| | | |
|:----------|:-------------|:------|:------|
|-h [ --help ] | |Print help messages||
|-i [ --id ] |arg|ID of video| |
|-v [ --video ] |arg|    Path to video file	|REQUIRED|
|-s [ --shot ] |arg|     Shot file path||
|-w [ --written ] |arg|  OCR file path||
|-j [ --json ] |arg|  OCR JSON output path (none by default)||
|-o [ --show ] ||        show output||
|-d [ --dlib ] ||        use dlib for landmarks (disabled by default)||
|-m [ --mediaeval ] ||        mediaeval output format (disabled by default)||

<shot_file> format (*.shot)

```
<videoID> <shotID> <start_time> <end_time> <start_frame> <end_frame>
```

<OCR_file> format (*.MESeg)

```
<videoID> <start_time> <end_time> <start_frame> <end_frame> <trackID> <person_name> <confidence>
```

## Output

#### JSON format: 

"videoID".JSON

Output example:  
  
{  
"faceId":  8 ,  
"name":  "na",  
"dwellTimeInMilliseconds":  720,  
"speechTimeInMilliseconds":  320,  
"numberOfDwellIntervals":  1,  
"dwellIntervalList":  [{"s": 21760,"e": 22480}],  
"speechIntervalList":  [{"s": 22200,"e": 22520}],  
"trajectory":  [{"s": 21760,"e": 21840,"x": 334,"y": -250,"z": 2142},{"s": 21840,"e": 22000,"x": 264,"y": -151,"z": 1708},{"s": 22080,"e": 22480,"x": -200,"y": 179,"z": 918}],  
"numberOfTemplates": 2,  
"alivenessProbability": 0,  
"shots": [ 4 ],  
"evidenceList":  []  
}

#### Mediaeval format

"videoID"_audio.MESeg  
"videoID"_vvad.MESeg

```
<videoID> <start_time> <end_time> <start_frame> <end_frame> <trackID>
<name> <confidence>
```



