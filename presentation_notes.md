# Introduction

Good morning, hope you're doing well.
So I'm here to talk about what I have been doing for my final year project.

I'm first going to start off with a couple of facts to get the ball rolling.

This is a project that revolves around the topic of the overall wellbeing of students, but mostly targeted at
mental health.

So... these are two facts that I want you to keep in your minds throughout this session.
15 to 20 percent of teenagers/youth suffer from some level of mental health issues, at the same time 95% of people
are considered to be in this age group own a smartphone; basically all of them.

Taking these facts into account, a potential software solution can be created in order to help those that may
face such issues.
The software solution chosen was to provide a tool that allows tailored questionnaire/survey to be created by an "expert" which can be pushed onto subscribed students.

# Motivations

The motivations behind using such a solution are that it can help students track their wellbeing and find ways they can improve it even if they don't suffer from anything.
Another point is that people may find that they feel ashamed about the issues they suffer from, so providing an anonymous is ideal.

# Current solutions

At the moment there are a number of survey creation tools that already exist, but they don't really fit the scope of the problem.
Services such as google survey and survey monkey provide a generic approach to creating surveys, this is because of the aim to have as many people use it as possible.
Survey systems also tend to be used for marketing purposes than for specific cases such as student wellbeing.
One major disadvantage is that these services don't provide the functionality to provide tailored user feedback.

# Proposed solution

My proposal for a solution is one that allows for scorable surveys so that students can build up a score history and use that to track their wellbeing.
The way they score when responding to surveys can determine what type of help they may need and these resources would be defined by the survey creator.

# Technical specification

What would actually need to be done to actually create such an application?
The approach that I had taken included two major components.
A server application that is able to manage data in a connected database and provide an API (application programming interface) that can allow for that to occur.

A user interface, in the form of a client application, needs to consume the provided API to provide the ncessary functionality.
The UI needs to perform well (i.e. no lag) and be straightforward for people to use.
An ide behind this was to also make the code re-usable for a potential Android application in the future.

Because the idea behind this application is to target students, the software solution needs to support ways for horizontal or vertical scaling opportunities too.

# High level architecture

As far as the implementation goes, this high level architecture view should give you a general idea.
At the lowest level there is a Java SpringBoot application running that is connected to an SQL database.
The server has a number of REST api endpoints defined for managing resources related to the database.
i.e. stuff to do with surveys.

The API is consumed by the implemented REACTjs client application which is what the end user will be using.

# Security

Now it is a bit silly if anybody can do anything so restrictions need to be applied.
The main security implementation for securing access to resources via the API is with Oauth2.
Users need to provide valid credentials first before obtaining an access token to use with requests.

Decided to use Json Web Tokens with Oauth2 mostly because of there being no need to deal with sessions that way.
No sessions to manage means that the application can scale a lot more easily due to no data needing to be shared
between instance of each server.
Even if a server needs to be restarted, there's no recovery period either.

The tokens that are generated are also digitally signed with a secret that is defined only in the server application.
Helping to mitigate tokens generated elsewhere.

# Technologies

Just wing this one
