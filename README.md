# Contribution 1: [Idea]: Animal calls/sounds #480


**Contribution Number:** 1
**Student:** Saarah
**Issue:** https://github.com/alveusgg/alveusgg/issues/480
**Status:** Data Repo: Merged, Site Repo: Merged! 


---

## Why I Chose This Issue

This issue would add an cool feature that engages users into the site's website. Furthermore, this feature would promote learning expereinces, and increase over knowledge about what the orginization does. Furthermore, this issue would align with my previous experience in Web Development, while allowing me to learn more about adding data files to a site and configuring them to work within the current site structure. Furthermore, this issue would allow me to sharpen previous skills I have in Web Development (including creating sites that have data passed from a backend) with newer skills (such as use of data packages, working within a larger scale, etc.). 

---

## Understanding the Issue

### Problem Description

This feature aims to include animal sounds into the site, making it more interactive and engaging. Because ALveus is a non-profit, a lot of their funding comes from user-interaction (be it through streaming, online videos, etc.). To faciliate this, having an operating site that is engaging and interactive will further promote the non-profit, and allow for a uniquer feeling when the site is visited by new traffic. Thus, inclusion of creative features (such as including animal noises) would benefit Alveus overall mission to promote Animal Conservation. I chose this because it fit within my previous skill expereince while also allowing me the opportunity to learn more about working with greater amounts of data in a web-app. 

### Expected Behavior

Where an animal sound snippet is found, there will be an option to learn about the animal and a chance to hear their animal sounds. This feature will be displayed on each individual ambassador's page, given that a clean audio snippet can be found of them. 

### Current Behavior

This feature is not currently implemented, and this contribution is aimed to include this feature. The site offers other information about the ambassadors, but does not allow for users to hear their sounds. 

### Affected Components

This affects the user interface component, as well as may include the need for initial storage needed on backend, depending on how many clips are added. Given this, it should not raise too much of a concern, given that there is a multitude of other elements in the data package. 

---

## Reproduction Process

### Environment Setup

Environment Setup was as followed through the repository's instructions. To begin, I forked the [repository]([url]([https://github.com/alveusgg/alveusgg](https://github.com/tri-sa-rah-tops/Alveus-Sanctuary))) to get the most up to date version. Then, I forked the [data repository]([url]([https://github.com/alveusgg/data](https://github.com/tri-sa-rah-tops/data))) as well, as the feature I am implementing would involve adding data files (sound clips of the animals) into the existing data structure. After that, I used the following tools as recommended by the repository's guide for development: 


1. Install nvm to find the correct node.js version, also can be viewed through the package.json file.
2. Run corepack enable
3. Register with GitHub Package Registery (needed to access the backend)
4. Install necessary dependencies from lockfile
5. Use docker to run database
6. Set environement rules through generating secret keys
7. Configure database using pnpm
8. Start server using pnpm.


Expected Behavior: Backend server and frontend server running in tandem, allowing for data to be read while using the web-app. 
Actual Behavior: Web Application working as expected.


I did have some issues regarding node versions, as I had incorrectly installed the wrong version of node. In doing this, there were some packages that came along that were not intended to be added to the repository. This was fixed in a later phase, as I upgraded node and removed the not-needed package called unrun. 

### Reproduction Evidence

- **Commit showing reproduction:** https://github.com/saarah-m/Alveus-Sanctuary
- **PLEASE NOTE: As this is an issue indenting to add a feature, there is no strict "replication of bug" since there is no previously existing feature. My goal is to add in the feature that will address the needs of the repository. 

---

## Solution Approach

