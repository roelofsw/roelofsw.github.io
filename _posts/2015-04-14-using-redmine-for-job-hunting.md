---
layout: post
title: "Using RedMine for job hunting"
date: 2015-04-14 +1000
comments: true
---

This investigation started off as a result of my frustration with the seemingly haphazard nature of looking for work using multiple avenues (websites, recruiters, leads from friends, etc) and keeping track of calls, e-mails and documents submitted (resumes, code samples, cover letters, etc), and the lack of options available to deal with this dilemma.
 
When I say lack of options, it doesn't mean there are no options.  I've signed up for a [jibberjobber](http://www.jibberjobber.com) account, and by and large it looks like a good site.  But it means I have to figure out and learn something new, which won't have much use to me beyond the immediate need of finding a job.  Something like [trello](http://www.trello.com) or a self hosted [kanboard](http://kanboard.net) could work, but they don't display 'at a glance' information I'd like to see.

Then I started writing my series of articles on self-hosting applications on a Raspberry Pi, and got re-acquainted with [RedMine](http://www.redmine.org).  Even though I'm a Jira fan, the inability of that to run on a Pi may have been fortuitous.  With a bit of tweaking, it turns out that RedMine is actually a really good way of keeping track of job application statii.  Beyond that, it has mobile clients available, and with a VPN (or hosted on a VPS), I have easy secure access to all my information, anywhere.  Oh, and of course it's free and open source :)

Note the following:

* It is still a work in progress.  If I find better ways of doing anything (or someone suggets something cool), I'll add it to the article.
* Though I've used RedMine, the approach below should work with almost any configurable issue tracker out there.  The point is that it is not hard to formalize the job hunting process using available tools.

So, without trying to convince anyone of the merits first, I'll show you what I've done, and you can decide for yourself if it's worthwhile.

# 1. Getting ready

First, you'll need a copy of RedMine running.  I'll be writing an article on that in the near future, but for the moment, you can use their website as a reference.  You'll need to do the following:

* If you plan on having it available anywhere, you'll need a computer with some ports open to the interwebz, or a VPS.
* [Install](http://www.redmine.org/projects/redmine/wiki/RedmineInstall) a copy of redmine - in short, it will run on pretty much any platform, and you will additionally need Ruby and a database server.
* If you want to be able to access your installation remotely, either an open port on your router (or VPS) or a VPN will be necessary.  For security reasons, I'd suggest using a VPN (such as [OpenVPN](http://openvpn.net), which is included with most Linux installations).
* For android phones and tablets, there is a very nice client called [MyMine](http://mymine.upactivity.com/) (there are others - I just happen to like MyMine)

_If you just want to try this approach without investing the time in setting up RedMine, you can apply for a demo account on RedMine's site.  Note that it my be upgraded or reset at any time, so only do this to experiment - don't use live data._

Depending on my available time, I might look at putting together a Docker container with a configured RedMine at some point - watch this space.

# 2. Configure RedMine

This step assumes a clean install of RedMine, but nothing here should clash with any other configuration changes already made on a live system.

# 2.1 Create a new project

Each job application will be an 'issue' under this new project.  Mine is called _Job Hunting_.

_Enable the following Modules:_

* Issue tracking
* Time tracking
* Documents
* Files
* Calender

_Enable the following Tracker:_

* Feature

Save the project.

# 2.2 Add issue categories

These will be used to track the current status of the job application.  I use the normal 'Issue Status' to indicate the overall status of an application (New, In Progress, Closed).

_My categories are:_

* Investigate
* Contacted
* Resume submitted
* Initial follow-up
* Interview
* Post interview follow-up
* Accepted
* Postponed
* Rejected

# 2.3 Enable a default activity

Under **Project Settings > Activities (time tracking)**, disable all but one of the items.

# 2.4 Add a custom field

By and large, I've managed to tweak the available settings in RedMine, but one additional field has so far been necessary - the recruiter or other source from where the opportunity came.

Under **Administration > Custom Fields**, add a new custom Issue field.  Make the following changes to the configuration:

* Under name, enter 'Source'
* Tick 'Required'
* Tick 'Feature' under trackers
* Tick the Job Hunting project under available projects

# 2.5 Set up a custom query for your issues

The meaning of these fields will become apparent in the workflow section below.

Open the list of issues for the project (even if empty), and drop down the **Options** section. 

_Add the following fields to the box on the right:_

* Priority
* Subject
* Source
* Updated
* Category

Select 'Group items by category'

Click 'Save' and give your query a name.

# 3. Workflow

Now for the fun part - actually using the setup you've just created!

# 3.1 Adding a new Job

Go to the Job Hunting project page, and click on 'New Issue'.  Now complete the following fields:

* The **Tracker** 'Feature' should be selected by default
* Under **Subject**, fill in the company name, and position that the application is for (Developer, Senior Engineer, etc).  Keep it short.
* Under **Description**, add any relevant links for the job, such as the job site listing, contact details, etc.
* Keep **Status** as 'New'
* Change the **Priority** based on application importance.  If it's something you think you're very suited to, change it to 'High' so you can keep an eye on it.
* Under the **Category** list, select 'Investigate'.
* Under your custom **Source** field, add the name of the recruiter or recruiting company, job site, or friend where you got the job information from.
* If you have a document copy of the job description (other than the website), upload it under *Files*

Select **Create**.

# 3.2 Updating the job application status

Every time you do something related to your application, that information should be captured.  In RedMine, we do this under the *Log Time* function.

Select the Job Application (Issue), and click **Log Time**.  Complete the following (and leave the rest as default):

* **Hours** - how much time was spent on the activity (useful to get an idea of how much effort you're putting into specific job applications)
* **Description** - brief description of the phonecall, e-mail, interview, or anything else that might be relevant

Click **Submit**.

In addition, if the application has now changed categories, **edit** the issue, and update according to the following rationale:

* **Investigate** - A jobsite posting or lead could be interesting - investigate further
* **Contacted** - An email, phonecall, or online application has been sent
* **Resume submitted** - I've formally submitted a resume, cover letter, and any other documents that may be required
* **Initial follow-up** - I've spoken to the prospective employer about my application, and I know that it is in the system
* **Interview** - I've been invited to an interview or follow-up interview
* **Post interview follow-up** - I've been in contact after an interview, and know where I am in the system
* **Accepted** - You have been offered the job
* **Postponed** - The employer has temporarily put their recruiting drive on hold
* **Rejected** - Your application has been turned down (be sure to mention a reason)

Also change the **Issue Status** to 'In Progress'.

If any documents have been submitted (cover letters, references, etc), attach copies to the issue.  This is useful if you need to quickly find what exactly you've sent to the prospective employer.

# 3.3 Viewing your applications

There are two ways to see 'at a glance' what's been happening in your job hunting process:

The custom query that you created will order (by category, ie application status) your applications in the **Issues** view.  Here you can see:

* All the jobs you've applied for, and your progress in each one
* When the last time was that you changed anything on an application (useful to see when you might need to ping someone)
* Who the recruiter is that you need to contact about a specific job

Clicking on a specific application, you can see the information you initially entered or updated, as well as the following:

* A history of changes (job status, documents uploaded, additional information added)
* By clicking on **Spent time**, you will see a history of contacts made with regards to the application (specifically, dates and times, and the comments you added every time you logged time on the application)

# 3.4 I've found a job!

Great!  Log time to the application, change its status, and use your application list (as a courtesy) to let other prospective employers know that you've been snared.

Hang on to the project though, since it will be useful next time you start job hunting, to see who you've applied to, where in the system you were with them, why you may have been rejected, etc.

# 4. What next?

There are obviously still things that can be improved in the workflow, but these are partially limited to the functionality provided by the issue tracker.

Some applications may require very specific actions.  By and large, the above setup has proven to be reasonably robust for me, but it is pretty easy to modify without impacting existing information.

Feel free to leave any comments or suggestions.  I'd also be really happy to hear if this helps someone to take the drudgery out of job hunting.

_Roelof_