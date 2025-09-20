+++
title = "It's Been a Busy Day"
date = "2025-09-19T04:15:00+01:00"
author = "Garry"
tags = ["blog"]
description = "A long day, too much coffee, a rebuilt gallery, and the looming return to university. From server tweaks to pre-uni jitters, here’s me rambling about tech, and trepidation."
readingTime = true
toc = true
+++

```
                             Z
                       Z
        .,.,        z
      (((((())    z
     ((('_  _`) '
     ((G   \ |)
    (((`   " ,
     .((\.:~:          .--------------.
     __.| `"'.__      | \              |
  .~~   `---'   ~.    |  .             :
 /                `   |   `-.__________)
|             ~       |  :             :
|                     |  :  |
|    _                |     |   [ ##   :
 \    ~~-.            |  ,   oo_______.'
  `_   ( \) _____/~~~~ `--___
  | ~`-)  ) `-.   `---   ( - a:f -
  |   '///`  | `-.
  |     | |  |    `-.
  |     | |  |       `-.
  |     | |\ |
  |     | | \|
   `-.  | |  |
      `-| '
```

---

## Introduction

It's been a long and busy day, though it feels like I've barely done anything because I've been glued to my desk. I managed to overhaul my digital infrastructure and sort out my gallery.

After about four coffees and an entire day at the computer, I'm finally done with this whole "2.0" transition. I think I've achieved the speeds and reliability I was aiming for. I'm happy with how the site looks and works—especially the blog.

---

## Chapter 1: A Bit About the Gallery

The gallery was a bit of a pain, mainly because the way it worked originally was that whenever the container started up, the entire repository would be rebuilt and compiled from scratch (which in my case, with ~600 photos, takes 1.5 hours each time). On top of that, the website was being served using a development server—a big no-no for security, stability, and performance.

I ended up splitting the project into a "builder" and a "runner." The builder compiles the website into a shared volume with the runner, which the runner (based on nginx) then serves.

It's perfect now: secure, fast, and robust. Previously, if I restarted the server or container, the gallery would take 1.5 hours to come online—which is just not ideal. Now, once everything is built, it's dependent only on nginx startup (which is negligible—practically instant).

However, on first builds (for example, when I want to add or remove photos and need to rebuild the database), I still have to spend a significant amount of time waiting for the gallery to become available. That's where a bit of cheekiness from Cloudflare comes into play.

When nginx detects that the gallery isn’t yet fully compiled, it sends HTTP code `503` to the visitor’s browser. A Cloudflare worker then intercepts that `503` and converts it into a `302` temporary redirect to the "[gallery down](/gallery-down)" page. This means no more ugly `502` errors and better communication for visitors.

(If you couldn’t tell, I’m very proud of myself for these solutions.)

---

## Chapter 2: What’s Left / Going Back to University

Now that my most procrastinated job—actually sorting out my own stuff before other people’s—is complete, all I can really do is sit around and prepare to go back to university.

I need to make a list of things to take with me. Last year I went a bit overboard: I kitted my accommodation out like an extension of my room at home, bringing a TV, a full-fat PC, an Xbox, a bunch of speakers, and all sorts of unnecessary luxuries. This made moving in and moving out an absolute pain.

This year, much like this new website, I aim to be as minimal as possible. Bring the bare minimum to survive and study. By cutting down on luxuries and distractions, I hope to study better.

As I said, I need to make a list. That’s easier said than done—not just because I’m lazy and it’s a boring task, but also because the draft I’ve made so far feels off. My idea right now is to pack all the boring necessities (clothes, kitchen stuff, toiletries, etc.) and bring them on the day I view the new accommodation and pick up my keys. Once I drop that off, I can go home and plan properly after seeing the room in person. (This is probably just me procrastinating again, but oh well.)

Other than that, I’ve filled out the necessary documents and finished induction. All that’s left is moving out.

---

## Chapter 3: Anticipation or Trepidation?

> trepidation (noun)
>
> a feeling of fear or anxiety about something that may happen.

I’m sure many can relate: that feeling of equal excitement and anticipation, mixed with anxiety and trepidation, when it comes to going back to university for a second year. First year was by no means easy, but it also wasn’t the end of the world.

Now, of course, it depends on the degree. Many are aware that second-year content is heavier, with a significantly increased workload and little to no help from lecturers<sup>[1]</sup>. But then again, you get to return to your beloved campus, meet up with your friends, and continue your student life...

It’s an interesting feeling—equally unnerving as it is exciting.

To be frank, I am sh\*tting myself about coming back and starting my course again. But I’m coping and hoping it won’t be as bad as everyone says. In the end, as long as you don’t piss around too much, eat well, sleep well, exercise, and study, how bad could it be? (Probably foreshadowing.)

I believe this is a form of anxiety prologue to the so-called "Sophomore Slump," a term that describes the exhaustion, burnout, and general demotivation/demoralisation students face in their second year<sup>[2]</sup> (thanks to the aforementioned increased workload).

Either way, I’m not a psychologist, and I don’t really care to be. I just think it’s an interesting occurrence, and I’ve noticed it as a trend among my peers.

---

## Conclusion

To summarise:

I love rambling, referencing, and researching random sh\*te. I’ve had a long day, I’ve done what was needed, it’s 4 a.m., and I should probably get to bed.

For anyone new here, thank you for taking the time to read the ramblings of a random man on the internet. There will be more content coming soon—once I get back into the groove of blogging. Yes, I’ll be researching and rambling about random, specific topics, but if you’re into that like I am, then this website is for you.

---

## References

[1] “The First Year to Second Year University Transition,” Uninotes.com, 2022. https://uninotes.com/uni-guides/second-year-university

[2] “Sophomore Slump - My Story | George Fox University,” www.georgefox.edu. https://www.georgefox.edu/offices/student-life/resources/slump.html
