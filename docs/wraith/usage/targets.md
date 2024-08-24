# Targets

A `Target` determines if a given class matches the target class
according to its targeting rule.

This can be used dispatch events to specific listeners or listen to specific
events.

## Definition

## Usage Examples

=== "Dispatch Targets"

    In this example, listeners are listening to **all** events, & will print the
    word "Hi" when they handle an event.
    
    ???+ info "Setup details."
    
        ```java
        EventBus eventBus = new EventBus();
        eventBus.register(new MyListener());
        eventBus.register(new MyExtendedListener());
        eventBus.register(new OtherListener());
        ```
        (`MyExtendedListener` extends `MyListener`.)
    
    If we dispatch our event normally, `"Hi"` will be printed {==3 times==}.
    
    ``` java
    eventBus.dispatch(new MyEvent());
    ```
    
    If we fine target `MyListener.class`, `"Hi"` will only be printed
    {==1 time==} because neither `MyExtendedListener` nor `OtherListener` are
    included in this target.
    
    ``` java
    eventBus.dispatch(new MyEvent(), Target.fine(MyListener.class));
    ```
    
    However, if we _cascade_ target `MyListener.class`, `"Hi"` will be printed
    {==2 times==} because `MyExtendedListener` extends `MyListener`.
    
    ``` java
    eventBus.dispatch(new MyEvent(), Target.cascade(MyListener.class));
    ```

=== "Listener Targets"

    In this example, listeners are listening to **all** events, & will print the
    word "Hi" when they handle an event.
    
    ???+ info "Setup details."
    
        Event bus setup.
        ```java
        EventBus eventBus = new EventBus();

        Target target = // ...

        eventBus.register(new MyListener(target));

        eventBus.dispatch(new MyEvent("hi"));
        eventBus.dispatch(new MyEvent.MyExtendedEvent("hi"));
        eventBus.dispatch(new OtherEvent("hi"));
        ```
        (`MyExtendedEvent` extends `MyEvent`.)

        `MyListener` class.
        ```java
        public class MyListener extends EventListener<MyEvent> {
        
            public MyListener(Target target) {
                super(target);
            }
        
            @Override
            public void invoke(MyEvent event) {
                System.out.println(event.message());
            }
        }
        ```

        `MyEvent` class.
        ```java
        public class MyEvent {
        
            private final String message;
        
            public MyEvent(String message) {
                this.message = message;
            }
        
            public String message() {
                return message;
            }
        
            public static class MyExtendedEvent extends MyEvent {
        
                public MyExtendedEvent(String message) {
                    super(message);
                }
            }
        }
        ```
    
    If we listen with a target of `all()`, `"Hi"` will be printed {==3 times==}.
    
    ``` java
    Target.all()
    ```
    
    If we fine target `MyEvent.class`, `"Hi"` will only be printed
    {==1 time==} because neither `MyExtendedEvent` nor `OtherEvent` are
    included in this target.
    
    ``` java
    Target.fine(MyListener.class)
    ```
    
    However, if we _cascade_ target `MyEvent.class`, `"Hi"` will be printed
    {==2 times==} because `MyExtendedEvent` extends `MyEvent`.
    
    ``` java
    Target.cascade(MyListener.class)
    ```
