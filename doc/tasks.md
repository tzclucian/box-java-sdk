Tasks
=====

Task objects represent a user-created task on a file.

* [Get a Task's Information](#get-a-tasks-information)
* [Get the Tasks on a File](#get-the-tasks-on-a-file)
* [Add a Task to a File](#add-a-task-to-a-file)
* [Update a Task's Information](#update-a-tasks-information)
* [Delete a Task](#delete-a-task)
* [Get a Task's Assignments](#get-a-tasks-assignments)
* [Add a Task Assignment](#add-a-task-assignment)
* [Update a Task Assignment](#update-a-task-assignment)
* [Delete a Task Assignment](#delete-a-task-assignment)

Get a Task's Information
------------------------

Calling [`getInfo()`][get-info] on a task returns a snapshot of the task's
info.

```java
BoxTask task = new BoxTask(api, "id");
BoxTask.Info info = task.getInfo();
```

[get-info]: http://opensource.box.com/box-java-sdk/javadoc/com/box/sdk/BoxTask.html#getInfo()

Get the Tasks on a File
-----------------------

You can get all of the tasks on a file by calling the
[`getTasks()`][get-tasks] method.

```java
BoxFile file = new BoxFile(api, "id");
List<BoxTask.Info> tasks = file.getTasks();
```

[get-tasks]: http://opensource.box.com/box-java-sdk/javadoc/com/box/sdk/BoxFile.html#getTasks()

Add a Task to a File
--------------------

A task can be added to a file with the [`addTask(String, String, Date)`][add-task]
method.

```java
BoxFile file = new BoxFile(api, "id");
Date dueAt = new Date();
file.addTask("review", "Please review this file.", dueAt);
```

[add-task]: http://opensource.box.com/box-java-sdk/javadoc/com/box/sdk/BoxFile.html#addTask(com.box.sdk.BoxTask.Action,%20java.lang.String,%20java.util.Date)

Update a Task's Information
---------------------------

The message of a task can be changed with the
[`updateInfo(BoxTask.Info)`][update-info] method.

```java
BoxTask task = new BoxTask(api, "id");
BoxTask.Info info = task.new Info();
info.setMessage("An edited message.");
task.updateInfo(info);
```

[update-info]: http://opensource.box.com/box-java-sdk/javadoc/com/box/sdk/BoxTask.html#updateInfo(com.box.sdk.BoxTask.Info)

Delete a Task
-------------

A task can be deleted with the [`delete()`][delete] method.

```java
BoxTask task = new BoxTask(api, "id");
task.delete();
```

[delete]: https://box.github.io/box-java-sdk/javadoc/com/box/sdk/BoxTask.html#delete()

Get a Task's Assignments
------------------------

Retreive a tasks assignments with the [`getAssignments()`][get-assignments] method.

```java
BoxTask task = new BoxTask(api, "id");
task.getAssignments();
```

[get-assignments]: https://box.github.io/box-java-sdk/javadoc/com/box/sdk/BoxTask.html#getAssignments()

Add a Task Assignment
---------------------

An assignment can be added to a task with the [`addAssignment(BoxUser)`][add-assignment] method.

```java
BoxUser user = new BoxUser(api, "user-id")
BoxTask task = new BoxTask(api, "id");
task.addAssignment(user);
```

[add-assignment]: http://opensource.box.com/box-java-sdk/javadoc/com/box/sdk/BoxTask.html#addAssignment(com.box.sdk.BoxUser)

Delete a Task Assignment
------------------------

An assignment can be deleted from a task with the [`delete()`][delete-assignment] method on a `BoxTaskAssignment` instance.

```java
BoxTaskAssignment taskAssignment = new BoxTaskAssignment(api, "id");
taskAssignment.delete();
```

[delete-assignment]: http://opensource.box.com/box-java-sdk/javadoc/com/box/sdk/BoxTaskAssignment.html#delete()

Update a Task Assignment
------------------------

A task assignment can be updated with the [`updateInfo(BoxTask.Info)`][update-assignment] method.

```java
BoxTaskAssignment taskAssignment = new BoxTaskAssignment(api, id);
BoxTaskAssignment.Info info = taskAssignment.getInfo();
taskAssignment.updateInfo(info);
```

[update-assignment]: http://opensource.box.com/box-java-sdk/javadoc/com/box/sdk/BoxTaskAssignment.html#updateInfo(com.box.sdk.BoxTask.Info)