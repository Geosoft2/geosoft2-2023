# Geosoftware II handout repository (WiSe 2023/24)

**Web-Tool for the supervised classification of earth observation data in OpenEO**

Teachers: [@edzer](http://github.com/edzer/), [@DaChro](https://github.com/DaChro)

[LSF/QISPOS](https://studium.uni-muenster.de/qisserver/rds?state=verpublish&status=init&vmfile=no&publishid=397467&moduleCall=webInfo&publishConfFile=webInfo&publishSubDir=veranstaltung)

[Learnweb course](https://www.uni-muenster.de/LearnWeb/learnweb2/course/view.php?id=71329)


In this repo, we collect the handouts for presentations on technical background and concepts required for this year's project task in Geosoftware II at ifgi. 
These handouts are the core of the preparation of a topic by each student/pair of students.
The handout should be prepared in a manner so that fellow students can use it as a starting point for getting up to speed on the new topics and making decisions during their project work.
The presenting students remain _experts_ on the topics for future questions and are very welcome to update the documents in this repository during the course.
Please follow the process below for creating and submitting your handouts.

**Due date**: October 11th, 2023, 14:00 hrs CET.

### Process

1. Fork this project
1. Do your research
1. Create a folder for your topic (`topic-title-no-capitals-with-hyphens-but-not-underscores`)
1. Add a file `handout.md` file in your folder
    * Take a look at the [markdown syntax](https://guides.github.com/features/mastering-markdown/)
    * Split up your work into logical sections and use informative names for each of these
    * Add any additional files needed (graphics not already available online, for example) to your folder
    * Add your GitHub username at the beginning of the document, e.g. [@DaChro](https://github.com/DaChro)
1. Add a git tag `handout-submission-<name>` and push it to your fork
1. Send a pull request before the submission deadline containing your handout (not the presentation)
    * Give the pull request a useful name and description, and @-mention all contributors in the pull request description
1. Create a presentation based on your handout (optional: add it to your folder)
1. Present at the seminar (approx. 10 minutes + 5 minutes questions and discussion)
1. Incorporate feedback from the presentation into the handout and update the pull request (don't forget to [sync your fork/merge `upstream master` beforehand](https://help.github.com/articles/syncing-a-fork/))
1. If you see an error in or want to add information to a colleague's handout ...
    1. Make a comment to the open PR if it is still open
    1. At any later point in time: make the changes yourself (fetch and merge into your fork, make the changes, send a pull request to the original author of the topic and present your changes, original author may then merge and send a PR to the main repository)
1. Teacher merges the final handout version after grading

### Evaluation

The evaluation is conducted based on the content of the handout, the presentation itself, and the discussion afterwards during the course.
Be prepared for questions by your fellow students and the teachers, but also prepare some additional content or questions yourself in case there are no comments from the audience.

### Topics & content

The goal of the project in this semester is to develop a web-based machine learning toolkit for the supervised classification of earth observation data in [OpenEO](https://openeo.org/) based on [openeocubes](https://github.com/PondiB/openeocubes). Your main tasks will include adapting/extending the existing API to enable supervised classification on the R backend and developing a simple web front-end through which the classification can be conducted and controlled (e.g., choose data, upload/digitize training data, choose hyperparameters, visualize results). Detailed information about the goals and deliverables will be communicated along with the invitation to bid at the start of the semester. 

Your presentations and handouts will serve as preparation by discussing several relevant topics that form the technical background of this project task. 

The specific topics will be posted on Wednesday, 30th August, as GitHub issues with label "Topic". Choose a topic by commenting on the respective issue. Make sure you cover at least the mentioned keywords. More is better, but only really better if you evaluate alternatives, phrase opinions, and provide guidelines for your fellow students.


