# Event Types

## Status Event

A status event can be suppressed or terminated, and the `StatusEvent` class and
`IStatusEvent` interface provide methods to manipulate and check their status.

Possible statuses are defined by the `IStatusEvent.EventStatus` enum.

| Value      | Description                                                          |
|------------|----------------------------------------------------------------------|
| ALIVE      | The event is active and not suppressed or terminated.                |
| SUPPRESSED | The event is suppressed. A suppressed event may become unsuppressed. |
| TERMINATED | The event is terminated and cannot be altered further.               |

### Definition

=== "StatusEvent"

    Extend the `StatusEvent` class.
    ``` java
    public class Event extends StatusEvent {
        
    }
    ```
    Completely functional out of the box, this is the recommended approach.

=== "IStatusEvent"

    If you need custom functionality, implement the `IStatusEvent` interface.
    ``` java
    public class Event implements IStatusEvent {
        
        private EventStatus status;
        
        @NotNull
        @Override
        public EventStatus getEventStatus() {
            return status;
        }

        @Override
        public void setEventStatus(@NotNull EventStatus status) {
            this.status = status;
        }

        @Override
        public boolean isSuppressed() {
            return status == EventStatus.SUPPRESSED;
        }

        @Override
        public boolean isTerminated() {
            return status == EventStatus.TERMINATED;
        }
    }
    ```

    ???+ warning
        It's recommended not to call `#!java setEventStatus()` outside of the 
        status event itself, even in your own implementations.

## Targeted Event

An event that targets a specific listener class.

Targeted events are dispatched to the targeted listener and all nested 
listeners.

### Definition

=== "ClassTargetingEvent"

    Extend the `#!java ClassTargetingEvent` class.
    ``` java
    public class Event extends ClassTargetingEvent {

        public Event(@Nullable Class<? extends Listener<?>> targetClass) {
            super(targetClass);
        }
    }
    ```
    Completely functional out of the box, this is the recommended approach.

=== "IClassTargetingEvent"

    If you need custom functionality, implement the `IClassTargetingEvent` 
    interface.
    ``` java
    public class Event implements IClassTargetingEvent {

        @Nullable
        private final Class<? extends Listener<?>> target;

        public Event(@Nullable Class<? extends Listener<?>> target) {
            this.target = target;
        }

        @Nullable
        @Override
        public Class<? extends Listener<?>> getTargetClass() {
            return target;
        }
    }
    ```

## Staged Event