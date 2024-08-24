# Listeners

## Definition

=== "EventListener"

    Extend the `EventListener<T>` class.

    ```java
    public class ExampleListener extends EventListener<MessageEvent> {
    
        public ExampleListener() {
            super(Target.fine(MessageEvent.class));
        }
    
        @Override
        public void invoke(MessageEvent event) {
            //...
        }
    }
    ```

=== "LambdaEventListener"

    `LambdaEventListener` provides a concise way to create a listener.
    
    ```java
    new LambdaEventListener<>(
        Target.fine(MessageEvent.class),
        event -> {/*...*/}
    )
    ```

## Registration

=== "EventListener"

    Listeners can be registered to a subsciber.
    
    ```java hl_lines="6"
    EventBus eventBus = new EventBus();
    Subscriber subscriber = new Subscriber();
    eventBus.subscribe(subscriber);

    // Assuming you've already defined a listener
    subscriber.registerListener(new ExampleListener());
    ```

    Or directly to an event bus.
    ```java hl_lines="4"
    EventBus eventBus = new EventBus();
    
    // Assuming you've already defined a listener
    eventBus.register(new ExampleListener());
    ```

=== "LambdaEventListener"

    Listeners can be registered to a subsciber.
    
    ```java hl_lines="6-9"
    EventBus eventBus = new EventBus();
    Subscriber subscriber = new Subscriber();
    eventBus.subscribe(subscriber);

    subscriber.registerListener(
        new LambdaEventListener<>(
            Target.fine(MessageEvent.class),
            event -> {/*...*/}
        )
    );
    ```

    Or directly to an event bus.
    ```java hl_lines="4-7"
    EventBus eventBus = new EventBus();
    
    eventBus.register(
        new LambdaEventListener<>(
            Target.fine(MessageEvent.class),
            event -> {/*...*/}
        )
    );
    ```
