
- main purpose is document request
- faculty is the one managing the documents
- admin is the one doing maintenance
- discuss mailbox or lalamove for courier


### 1. Products Migration Columns

I would include the auto-incrementing id and timestamps, along with a foreign key column for the category using `foreignId('category_id')->constrained()`. For the product details, I would add a string column for the name and a decimal column for the price.

### 2. Product Model Relationships

In the Product model, I will define a `category()` method that returns `$this->belongsTo(Category::class)`. Then I will add a `reviews()` method that returns `$this->hasMany(Review::class)` to handle the product feedback records.

### 3. Validation Rules

For creating a product, I would set the name as `required|string|max:255` and the price as `required|numeric`. I will also validate that the `category_id` is `required|exists:categories,id` to ensure it links to an existing category.

### 4. Blade Directive

I would use the `@csrf` directive inside the form to securely include the CSRF token. Laravel requires this protection on all POST forms so our application stays safe from cross-site request forgery.





- **The Baseline Test:** If you met her for the very first time today, knowing everything you know about her personality and who she is right now, would you actively choose to date her?
- **Obligation vs. Desire:** Are you staying because you genuinely _want_ to build a future with her, or are you staying because you feel like you _have_ to because of what you've done in the past?




```
add these new features to this mockup frontend project:

- Remake the ui/ux on new document request page that adhere to the 15 ux principles wherever needed
  
give the whole revised codebase to me in a .zip file. no need to test it if it is working. make no mistakes.
```

```
- Remake the ui/ux on new document request page that adhere to the 15 ux principles wherever needed
- How should the document type be chosen on the new request page? we will have around 40 types of documents total in different categories (transfer credential page, transcript of records, certificates, authentication, for Ched only, certified true copy of the original records, others). choose the best ux approach for that. the list is sent below so you can add it all. as for their fees, requirements, etc make mockups for it.
- Which page layout should the redesign use? Two columns: sectioned form left, sticky summary right
Add a trust cue near the Submit button, such as typical processing time? No, keep only the payment and pickup notes

Document

- True Copy of Grades
- AESAR (Automated Evaluation of Students Academic Records)

Transfer Credential Package

- Transfer Credential Package (Honorable Dismissal) Undergraduate
    - Certificate of Good Moral Character
    - Transfer Credential Certificate (Honorable Dismissal)
    - True Copy of Grades

Transcript of Records

- Transcript of Records - For Abroad OTR (Undergraduate)
- Transcript of Records - For Employment OTR (Undergraduate)
- Transcript of Records - For Evaluation
- Transcript of Records - For Evaluation (Application for Bachelor of Laws Entrance Exam)
- Transcript of Records - For Evaluation (Application for Graduate Studies)
- Transcript of Records - For International Evaluation
- Transcript of Records - For OJT
- Transcript of Records - For Professional Regulations Commission (PRC - Undergraduate)
- Transcript of Records - For Scholarship Application

Certificates

- Certificate of Class Ranking (Undergraduate)
- Certificate of Clock Hours (Undergraduate)
- Certificate of Correction of Name/Birth Date/Place of Birth
- Certificate of Eligibility (C1) for Law Students
- Certificate of English Course Taken
- Certificate of Equivalency (UAE)
- Certificate of General Weighted Average (Undergraduate)
- Certificate of Good Moral Character
- Certificate of Grading System
- Certificate of Medium of Instruction
- Certificate of Medium of Instruction (with Percentage)
- Certificate of NSTP Serial Number
- Certificate of Student Status
- Certificate of Translation to English for Filipino Students
- Certificate of Units Earned (Undergraduate)
- Course Descriptions (Undergraduate)
- Related Learning Experiences (RLE - Undergraduate)

Authentication / CAV / Apostille

- For Abroad - Undergraduate
- Certificate of Enrollment
- Certified Copy of Transcript of Records
- CHED Endorsement

For Ched Only

- Certificate of Enrollment
- CHED Endorsement
- Transcript of Records  
    Certified True Copy of The Original Records
- Academic Calendar
- Certificate of Registration
- Computerized Grades

Others
```




after defense, go immediately downstairs and get your desired technical advisor kasi mabilis maubusan ng slot

right now, isip na agad ng magiging team for capstone 1



jan 6 - enjoy the reward
jan 24 - prayer as the first option
jan 26 - just do it
jan 30 - joyful in every cirucmstance
feb 1 - keep life fresh and exciting


Gala Drawings
- pool with plantitos
- gala with disciples
- gala with icy
- national library with duke
- anniversary outing to tagaytay


John Steven Maluenda
BSIT
21


