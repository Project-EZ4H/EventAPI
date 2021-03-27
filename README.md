# EventAPI
a simple event api for minecraft development
~~~xml
<repository>
  <id>EZ4H-repo</id>
  <url>http://repo.liulihaocai.pw/</url>
</repository>

<dependency>
    <groupId>me.method17</groupId>
    <artifactId>EventAPI</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
~~~

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

### Cancellable Event
use **event.setCancelled()** to set event to cancelled  
or use **event.setCancelled(boolean stage)** to change cancel stage  
and use **event.isCancelled()** to check is the event cancelled
~~~java
@EventHandler
public void onEvent(TestCancellableEvent event){
    event.setCancelled((Math.random()>0.5)?true:false);
    if(event.isCancelled()){
        System.out.println("Event Cancelled!");
    }
}
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
