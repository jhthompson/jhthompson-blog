---
title: Chociattos and Carnivals
header:
  teaser: /assets/images/rottenburg_header.jpg
categories:
  - germany
tags:
  - Bosch
  - running
  - sensors
  - Rottenburg
  - carnival
  - festival
  - parade
  - beer
  - chociatto
  - pizza
  - visual inertial fusion
toc: true
toc_label: Topics
toc_icon: fa fa-ellipsis-h
---

This week was the first official full week of work at Bosch. We also traveled to the nearby town of [Rottenburg am Neckar](https://en.wikipedia.org/wiki/Rottenburg_am_Neckar) on the weekend for a carnival / festival type of event. There was a small(er) parade on Saturday, and a large one on Sunday.

## What's in Your Phone

Have you ever wondered what company makes the sensors that go into your smartphone? If you're like me, probably not. Rather, I didn't think about it until I started working for a company that puts sensors into ["three-quarters of smartphones in the market"](http://www.huawei.com/minisite/hwmbbf15/en/bosch.html). If you're curious to see what sort of sensors are in your own phone, Android users can download [an app](https://play.google.com/store/apps/details?id=com.android2ee.project.my.sensors&hl=en) that will tell you the manufacturer of each sensor in your phone. The odds are pretty good that there will be a Bosch sensor in that list somewhere. In particular, the [BMI 160](https://www.bosch-sensortec.com/bst/products/all_products/bmi160) is quite a popular sensor for modern smartphones, due to it's reduced power consumption and other features. If you're an iPhone user, I'm not sure how to verify what's in your current device, but Bosch has a contract with Apple to build ["as much of half of the motion sensors"](http://www.idownloadblog.com/2017/05/05/bosch-iphone-8-motion-sensors/) in the iPhone 8.

***

<figure class="align-center">
  <img src="/assets/images/sensors_screenshot.jpg" alt="">
  <figcaption>Some of the sensors in my personal device. The BMI 160 is a particularly popular Bosch sensor</figcaption>
</figure>

***

## Chociattos

Bosch Sensortec has some of the best coffee machines I have ever used. Apparently they cost around €5,000 each! My drink of choice for now has been the ["chociatto"](http://coffeeninjatraining.com/chocciato.html) which is apparently similar to a machiatto, but uses chocolate. I've never really been a coffee drinker before in my life, but this work term might just change that.

## Pizza Planet

Thursday night, we decided to go out and get some pizza. Not knowing where to go, Google maps led us to one of the closest places with good reviews - Pizza Planet (unaffiliated with Toy Story). After a brief walk, we got there, and found out from the owner that Pizza Planet is the oldest pizza place in Reutlingen, started by him 20 years ago. He is also the man in the photograph below, and was very helpful. I'm sure we'll be making more trips to Pizza Planet again in the future.

***

<figure class="align-center">
  <img src="/assets/images/pizza_planet1.jpg" alt="">
  <figcaption>We ordered pizza from this exact guy!</figcaption>
</figure>

***

<figure class="align-center">
  <img src="/assets/images/pizza_planet2.jpg" alt="">
  <figcaption>The good stuff</figcaption>
</figure>

***

## Visual Inertial Fusion

I'm going to try and describe the sort of work that I'm doing at Bosch, feel free to skip this if you're not into learning how robots can navigate their environment (but seriously you should keep reading, it's super cool stuff). Here's a video demonstrating an existing algorithm at work:

***
<iframe width="560" height="315" src="https://www.youtube.com/embed/2zE84HqT0es?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen>
</iframe>
***

The category of work that I'm involved with can be classified as SLAM (simultaneous location and mapping). This means that a robot is trying to navigate an unknown environment (meaning it knows nothing about its surroundings). Therefore, it needs to do 2 things at once: create a map of its environment, and figure out where in that environment it is. There has been massive interest in this field in recent years, with drones often being used to test new algorithms, with self driving cars being another major application.

What makes the SLAM problem difficult is that the processes of creating a map and localizing yourself within that map are tightly dependent on one another, and an error in one process will directly cause an error in the other. If your map is wrong, you won't be able to navigate through your environment properly. Vice versa, if you're not able to properly determine where you are in a map, even if you know the map is perfect, you won't be able to get very far. When both are unknown (as in most SLAM algorithms, and indeed this is the most common and useful case), any uncertainty about the creation of the map or the localization process will cause uncertainty about the other process, and this error is only amplified the longer the system continues to be run (called drift, which can be partly solved in some cases by loop closure, another topic entirely).

So how can the SLAM problem be solved? One option is to use [LIDAR](https://oceanservice.noaa.gov/facts/lidar.html) sensors for map creation and localization, as they are very good at determining precise distances from an object. However, for many applications, LIDAR isn't a viable solution, as they tend to be expensive, and can be heavy to mount on a drone. We're looking at another method of solving the problem, ideally using only a single camera and a cheap IMU unit. This is an interesting setup because basically every smartphone has a single camera and an IMU, and could potentially run this sort of algorithm if it was efficient enough.

If had to summarize the project that me and Patti are working on in three words, they would be: "visual inertial fusion". That's a very nice buzzword, but what does it actually mean? Essentially, it means the combination of data from multiple sensor sources (in this case, visual = video from a camera, inertial = accelerometer and gyroscope data from an IMU, and fusion = fusion of those two kinds of data). On their own, either kind of sensor can be used to make a state estimation, or to predict where in an environment a robot is. However, both sensor readings encode different things about the environment around them, ie. the information presented by one isn't completely reproduced by the others data. Because of this property, if there was a way to combine both kinds of data, it would be a more accurate estimate of the robots current position. The actual way that the algorithm fuses the data from the two sensors can change, but the basic idea is that the position estimate will be more accurate than a single sensor could accomplish on its own.

Also, we have some pretty fun tools to work with. One of our major objectives at the moment is to figure out how to get our [Turtlebot](http://www.turtlebot.com/turtlebot2/) working. If you want an introduction to what a Turtlebot is and what it can do, check out that link.

***

<figure class="align-center">
  <img src="/assets/images/turtlebot.jpg" alt="">
  <figcaption>Our Turtlebot robotic platform</figcaption>
</figure>

***

<figure class="align-center">
  <img src="/assets/images/computers.jpg" alt="">
  <figcaption>44GB of RAM between these three machines...</figcaption>
</figure>

***

## Rottenburg Carnival

As per the advice of someone who had grown up in Reutlingen, we spent most of the weekend attending the [Fasnet](http://www.narrenzunft-rottenburg.de/NZ/Fasnet-in-Rottenburg.html) carnival. On Saturday we walked around and ate some food from the stands set up in the middle of the square. There was also a parade later in the afternoon that we watched.

***

<figure class="align-center">
  <img src="/assets/images/rottenburg2.jpg" alt="">
  <figcaption>Kartoffelspirale!!!</figcaption>
</figure>

***

<figure class="align-center">
  <img src="/assets/images/rottenburg1.jpg" alt="">
  <figcaption>The more ridiculous your costume the better</figcaption>
</figure>

***

<figure class="align-center">
  <img src="/assets/images/rottenburg3.jpg" alt="">
  <figcaption>A more traditional sort of costume</figcaption>
</figure>

***

<figure class="align-center">
  <img src="/assets/images/rottenburg4.jpg" alt="">
  <figcaption>First look we got at the town</figcaption>
</figure>

***

<figure class="align-center">
  <img src="/assets/images/rottenburg5.jpg" alt="">
  <figcaption>Bridge in town</figcaption>
</figure>

***

I'm not sure exactly what the history behind the carnival is, but in the parade there were plenty of witches / hag-like costumes, as well as other recurring characters like clowns and animals. The parade on Sunday was extremely impressive, as it went on for close to two hours and contained a variety of bands, floats, and costumes.

***

<figure class="align-center">
  <img src="/assets/images/rottenburg6.jpg" alt="">
  <figcaption>Interesting vehicle</figcaption>
</figure>

***

<figure class="align-center">
  <img src="/assets/images/rottenburg7.jpg" alt="">
  <figcaption>So many costumes</figcaption>
</figure>

***

<figure class="align-center">
  <img src="/assets/images/rottenburg8.jpg" alt="">
  <figcaption>Colorful, nature themed people</figcaption>
</figure>

***

<figure class="align-center">
  <img src="/assets/images/rottenburg10.jpg" alt="">
  <figcaption>Couple of birds</figcaption>
</figure>

***

There were also multiple sections in the parade where the participants would go into the crowd, take a somewhat willing "victim" and dump them into a pile of straw. Other versions of this included throwing confetti onto people and rubbing it into their hair, or throwing straw over the crowd. This caused a bit of a mess, but it was all in good humor and quite fun to watch.

***

<iframe width="560" height="315" src="https://www.youtube.com/embed/LKVnhavYmXE" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

***

<figure class="align-center">
  <img src="/assets/images/rottenburg9.jpg" alt="">
  <figcaption>The aftermath of the parade (that's not snow or ice, it's confetti)</figcaption>
</figure>

***

## Kali Café Bar & Lounge

If you ever find yourself in Reutlingen and are looking for a chill spot to have a coffee or a beer, the [Kali Cafe](http://www.kali-bar.de/) is a great place. They have old movie theater chairs in their upstairs seating area, and are overall a very relaxed place. Also, the sweet Radler they serve is very good.

***

<figure class="align-center">
  <img src="/assets/images/berg.jpg" alt="">
  <figcaption>Beer from Kali</figcaption>
</figure>

***

## Running

Monday - Busy day at work and afterwards, unplanned rest day.

Tuesday - [Easy run](https://www.strava.com/activities/1394766893), still trying to find good roads to run on at night. Felt good, but the IT band on my right side was having some pain after the run, I think it's just getting used to running again.

Wednesday - Met up with a Bosch [running group](https://www.strava.com/activities/1396372618) to get some tips from a professional triathlete. I assumed there would be some sort of workout to go with the session, but it was just a small hill repeats workout. Not an exhausting workout by any means, but it was nice to run with some company for the first time in a while.

Thursday - [Met up with a runner](https://www.strava.com/activities/1397958591) from a local university. He told me that in the summer there can be as many as 20 people who come out to run with his group, but in the winter people don't run outside as much because of the cold (it was about -1 C on that day... :snowflake:).

Friday - Rest day. Busy day at work and afterwards.

Saturday - Twenty minute [tempo run](https://www.strava.com/activities/1401160398) around the wooded trails. Pretty happy with how this went, since this was the first longer effort I'd tried in a while.

Sunday - Yet another rest day. The carnival in [Rottenburg am Neckar](https://en.wikipedia.org/wiki/Rottenburg_am_Neckar) and writing this post took up all of my time.

Overall, I'm really happy with how this week went; work was interesting and we spent a good portion of the weekend traveling. Hopefully this formula can be replicated and repeated for another 5.75 months!!!

Jeremy