**4gb**
[1600](https://shopee.ph/Samsung-M471A5244CB0-CWE-4GB-DDR4-3200MHz-Laptop-RAM-SODIMM-1Rx16-PC4-3200AA-i.728857418.45513562721?extraParams={%22display_model_id%22%3A326172720243%2C%22model_selection_logic%22%3A3})

**8gb**
[1700](https://www.facebook.com/marketplace/item/1364081141941537/)
[3500](https://shopee.ph/SK-HYNIX-8GB-DDR4-3200MHz-Laptop-RAM-1Rx16-SODIMM-PC4-3200AA-HMA81GS6JJR8N-Fast-Reliable-i.728857418.43231833865?extraParams={%22display_model_id%22%3A431189155183%2C%22model_selection_logic%22%3A3})
[3609](https://shopee.ph/IN-Ready-Stock-Kingston-hyperx-4GB-2400mhz-2666mhz-8GB-16GB-DDR4-2133-2400-2666-3200-MHZ-SODIMM-PC4-Laptop-Memory-1.2V-260Pin-Notebook-RAM-Class-Online-Gameing-Time-i.343405469.3865772389?extraParams=%7B%22display_model_id%22%3A35794365398%2C%22model_selection_logic%22%3A2%7D)
[3609](https://shopee.ph/Kingston-HyperX-DDR4-4GB-8GB-16GB-SODIMM-260-Pin-1.2V-for-Laptop-Notebook-PC4-17000-PCD-19200-PC4-21300-PC4-24000-i.343405469.28454972166?extraParams={%22display_model_id%22%3A256172483726%2C%22model_selection_logic%22%3A2})
[3609](https://shopee.ph/Samsung-8GB-DDR4-2400Mhz-2666Mhz-2133Mhz-3200MHz-1.2V-260Pin-SODIMM-Laptop-Memory-RAM-PC4-DDR4-2400T-2666V-i.343405469.23925934209?extraParams=%7B%22display_model_id%22%3A365695461719%2C%22model_selection_logic%22%3A3%7D)
[4695](https://shopee.ph/Crucial-8GB-260-Pin-DDR4-SO-DIMM-DDR4-3200-(PC4-25600)-Laptop-Memory-(CT8G4SFRA32A)-i.89762129.17186682032?extraParams=%7B%22display_model_id%22%3A212574144016%2C%22model_selection_logic%22%3A3%7D)

**16gb**
[4959](https://shopee.ph/8GB-16GB-DDR4-LAPTOP-MINI-PC-SODIMM-RAM-USED-i.108029835.57912081845?extraParams={%22display_model_id%22%3A366167653210%2C%22model_selection_logic%22%3A3})
[4989](https://shopee.ph/8GB-16GB-DDR4-LAPTOP-MINI-PC-SODIMM-RAM-USED-i.108029835.57912081845?extraParams={%22display_model_id%22%3A366167653210%2C%22model_selection_logic%22%3A3})
[6041](https://shopee.ph/IN-Ready-Stock-Kingston-hyperx-4GB-2400mhz-2666mhz-8GB-16GB-DDR4-2133-2400-2666-3200-MHZ-SODIMM-PC4-Laptop-Memory-1.2V-260Pin-Notebook-RAM-Class-Online-Gameing-Time-i.343405469.3865772389?extraParams=%7B%22display_model_id%22%3A35794365398%2C%22model_selection_logic%22%3A2%7D)
[6041](https://shopee.ph/Crucial-DDR3-DDR4-Laptop-RAM-4GB-8GB-16GB-SODIMM-1333-1866-2666-3200MHz-1.5V-1.2V-Ready-Stock-i.343405469.9036004741?extraParams={%22display_model_id%22%3A91334359967%2C%22model_selection_logic%22%3A2})
[6041](https://shopee.ph/Kingston-HyperX-DDR4-4GB-8GB-16GB-SODIMM-260-Pin-1.2V-for-Laptop-Notebook-PC4-17000-PCD-19200-PC4-21300-PC4-24000-i.343405469.28454972166?extraParams={%22display_model_id%22%3A256172483726%2C%22model_selection_logic%22%3A2})
[6099](https://shopee.ph/Crucial-DDR4-Laptop-RAM-4GB-8GB-16GB-2133-2400-2666-3200MHz-260-Pin-SODIMM-PC4-17000-1.2V-i.306494530.4154704468?extraParams=%7B%22display_model_id%22%3A31187817509%2C%22model_selection_logic%22%3A3%7D)


intel core i5 10th gen
16gb ddr4
256gb nvme
14 fhd screen
intel uhd graphics

intel core i7 8th gen
16gb ddr4
512gb nvme
13.3 fhd screen
intel uhd graphics 620

amd ryzen 5 pro 46500 w/ radeon graphics 2.1 ghz
16gb ddr4
256gb nvme
13 fhd screen
amd radeon graphics

intel core i7 8th gen
16gb ddr4
256gb nvme
14 fhd screen
intel uhd graphics 620

intel core i7 10th gen
16gb ddr4
256gb ssd
15.6 hd screen
intel uhd graphics

intel core i5 10th gen
16gb ddr4
256gb nvme
14 fhd screen
intel uhd graphics

intel core i7 10th gen
16gb ddr4 dual channel
256gb nvme
14 fhd screen
intel uhd graphics

intel core 15 11th gen
16gb ddr4
256gb nvme
14 fhd screen
intel iris xe graphics


### Changes

- new theme 'nord night' for dark mode
- new selectors for many previously unselected elements
- fixed the dark border on navbar below the adamson logo

### Unsolved Issues

- i don't know how to apply and test in firefox
- input element color issues (form input elements are notorious for being hard to style, much less select)
- activity stream item hover

### Future Improvements

- better styling for input elements (dropdown, label, etc)
- correct the hover styling on activity stream page
- connect the nord light and dark mode themes, and then make a system default option for it


Free time: - thursday 9:00-10:30am, 5:00-6:00pm - friday 9:00-11:30am
Free time: thursday- 1:00pm onwards Friday - 10:00 hanggang 11:30am