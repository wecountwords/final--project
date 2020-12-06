# CSCI-33a Final-Project: WeCountWords, a Django App

### Concept
WeCountWords (WCW) is a virtual writing productivity coach to help writers establish and maintain a daily writing habit. By establishing a habit or practice of writing, writers increase their productivity and ability to complete their projects. WCW helps writers establish writing goals, track progress against their goals, and analyze their progress through data visualizations. In addition, writers are supported through curated content on regional conferences, national organizations, and other articles on the business of writing.

WeCountWords, for the purposes of the final project, is the application framework to support the concept. It is the first iteration beyond the prototype and will serve as the foundation for the first iteration of the publically available app. To this end, the focus on the final project has been three-fold:
1. Setup a backend for content developers to easily add, update, and remove WCW content: wcw content developer app
1. Build the first iteration of a working member site such that a member will register, setup a basic profile, and begin tracking their writing productivity via the daily word count
1. Build the first iteration of teh selected content section of the site (now named curated content) for both WCW members and non-members

### Project Proposal vs. Outcome: GOOD (what will be accomplished no matter what)
1. Basic member site including a member page with 2 data visualizations updated real-time with word counts - DONE
   - Members are able to add their daily word count before or after login
   - Upon login, members are presented with 2 writing visualizations for tracking their progress and analyzing days they are most productive
   - Each time the member accesses their page, data is retrieved to update the Total Words table
   - The Words Written by Day of Week visualization is historical. It changes each day rather than each time a member adds words. This is an implementation decision to enhance the usefulness to the writer.
   - Both visualizations are drawn using Google Charts (https://developers.google.com/chart)
1. Profile page for users to setup their writing goals - DONE
   - Members are presented with their profile page when they first register on the site and any time after when they click on their username in the top menu bar
   - Members set their writing goals for words per day and days per week (required)
   - Member also have the option to add a first and last author nae or update their email address
1. Selected contect page (Curated Content) - DONE
   - The name of the selected content section has changed to Curated Content.
   - This page is populated with links to relevant organizations, conference, blogs, tools, and so on
   - For the purposes of the project, the important aspects are content layout and ability to populate content from the content development site. 
1. Basic content developer site to add content (textual only) to the database that will then be published to the Curated Content section of the member site - DONE
   - From the top nav bar, content developers are able to navigate to various forms to submit new content. 
   - Add New Event form adds an events that is then published on the member site.
   - Add URL form submits URLs that are then published in the Curated Content section of the member site.
   - Add New Article form adds an blog article to the database. Blog content pages on member site are out of scope for the final project.
   - Update New This Week form submits the intro to the Currated Content Page
  
### Project Proposal vs. Outcome: BETTER (what do I think can be accomplished in addition to the GOOD features)
1. On the content developer site: new landing page with a list of existing content and its current state (Saved, Published, Archived) - DONE
   - http://127.0.0.1:8000/console
   - WC Console landing, click on any of the 4 categories: URLs, Event, Articles, Archived Items, to go to the title and state for that article
1. Ability to select any unpublished item from teh list and take the following actions: edit, save, publish, archive (soft-delete)
  - URLs - DONE
    - By design, URLs are not editable. You can "Remove" one from the member site, thereby archiving it.
    - By design, URLs are published directly to the site upon submitting a new URL
  - Events - NOT DONE
  - Articles - NOT DONE
1. Ability to select a published content from the list, movit it to a Saved state thereby removing it from the published content on the site
   - URL - DONE
     - from the URL list in the WCW Console, select any URL and then use the Remove option to archive it
     - archived URLs are excluded from those that are available to the member site
   - Events - DONE
     - from the Event list in the WCW Console, select any event showing as published, and then use the Remove option to archive it
     - archived Events are excluded from those that are available to the member site
   - Articles - DONE
     - from the Article list in the WCW Console, select any article showing as published, and then use the Remove option to archive it
     - archived Articles are excluded from those that are available to the member site
  
### Project Proposal vs. Outcome: BEST (what I hope to accomplish in addition to the GOOD and BETTER features )
1.  Add the Daily Word Count in calender format -  not attempted due to time constraints. 

### Additional requirements from final project slide deck


Outlines of Parts
1. WeCountWords description of purpose and audience
1. Frontend vs. Backend
1. User Journey Map
1. Backend: input content and updcoming events
1. Frontend: each user will have a member page and profile page profile page. All members and non-members have access to Selected Content.

### Milestones

### Development Stack
* Django, Python, JavaScript, HTML, CSS

### Prototype
* https://www.wecountwords.com

### Application Specification
* Profile Page
  - Upon registration, a member is taken to their profile page where they will add their writing goals and author name for their current project.
  - Members are required to add a goal for (1) number of words per writing session they will commit to writing and (2) number of days each week they will commit to writing each week.
  - Members have the option of putting in a first and last name for the writing project
  - Members can change the email associated with their account.
  - In addition, the profile page will display a default project name: <username> Project 1.
  - Once the required information has been added adn successfully saved, members are able to navigate to their project landing page.
  - The member must be logged-in to access the profile page.
  - Open items to be implemented in the future (not included in the final project): changing passwords, adding more than one project, communication preferences for reminders and emails

### Implementation Notes: WeCountWords console for content developers
* Add new Artiles, Events, or URLs
  - _Add_ links at the top of the page ad a new content item to the datastore
  - Open item: to edit a pre-published content item, navigate to _Articles and Events for Editing_ list and select the item to edit. 
  - Content items are not editable after they are published. Links are not editable after they are submitted to the datastore.
  - Open item: delete content item
* Member Profile Page
  - Project name is not editable. Non-paying members have one project with a name of the form "<username> Project 0". Selecting and hosting multiple writing projects is an open item for a future iteration.
   

### References
* CSCI E-33a course lecture, notes, and past assignments
* Django documentation and Python documentation
  - https://docs.djangoproject.com/en/3.1/
  - https://docs.python.org/3/
* W3Schools HTML, CSS, and JavaScript references including JavaScript regular expression references
  - https://www.w3schools.com/
  - https://developer.mozilla.org/en-US/docs/Web
* How to share data between Django Apps
  - https://stackoverflow.com/questions/42424955/how-to-exchange-data-between-apps-in-django-using-the-database
* Google Charts
  - https://developers.google.com/chart/interactive/docs
* API Design and Naming Conventions
  - https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/
  - https://cloud.google.com/apis/design/naming_convention
* Fonts
  - https://fonts.google.com/specimen/Special+Elite?query=special#standard-styles
* HTML validation reference
  - https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#the-constraint-validation-api
* Python date functions
  - https://stackoverflow.com/questions/32490629/getting-todays-date-in-yyyy-mm-dd-in-python
  - https://stackoverflow.com/questions/441147/how-to-subtract-a-day-from-a-date
