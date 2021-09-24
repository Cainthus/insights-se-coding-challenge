# Take-home coding challenge.

This is a practical application test. It’s a mini version of a scenario you’ll face on the job.
We ask that you spend no more than 2-4 hours on the test. It doesn’t have to happen all at once. We understand this is an interview exercise and people have other commitments.

We also give you free reign to use whatever code libraries you'd like, but coded in python.

You’ll have a week to complete a technical exercise and submit the code repository link back to us.

If you run out of time you can write a summary of what else you would have done to complete the test or any other suggestion for improvement.

## What do we expect?
* Code that is clean, readable, performant, and maintainable 
* Coding standards 
* Coding best practices 
* Comments 
* Documentation 
* Logs 
* Exceptions treatment 
* Automated tests


## What can we learn about the candidate?
* Can the candidate write code as per the company’s levels and standards? 
* How do they approach a problem? 
* What do they do when they get a little stuck? 
* Can they brute force their way through this? 
* Are they going to be “done” as soon as it’s running, or are they going to clean up any inefficiencies once it’s working? 
* Do they leave good documentation and comments on their code? 
* Do they write a clear and concise readme 
* There aren’t really right or wrong answers to a lot of this. It’s just really helpful and interesting to us to see how candidates work.

## Problem

### Given the folder structure of image frames captured by a camera:
```
/node
    /images
		/frames
			/farm-xxx
				/camera-1
					/images
						/2020-11-02
							/00  (hour)
								farm-xxx_barn-3_camera-1_2020-11-02T00h00m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T00h01m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T00h02m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T00h03m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T00h04m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T00h05m00s+0000.png
							/01
								farm-xxx_barn-3_camera-1_2020-11-02T01h00m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T01h01m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T01h02m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T01h03m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T01h04m00s+0000.png
								farm-xxx_barn-3_camera-1_2020-11-02T01h05m00s+0000.png
							...
							...
							/23
```

### Requirements:
Each day/folder contains a folder for each hour, and each hour/folder contains 5 images (one for every minute).

Each image filename contains a UTC timestamp in it. 

The camera works on UTC but the farm works on local timezone dates. You need to read the date range contained in these files and return a dict that aggregates the files by their respective timezone-aware date.

### What do you need to do:
Create a class that receives {path} at the initialization
1) {path} str = Absolute folder_path
2Create a method that returns the date range available on the {path}
    Return format:  f”date range: {start_date} - {end_date}”
2) Create a method that receives {timezone_tz} as parameter and:
   1) It gets all files in {path}/images/frames/farm-name/camera-x/images/{date}/{hour}/**image_files_per_minute**.png 
      1) The filename contain a UTC timestamp in it, following this pattern: farm-name_barn-3_camera-1_2020-11-01T00h00m00s+0000.png 
   2) Extract the UTC timestamp from the file name and convert it to timezone-aware, using {timezone_tz} 
   3) Return a list of dict that aggregates the <Absolute path>/files by timezone-aware date in which the UTC file belongs (per camera)
           @return:
```
[
   {
      "date_tz" str: "2020-10-31",
      "files" list: [
        "absolute_file_path"
      ]
   },
]
```
```
Example:
[
    {
        "date_tz":"2020-11-02",
        "files": [
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/00/*{file_names_from_01_to_05_minute}',
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/01/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/02/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/03/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/04/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/05/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/06/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/07/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/08/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/09/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/10/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/11/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/12/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/13/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/14/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/15/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/16/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/17/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/18/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/19/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/20/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/21/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/22/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/23/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-02/17/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-03/00/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-03/01/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-03/02/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-03/03/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-03/04/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-03/05/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-03/06/*
            '.../node/images/frames/farm-xxx/camera-1/images/2020-11-03/07/*
        ]
    }
]
```

**IMPORTANT**: 
* Such that Each local date maps to corresponding set of image filepaths. 
* You should consider that there may be more than one camera, like, camera-1, camera-2 etc folder.

