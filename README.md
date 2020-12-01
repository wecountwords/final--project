# CSCI-33a Final-Project Proposal

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
* W3Schools HTML, CSS, and JavaScript references
  - https://www.w3schools.com/
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
