Components and Systems are built and edited in the Components and Systems tabs. They can also be used to get more detailed information on what any given one does. Only Components that Thangs in your Level have will show up in the Components Tab.

### To See What Any Component Does

1. If it's not already on one of the Thangs in your Level, add it to one.
1. Go to the Components Tab
1. Click on the now listed Component and view its code and other details.

This is really hacky, but right now the only way to view any given Component and all its data.

### To See What a System Does

1. If it's not already added to the list of systems, add it with the 'Add System' button at the lower left.
1. Click on the now listed System and view its code and other details.

### To Build a new Component or System

1. Click 'Add New Component' or 'Add New System' on the upper right. If you're adding a new Component, include the System it depends on in lower case (so 'ai' or 'event').
1. In its settings, give it a description, name, and list dependencies on other systems or components.

### To Define a Component's Configuration

1. Read up on how [[JSON-Schema]] works. Configurations are defined with them.
1. Select the Component on the left.
1. Click 'Config Schema' on the Component pane that appeared to the right.
1. Use the Treema that appeared to edit the Component's Configuration Schema.
1. To test a config, try configuring it. See [[Editing Thang Components]].

### To Test a Component or System

1. Select the Component on the left.
1. Edit the code in the ACE editor that appeared.
1. Press Play to see what happens. Use console.log to debug. There are some limitations to logging though when running the code in the background.

### To Understand How Components and Systems Work

Explore the existing Components' code and [talk with us](http://www.hipchat.com/g3plnOKqa) for any questions you have.