### Analysis
Using the UMPIRE Method: 
- UNDERSTAND: The sound feature would add a great deal of interactivity and intrigue to the current site. Implementing this into the site also benefits Alveus' ultimate goal of animal conservation, as it allows for more knowledge about animals to be available and easily accessible to the average person.
- MATCH: There are a plethora of other sites that use sound only snippets, such as the site [GetPodcast]([url](https://getpodcast.com/)) which allows for users to listen to podcasts. Similarly, the sound feature is aiming to be added here, where only a sound is played without playing a video (only playing a .mp3)
- PLAN: Based on the current method of Alevus handeling data, I will attempt to add sound files to the data package. Then, on the front-end, these sound clips will be rendered in a sound player on each Ambassador's Page.
- IMPLEMENT: A breakdown of implementation is included in the Proposed Solution section below.
- REVIEW: This configuration can be ideal, however may cause issues with larger files. Will discuss this with maintainer and see further thoughts after short files are included in first implementation. 

### Proposed Solution

My proposed solution involves updating the repository to include these features, as well as scour Alveus's videos to find usable clips. For now, I maintain a smaller goal of clips, and hope to build on this in the future once the intial PR has been accepted. This will be done through the process mentioned above, while keeping communication with repository maintainer's incase of a change in needs, or a different desired approach. A breakdown of my current Proposed Solution Includes: 

    1. Finding clean audio clip from the variaty of online clips Alveus has posted (including streams, YouTube Videos, Instagram Reels, TikTok Clips, etc.)
    2. Adding them into the data package matching the current structure of the datapack, including:
         - Declaring the .mp3 file extension in src/global.d.ts
         - Adding audio clips into each Ambassador's folder, and naming them following the current naming convention (01.mp3, etc.) into assets/ambassadors/(AmbassadorName)
         - In src/ambassadors/sounds.ts include a file called sounds.ts that renders and stores information regarding the sound clip (such as captions, importing, etc.)  
    3. Creating a player in the frontend that makes them accessible to the user in apps/website/src/pages/ambassadors/[ambassadorName].tsx:
         - Import Audio clips, and create a player that uses the soudn clip
         - Also displays caption information
    4. In apps/website/src/types/additional.d.ts declare the .mp3 file so that it can properly be interperted and In apps/website/next.config.ts, load file as url so that it can be properly interperted
    5. Update data package to match newly included sounds. 

---

## Testing Strategy

### Unit Tests

- Use testing features provided by the repo to ensure compliation, as well as compile on local machine to ensure sound clip properly plays as expected.
- As for new tests, there were no specific ones added, since this did not adress fixing a bug. The previous tests for the site work as valid tests in the current state. 

### Code Changes

- **Files modified:**
    In Data Repository:
      - src/ambassadors/sounds.ts
      - src/assets/ambassadors/abbott/01.mp3
      - src/assets/ambassadors/jalapeno/01.mp3
      - src/assets/ambassadors/mia/01.mp3
      - src/assets/ambassadors/serrano/01.mp3
      - src/global.d.ts
      - package.json
      - tsdown.config.ts

    In Alveus (Frontend) Repository:
      - apps/website/src/pages/ambassadors/[ambassadorName].tsx
      - apps/website/src/types/additional.d.ts
      - apps/website/next.config.ts
      - apps/website/package.json
      - pnpm-lock.yaml
  
        


- **Key commits:** Largest new portions include new UI feature, sound clips added, as well as supprot for strucutre of these clips. 
- **Approach decisions:** This approach was made, as it followed along wtih the current data package in-place. This feature allows for the data to be used across all Alveus resources, not just on the site itself. 

---

## Pull Request

**PR Links: [Data Repo](https://github.com/alveusgg/alveusgg/pull/2196) & [Site Repo]([url](https://github.com/alveusgg/data/pull/288#event-26946375022))

**PR Description:** Final PRs included decriptions made above. Currently, I am waiting on a response for the maintainer, and for the PR to be merged. 

**Maintainer Feedback:**
- [07/26/2026]: Maintainer and I have been having consistent communication regarding the feature's, and I've been making changes as requested. The most recent-hang up has been regarding 

**Status:** Data Repo Merged, Wiating on Vercel Status for Site Repo 

---

## Learnings & Reflections

### Technical Skills Gained

Technically, I gained a lot of insight into large-scale web applications. This included storing data in a data packge, and rendering it so that it works in the front-end smoothly. More specifically, I gained more inisght into usign JavaScript, TypeScript, and also collaberation on an open-source project. This is my first open-source contribution, and it has been a great learning process into how a PR is open, accepting feedback, implementing it, and fianlly having it merged! 

### Challenges Overcome
There were a number of challenges faced in this process. The largest of these challenges included finding clean audio clips. Since many of the animals appear in online content, there are times where music is overlaid over the animal sounds. Thus, this was the most difficult and time consuming part of the process. 

Other than this, I found it to be quite a learning curve adhering to the Open Source format of working. It feels like there is a large barrier to overcome (such as, a new vocabulary to learn, understnading a certain orginization's chosen method of handeling features, etc.) I believe that this will get eaier with time, and this process definilty was a great introduction to this! 



### What I'd Do Differently Next Time

If I had to do this again, I would spend more time getting familar with the codebase. I did an overlook of the codebase, however I now realize I could have gone much more in depth with the process. I would definilty do this next time, as I find it makes the process later more simplified. 

---

