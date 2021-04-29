---
layout: essay
type: essay
title: The beauty of design patterns
date: 2021-04-29
labels:
  - Design patter
  - Meteor
  - User interface
  - Database
---

Design patterns are one of the most beautiful/important elements in the software development process. Design patterns can help developers create almost complete applications quickly and easily. My [last project in the ICS 314 course](https://manoa-hunger-helper.github.io/) was to use [Meteor](https://www.meteor.com/) to create an application with a user interface, database, and interaction with the database. In this project, the design pattern provided me with the optimal solution to different kind of problems.

The most important design pattern in this application is the Model-View-Controller design pattern. The model in the application is [collections](https://docs.meteor.com/api/collections.html) in the mongo database. The view is traverse the database and create cards or tables about the data so that users can view the data in the interface. The controller use in this application is react-router-dom.

Model example [code](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/api/menu/FoodMenu.js)
```
this.name = 'FoodMenusCollection';
```

View example [code](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/ui/pages/AdminManageVendors.jsx)
```
{this.props.foodmenus.map((foodmenu) => <AdminFoodMenuItem key={foodmenu._id} foodmenu={foodmenu} FoodMenus={FoodMenus}/>)}
```

Controller example [code](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/ui/layouts/App.jsx)
```
<Route exact path="/" component={Landing}/>
```
