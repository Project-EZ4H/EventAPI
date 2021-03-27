# EventAPI
a simple event api for minecraft development
## Usage
### Create Event
create a new class and implements **Event**
~~~java
import me.method17.eventapi.events.Event;

public class TestEvent implements Event {
~~~
if u want a cancellable event plz extends **CancellableEvent**
~~~java
import me.method17.eventapi.events.CancellableEvent;

public class TestEvent extends CancellableEvent {
~~~

### Call Event
*new* an event object and use EventManager to call it
~~~java
import me.method17.eventapi.EventManager;

EventManager.callEvent(new TestEvent());
~~~

### Listen an Event
first create a class extends **Listener**
~~~java
import me.method17.eventapi.listener.Listener;

public class TestListener extends Listener {
~~~
listener will register automatically  
then create a method with annotation **@EventHandler**
~~~java
import me.method17.eventapi.events.EventHandler;

@EventHandler
public void onEvent(TestEvent event){
    //code...
}
~~~
