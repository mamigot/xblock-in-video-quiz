In Video Quiz XBlock ![BS] ![CA]
================================

This XBlock allows for edX components to be displayed to users inside of videos at specific time points.

Installation
------------

Install the requirements into the python virtual environment of your
``edx-platform`` installation by running the following command from the
root folder:

```
$ pip install -r requirements.txt
```

Enabling in Studio
------------------

You can enable the In Video Quiz XBlock in Studio through the
advanced settings.

1. From the main page of a specific course, navigate to
   ``Settings ->    Advanced Settings`` from the top menu.
2. Check for the ``advanced_modules`` policy key, and add
   ``"invideoquiz"`` to the policy value list.
3. Click the "Save changes" button.

Usage and configuration
-----------------------

#### In Studio (CMS):

For this xblock to function properly, the course author must add to the unit:

a video to be played
a problem to pop up at a specific time moment (or several problems)
an in-video-quiz xblock (from the list of advanced components)
(see the screenshot below).

![Studio Unit view](/doc/img/invquiz-unit.png)

The `in-video-quiz block` **must** be edited as follows:

- the very last part of `Component Location ID` of the Video block (not the `Video ID`!) should be copied from the settings of the video and pasted into "Video ID" field.
- the very last part of `Component Location ID` of the Problem block should be copied from the settings of the
corresponding problem(s) and inserted into the dictionary-like JSON structure in the 'Problem Timemap' field (see the screenshot below).
- blocks order within the Unit matters (`in-video-quiz block` must follow after the video block and problems / quizes).

![Studio xBlock Editor view](/doc/img/invquiz-editor.png)

NOTE: The key "5" in the dictionary corresponds to the 5th second (0:05) of the video.

#### In LMS:

When a student is logged in, only the video is displayed initially:

![LMS Student view](/doc/img/invquiz-lms-view.png)

At the time moment indicated by the course author in the `in-video-quiz xblock` settings (5th second in this example), the video is paused and is replaced by the quiz (problem):

![LMS Student quiz view ](/doc/img/invquiz-lms-continue.png)

NOTE: The video can be resumed by pressing the 'Continue' button.

When a staff member is logged in, the video is displayed along with the problem(s) to be shown in it. Each problem is supplied with indication of the time moment, when it appears in the video:

![LMS Staff view](/doc/img/invquiz-lms-staff-view.png)

Package Requirements
--------------------

setup.py contains a list of package dependencies which are required for this XBlock package.
This list is what is used to resolve dependencies when an upstream project is consuming
this XBlock package. requirements.txt is used to install the same dependencies when running
the tests for this package.

License
-------

The In Video Quiz XBlock is available under the AGPL Version 3.0 License.


[BS]: https://travis-ci.org/Stanford-Online/xblock-in-video-quiz.svg

[CA]: https://coveralls.io/repos/Stanford-Online/xblock-in-video-quiz/badge.svg?branch=master&service=github
