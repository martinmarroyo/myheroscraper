# My Hero Academia Fetcher

![my_hero_academia](https://img1.hulu.com/user/v3/artwork/36e318dc-3daf-47fb-8219-9e3cb5cd28f2?base_image_bucket_name=image_manager&base_image=2d0d3308-9323-4716-b7d8-03f171c844af&size=1200x630&format=jpeg)

I love My Hero Academia. I'm an avid reader of the weekly manga that comes out. I read the early English translations of the scans that come out every Friday (mostly). The release times vary, but it's generally available in the afternoon or
evening most Fridays. 

When I'm looking for the next issue I normally search by issue number, which takes memorization. I don't mind it, but there's certainly a better way. Also, sometimes there are break weeks where there is no release at all. I want to know about those as well, and sometimes it's useful to have a reminder that it's a break week.

This script will be used to check [MHARead](https://mharead.com) to see when the newest translation is available. Once it's available, it will send me a text message and an email with the link so that I can go ahead and read the latest issue. If it's a break week, it will also send me a text to remind me that there will be no comic. The script will also keep track of the current, previous, and next issues coming up.

## Tools used

For this project, I will be using `requests`, `BeautifulSoup`,`re`, `time`, `date`, and `schedule`. Additionally, I'll be using Windows TaskScheduler to kick it off every Friday. The overall plan is to use `requests` and `BeautifulSoup` to scrape the site to check for availability, and `re` will be used to handle searching for specific text. Finally, I'll be using `twilio` to send myself text messages from the script to either send me the link to the comic or let me know it's a break week. 

## Program Flow

On a given Friday:
- Windows TaskScheduler kicks off the script at 8:00 a.m. EST
- The script first checks the date and compares that to the next known release date
- If the current date and release date match, then the script begins to check the site for the manga.
- If the manga is on the site, then it will send me a link to the page via text message
- If the manga is not on the site, then the script will run again in two hours to check
- If the current date and release date don't match, then the script will not run and I will get a message saying that it is a break week and letting me know when the next issue will be available
