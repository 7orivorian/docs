# Events

## Define

Any object can be used as an event, but it's good practice to use standardized
event classes. Events can be small, large, simple, or very complex. Anything
goes!

A few example event classes:

```java
public class EmptyEvent {

}
```

```java
public class MessageEvent {

    private String message;

    public MessageEvent(String message) {
        this.message = message;
    }

    public String getMessage() {
        return message;
    }

    public void setMessage(String message) {
        this.message = message;
    }
}
```

```java
public class SunEvent {

    private final String description;

    public SunEvent(String description) {
        this.description = description;
    }

    public String getDescription() {
        return message;
    }

    public static class SunriseEvent extends SunEvent {

        public SunriseEvent() {
            super("The sun rises");
        }
    }

    public static class SunsetEvent extends SunEvent {

        public SunsetEvent() {
            super("The sun sets");
        }
    }
}
```

## Dispatch

To dispatch an event, call one of the `dispatch` methods defined in `EventBus`,
passing your event as a parameter:

```java
MessageEvent event = new MessageEvent("world greetings");

EVENT_BUS.dispatch(event);
```