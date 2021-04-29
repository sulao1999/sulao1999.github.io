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

Design patterns are one of the most beautiful/important elements in the software development process. Design patterns can help developers create almost complete applications quickly and easily. My [last project in the ICS 314 course](https://manoa-hunger-helper.github.io/) was to use [Meteor](https://www.meteor.com/) to create an application with a user interface, database, and interaction with the database. In this project, the design pattern provided me with the optimal solution to different kind of problems, and allow me to reuse the code in different part of the project.

The most important design pattern in this application is the Model-View-Controller design pattern. The model in the application is [collections](https://docs.meteor.com/api/collections.html) in the mongo database. The view is traverse the database and create cards or tables about the data so that users can view the data in the interface. The controller use in this application is react-router-dom.

Model example [code](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/api/menu/FoodMenu.js) :
```
this.name = 'FoodMenusCollection';
```

View example [code](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/ui/pages/AdminManageVendors.jsx) :
```
{this.props.foodmenus.map((foodmenu) => <AdminFoodMenuItem key={foodmenu._id} foodmenu={foodmenu} FoodMenus={FoodMenus}/>)}
```

Controller example [code](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/ui/layouts/App.jsx) :
```
<Route exact path="/" component={Landing}/>
```

Another very useful design pattern is the Singleton pattern, which is combined with the [Publish-Subscribe](https://guide.meteor.com/data-loading.html) design pattern (similar to the Observer design pattern). This solves the problem that the interface may display before the data is ready. If the data is not loaded before the page is displayed, it may cause an application error. This design pattern makes it easier for the program to interact with the database collection, such as shows data in interface ([view above](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/ui/pages/AdminManageVendors.jsx)) , adding, editing and deleting.

Singleton pattern example [code](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/api/menu/FoodMenu.js):
```
export const FoodMenus = new FoodMenuCollection();
```

Publish example [code](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/startup/server/Publications.js):
```
Meteor.publish(FoodMenus.adminPublicationName, function () {
  if (this.userId && Roles.userIsInRole(this.userId, 'admin')) {
    return FoodMenus.collection.find();
  }
  return this.ready();
});
```

Subscribe example [code](https://github.com/manoa-hunger-helper/manoa-hunger-helper/blob/master/app/imports/ui/pages/AdminManageVendors.jsx#L78):
```
const subscription2 = Meteor.subscribe(FoodMenus.adminPublicationName);
```

Design patterns are very helpful when developing applications. It provides a simple and good way to solve the problems that programmers may face during the development process. Design allow developer reuse the code, and ensure the reliability of the code. When reusing some code, the code size will be reduce, which makes the code become neater and more beautiful. All these factors make design patterns become very important in software development.
