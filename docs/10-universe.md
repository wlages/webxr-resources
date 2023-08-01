---
title: Universe!
description: Step 10 - Moving earth and moon
order: 100
---

* sdfasdfs
{:toc}

# Joining the planetary systems!

In this step we will add a link to the starbase Hub, which which links together all star sytems. The only thing required is to add a new method to navigate to another webXR application.

Add the method below in the end of your script:

```javascript
function LeaveSystem(button,scene)
{
     button.actionManager = new BABYLON.ActionManager(scene);
     button.actionManager.registerAction(new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, function() {
               window.location = "https://wlages.github.io/galaxy/";

    }));
}

```

This is linking to my GitHub [Galaxy Page](https://wlages.github.io/galaxy/), which reads from a database with the star systems.


As usual, you will need to call this method from "CreateScene". Add it before "return scene;":

```javascript
LeaveSystem(earth,scene);
```

Before you leave to explore the galaxy, [add your planetary system here](https://airtable.com/invite/l?inviteId=invsMHG1BObOw5qOj&inviteToken=ba576f860149d12329391f413eb6a27902517ae46facfa7b17a62d9bab984af7&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts)

To leave the system, point with your controller to the ground and press trigger.

# Explore

Try other planetary sytems! Find out who is the creator and give some feedback!

Here is the [complete project for this step](https://playground.babylonjs.com/#EQHLXS#9).