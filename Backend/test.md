Objectives & Scope
Validate that the MVP meets functional requirements (search, details, enquiry), data validation rules, business logic (publish/unpublish, role‑based access), and basic non‑functionals (responsiveness, accessibility checks, performance smoke).

Test Types & Approach
Functional/UI: filters, navigation, forms, CRUD flows.
Data validation: required fields, formats, ranges; clear error messages.
Business logic: listing status workflow; role permissions (Admin/Agent/Buyer).
Compatibility/responsiveness: modern desktop + mobile widths (≥ 360px).
Accessibility (basic): keyboard focus, alt text for images, labels for form fields.
Performance (smoke): listings pages paginate; images optimised; LCP target < 3s on staging.
Security (basic): auth protection on dashboards; server‑side validation; no sensitive data in client logs.

UAT Test Cases (Representative Set)
ID	Title	Actor	Preconditions	Steps	Test Data	Expected Result	Owner	When	How/Tools
UAT‑01	Filter listings by suburb+price	Visitor	Listings exist across suburbs and prices	1) Open Listings  2) Select 'Tarneit'  3) Set price < $700k  4) Apply	Suburb: Tarneit; Price < 700k	Results show only Tarneit under $700k; count updates; pagination intact	QA Lead	Day 2	Manual UI
UAT‑02	View property details	Visitor	At least one property matching filters	1) Click a result card  2) Switch gallery image  3) Open Map tab	N/A	Details page renders key facts; gallery and map work	QA Lead	Day 2	Manual UI
UAT‑03	Submit enquiry with validation	Visitor	On details page	1) Leave required fields empty  2) Attempt submit  3) Fill valid data  4) Submit	Name, Email, Message	Inline errors appear for invalid; success confirmation on valid; enquiry saved	QA Lead	Day 2	Manual UI
UAT‑04	Request inspection	Visitor	Details page; inspection form enabled	1) Open Request Inspection  2) Choose date/time  3) Submit	Preferred date/time	Request recorded; agent notified (sandbox email)	QA Lead	Day 2	Manual UI
UAT‑05	Agent login (auth)	Agent	Agent user exists	1) Open login  2) Enter valid creds  3) Submit  4) Logout	agent@example.com / ****	Successful login redirects to dashboard; invalid creds show error	Agent	Day 3	Manual UI
UAT‑06	Create & publish listing	Agent	Logged in as Agent	1) Open Create Listing  2) Fill required fields  3) Upload images  4) Publish	Title, price, address, beds/baths, amenities, images	Listing visible on public site when status=Published	Agent	Day 3	Manual UI + images
UAT‑07	Manage listings status	Agent	Agent has multiple listings	1) Open Manage Listings  2) Unpublish one  3) Archive one	N/A	Unpublished hidden publicly; archived hidden from agent defaults	Agent	Day 3	Manual UI
UAT‑08	View enquiries & mark read	Agent	Enquiries exist	1) Open Enquiries  2) Open latest enquiry  3) Mark as Read	N/A	Detail panel shows message/contact; status updates to Read	Agent	Day 3	Manual UI
UAT‑09	Admin users & roles	Admin	Admin account exists	1) Add user  2) Assign Agent+Buyer roles  3) Save  4) Login as the new user	Name/email; roles	User can access only permitted sections by role	Admin	Day 4	Manual UI
UAT‑10	Admin master data	Admin	Amenities/types list available	1) Add a new amenity  2) Deactivate an old one	Amenity name	New amenity appears on listing form; deactivated hidden from new selections	Admin	Day 4	Manual UI
UAT‑11	NLP search parsing	Visitor	Dictionary seeded with common suburbs/amenities	1) Enter '3‑bed under $700k in Tarneit with parking'  2) Submit	NL query text	Filters auto‑populate: beds=3, price<700k, suburb=Tarneit, amenity=parking	QA Lead	Day 2	Manual UI
UAT‑12	AI reply drafting	Agent	Enquiry exists; AI module enabled (sandbox)	1) Open enquiry  2) Generate draft  3) Regenerate	Enquiry body sample	Draft references property facts; no PII leaked; regenerate produces variation	Agent	Day 3	Manual UI

