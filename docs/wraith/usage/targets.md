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
    
    ??? info "Listener setup details."
    
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
    
    ??? info "Setup details."
    
        ```java
        EventBus eventBus = new EventBus();
        eventBus.register(new MyListener());
        eventBus.register(new MyExtendedListener());
        eventBus.register(new OtherListener());
        ```
    
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