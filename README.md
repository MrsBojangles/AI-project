# AI-project
This is my AI project of the Building AI course 

# Knee pain workout planner

## Summary

The idea of this project is to help users schedule a workout that is safe for their knees and can help them recover from their injury building strength and stability. The app should be able to predict the safety of new exercises using a logistic regression model. Moreover, I would like it to have improve overtime using feedback from the user.

## Background

I played volleyball for many years and I work part-time as a yoga teacher. Knee pain was one of the most common problems among volleyball players and is a fairly common issue for many of my clients as well. Of course professional athletes can easily receive the necessary assistance to adapt their workout schedule when they're affected by knee pain, but for amateurs or people who just exercise to stay healthy seeking professional help can take time and an extra effort that they might not be willing to put in. So they either stop exercising all together or they end up doing it unsafely. This app can provide a solution for this and help them maintaining their workout routine while keeping their knees healthy.

## How does it work?

The data our app will need is a list of exercises with certain features. Here's an example of how the data set will look like.

| Exercise Name     | Target Area   | Knee Pain Safe | Requires Equipment | Intensity | Notes                         |
| ----------------- | ------------- | -------------- | ------------------ | --------- | ----------------------------- |
| Glute Bridge      | Glutes/Core   | Yes            | No                 | Low       | Keep knees aligned            |
| Wall Sit          | Quads         | No             | No                 | Medium    | Puts pressure on knees        |
| Seated Leg Raise  | Quads         | Yes            | No                 | Low       | Good for strengthening safely |
| Step-Up (low box) | Glutes/Legs   | Caution        | Step or box        | Medium    | Avoid if pain > 3             |
| Chair Yoga Twist  | Mobility/Core | Yes            | Chair              | Low       | Promotes mobility             |


When opening the app, the user will be asked to input the following data.

Pain level (scale 1–10)
Goal (strength, flexibility, mobility)
Equipment available
Time per session
Days per week

So our app will select only suitable exercises for the user. The psuedo-code will be something like this:

```
if pain_level >= 7:
    exclude all exercises marked "medium" or "high" intensity
    exclude any exercise requiring knee flexion > 90 degrees
elif pain_level >= 4:
    include only low-impact exercises marked "knee-safe"
else:
    include low + medium intensity exercises marked as "low flexion" or "caution"

if goal == "mobility":
    prioritize exercises tagged "mobility"
elif goal == "strength":
    prioritize "glute", "core", "hip stability" exercises

if no equipment:
    exclude exercises with equipment_required == True
```
The output will then be a personalized plan after the application of the rules.

We would then like our app to be able to establish whather an exercise is safe or not based on its other features. To this end, we could train a logistic regression model.

There is one more feature that I would really like to add to my app and this is the ability to adapt to feedback. Ideally, I would like to collect feedback from the user to then retrain the model including this new information.
    


## Data Source and AI method

The data can be obtained from health organizations (NHS has a selection of exercises for example) and physical therapy or sports blogs. At least at this stage, the data would be manually tagged.

The logic of the app was presented in the above paragraph. In  particular, I would like to use the logistic regression model that I learnt from the course.

## Challenges

There is the danger that the app could be used as a replacement for consulting a medical professional. Clearly, this can become problematic when the injury requires a prompt medical treatment or when rest is absolutely necessary to recover fully. Another issue is that, while using the app, the user cannot receive corrections and might do the exercises incorrectly and therefore unsafely.

## What next?

An idea to face the challenges I presented would be to team up with medical professionals to improve the app. A very useful development would be to add a "proposed diagnosis" as the user answers the initial questions. This might be difficult to implement, so an easier step to help in this direction would be to send a notification to the user suggesting to consult a doctor when they report particularly a particularly high level of pain following the exercise session. 
As for corrections, I don't think there's an easy fix for that: it is probably extremely difficult to make our app able to recognize whather the user is doing the exercises correctly. If, however, the app was used under the supervision of a physiotherapist for example, we could require that the user has to record themselves performing an exercises and receive feedback from the physiotherapist before moving forward with his workout plan.

## Acknowledgements

I would like to thank all the friends with whome I share the passion for sport. Their stories and their support were the reason why I came up with such a project.


