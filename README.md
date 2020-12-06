# CSCI-33a Final-Project: WeCountWords, a Django App

### Concept
WeCountWords (WCW) is a virtual writing productivity coach to help writers establish and maintain a daily writing habit. By establishing a habit or practice of writing, writers increase their productivity and ability to complete their projects. WCW helps writers establish writing goals, track progress against their goals, and analyze their productivity through data visualizations. In addition, writers are supported with curated content on regional conferences, national organizations, and content on the business of writing.

WeCountWords, for the purposes of the final project, represents the application framework to support the concept. It will serve as the foundation for the first iteration of a publically available app. To this end, the focus of the final project is three-fold:
1. Setup a backend for content developers to easily add WCW content: wcw content developer app at http://127.0.0.1:8000/console on the django dev server
1. Build the first iteration of a working member site such that a member will register, setup a basic profile, and begin tracking their writing productivity via the daily word count: http://127.0.0.1:8000 on the django dev server
1. Build the first iteration of the selected content section of the site (now named curated content) for both WCW members and non-members

### Project Proposal vs. Outcome: GOOD (what will be accomplished no matter what)
1. Basic member site including a member page with 2 data visualizations updated real-time with word counts - DONE
   - Members are able to add their daily word count before or after login.
   - Upon login, members are presented with 2 writing visualizations for tracking their progress and analyzing days they are most productive.
   - Each time the member accesses their page, data is retrieved to update the Total Words table.
   - Words Written by Day of Week, as a historical view, changes each day rather than each time a member adds words. 
   - Data visualizations are drawn using Google Charts (https://developers.google.com/chart)
1. Profile page for users to setup their writing goals - DONE
   - Members are presented with their profile page when they first register on the site and any time after when they click on their username in the top menu bar once logged in.
   - Members set their writing goals for words per day and days per week.
   - Member have the option to add a first and last author name or update their email address.
1. Selected content page (Curated Content) - DONE
   - The name of the selected content section has changed to Curated Content.
   - This page is populated with links to relevant organizations, conference, blogs, tools, and so on.
   - For the purposes of the project, the important aspects are content layout and ability to populate content from the content development site. 
1. Basic content developer app - DONE
   - Content developers are able to add content (textual only) to the database that will then be published to the Curated Content section of the member site.
   - From the top nav bar, content developers are able to navigate to various forms to submit new content in the form of URLs, event listings, or blog articles.
   - Update New This Week form gives conent developers the ability to add an intro title and text to the Curated Content section of WCW.
  
### Project Proposal vs. Outcome: BETTER (what do I think can be accomplished in addition to the GOOD features)
1. On the content developer app: landing page with a content list and current state (saved, published, archived) - DONE
   - Category list added to the landing page with the following selections: URLs, Events, Articles, Archived Items. Click on any of the categories opens a list of content of that type with the current state.
1. Ability to select any unpublished item from the list and take the following actions: edit, save, publish, archive (soft-delete)
  - URLs - DONE
    - By design, URLs are not editable. By design, URLs are published directly to the content site and do not go through a save / edit phase.
    - You can "Remove" one from the member site, thereby archiving it.
  - Events - NOT DONE
  - Articles - NOT DONE
1. Ability to select a published content from the list, move it it to a Saved state thereby removing it from the published content on the site - DONE
   - Only content items in a published ("p") state are make available to the content site.
   - URLs are published on submit. Use the Remove option to put it into an archive state.
   - Events and Articles are either saved, published, or archived. 
     - If the current state is published, set the new state to Saved to remove it from the site. 
     - From a saved state, the content item can be resaved, archived, or published
  
### Project Proposal vs. Outcome: BEST (what I hope to accomplish in addition to the GOOD and BETTER features )
1.  Add the Daily Word Count in calender format -  not attempted due to time constraints. 

### Project Details for the Django _wecount_ project
Apps in the _wecount_ project: 
1. _words_: public facing member app for WeCountWords
1. _wcconsole_: content developer app to support the member app
1. _Django admin_ console: supports user admin 

### Other notes:
1. Full authentication and authorization is not yet fully implemented. Registration and login is managed on the member site. This is to test member dependent features.
2. For the content developer site, login is through the member site. Logout is ok from either site. 

### Files: models, urls.py, admin.py, setting.py
wecount > urls.py : contains the top-level url patterns for WeCountWords WCW Console, and the Django admin app
> page:  path('', include('words.urls')),
> path('console/', include('wcconsole.urls')),
> path('admin/', admin.site.urls),
    
wcconsole > urls.py : contains the url paths for the contend developer site.
> View paths
> path("", views.index, name="console"),
> path("faq", views.faq_view, name="console_faq"),
> path("logout", views.logout_view, name="console_logout"),

> API paths
> path("article", views.article, name="article"),
> path("event", views.event, name="event"),
> path("submiturl", views.submiturl, name="submiturl"),
> path("url/<int:urlid>", views.get_url_by_id, name="get_url"),

1. words > urls.py : contains the url paths for the main member app
    View paths
    path("", views.index, name="index"),
    path("project/<str:username>", views.project_view, name="project"),
    path("lists", views.content_view, name = "content"),
    path("profile", views.profile_view, name = "profile"),
    path("login", views.login_view, name="login"),
    path("logout", views.logout_view, name="logout"),
    path("register", views.register, name="register"),

    API paths
    path("profile/<int:userid>", views.update_profile, name="update_profile" ),
    path("profile/<int:userid>/member", views.update_member, name="update_member"),
    path("wordcount", views.word_count, name="word_count" ),
    path("wordcount/<int:userid>/byweekday", views.totals_by_weekday, name="totals_by_weekday"),
    path("wordcount/<int:userid>/intervals", views.totals_by_interval, name="totals_by_interval"),

1. wecount > settings.py
   added to the INSTALLED_APPS
       'words',
      'wcconsole',
   added the wecount.url to the ROOT_URLCONF
      ROOT_URLCONF = 'wecount.urls'
   set the user authentication model
      AUTH_USER_MODEL = 'words.User'
 
1. Django admin is setup on words (member site) app and supports users and user profile. Anything direct model access for content items, other models in either app, is being handled via the django shell app. Intent is that users can be managed through a UI if necessary. Everything else should not need a backend UI to view or manipulate it. If it does, the same admin should be able to successfully handle this through the command line shell.
 
1.  








### Additional requirements from final project slide deck

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
