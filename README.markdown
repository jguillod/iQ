iQ — The Dynamic, Structured and Easy Form JS Library
====================================================

©2011-5 by [iMed Edition](http://www.imed-edition.net) and [Joël Guillod](mailto:joel.guillod@gmail.com)

**Notice : there are many projects to build web forms from JSON schema.**

The iQ project aimed at building complex web forms and managing forms data. The base engine is written in javascript and the default adapter for user interface (GUI) uses the ExtJS 4 library.
[iMed Edition](http://www.imed-edition.net/iq) main goal is to provide a simple but complete tool for defining forms, capturing, rendering and analyzing patient healthcare data (EHR). Any application domain which manages forms could benefit from this project.

The complete lifecycle of a form and its content is addressed by iQ and can be schematized as&nbsp;:
![this figure](http://www.imed-edition.net/iq/img/iq_overview.png "Overview")

Definition of concepts
----------------------
*(If you'd like to suggest better terms naming, [please do submit proposals with argumentation](https://github.com/jguillod)!)*
### 1. The Authoring Phase

An author is responsible to maintain the definition and semantics of Forms, Sections, Questions and their Dimensions, Rules, and Templates.

* **Form** : a form is a questionnaire composed of { sections, questions, reports }. Filling a form may be questions in sequence or in random and the collected data is named the *Form Response*. The reports items of a form are read only sections of a linked response form.
* **Section** : a section belong to a questionnaire and is itself a questionnaire, i.e. subform.
* **Question** : a question is an observation about a given subject. It is composed of a set of given properties (dimensions) which characterizes the subject.
* **Dimension** : a dimension is a characteristic of an object and belongs to a question or another dimension. A dimension can take a predefined set of typed values. Sample types are: quantity, unique and multiple choices, date, …
* **Template** : is the definition to produce a report from a Form Response.
* **Rule** : a rule is used to constrain the user in filling the values in a form. The following rules may apply:
  * **Sequence rule** : used in a sequential form to define the path from one answer to the next question.
  * **Composition rule** : used to dynamically change the set of questions in a form.
  * **Coherence rule** : reflects a constrains between the dimension values in a form. Its invocation results in the following actions:  
    IF (predicate) THEN (set a value)  
    IF (predicate) THEN (alert)

The authoring tool outputs *forms* and *questions* definitions in a normalized [JSON](http://www.json.org) [schema](http://tools.ietf.org/html/draft-zyp-json-schema-03). Other implementations (xml, …) will need a specific adapter.


![this figure](http://www.imed-edition.net/iq/img/question_anatomy.png "Question Anatomy")

### 2. The Filling Form Phase


The user fills a chosen form as usual in a web page. The product of this phase are: Values, Answers, Response.

* **Value** : a value is the data given by the user to a Dimension.
* **Answer** : an answer is the set of values a user has given to a Question.
* **Form Response** : the response is the set of answers given to a Form.

When filling a form events automatically trigger the execution of appropriate rules.

### 3. The Reporting Phase

* **Report** : a report is a formatted document as the result of applying a Response to a Report Template&nbsp;:  
  Report = ƒ( Template, Form_Response)

User interface
--------------

The authoring phase is not discussed here. The basic way to defined forms is writing a JSON file according to the definition schema.

During the user filling form phase we propose to display some areas:

* The mandatory **Data Capture widget**.
* An optional **Context widget** to link answers to some contextual data (e.g. a medical problem in the SOAP oriented record).
* An optional **Browser widget**, the form table of content, i.e. the tree with titles of Sections and Questions. Color flags could show the states of answers.
* An optional **Report widget** to display the result of the response so far in real time.

![this figure](http://www.imed-edition.net/iq/img/iq_gui.png "User interface areas")

Amazing Features
----------------
Because Q/A values are coded **automatic translation** in other languages is a feature of iQ.

Various manipulations on the Q/A sets are included to **assist the user** during data capture. For instance in EHR iQ will enhance the patient encounter experience and the data quality and completion. User draws a differential diagnosis and then iQ dynamically composes the Form! More to say... stay tune.

* * *
Update: Mon Jul 04 2011 23:02:10 GMT+0200 (CEST)
update Thu Jul 16 2015 18:44:22 GMT+0200 (CEST)

See also: [iQ on Github](https://github.com/jguillod/iQ)

(c) Copyright 2011-12 by [iMed Edition](http://www.imed-edition.net) and [Joël Guillod](joel.guillod@me-com). All Rights Reserved.
