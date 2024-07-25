# Listeners

## Definition

=== "EventListener"

    Extend the `EventListener<T>` class.

    ```java
    public class ExampleListener extends EventListener<MessageEvent> {
    
        public ExampleListener() {
            super(MessageEvent.class);
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
        MessageEvent.class,
        event -> {//...}
    )
    ```

## Registration

=== "EventListener"

    Listeners can be registered to a subsciber, 
    
    ```java hl_lines="6"
    EventBus eventBus = new EventBus();
    Subscriber subscriber = new Subscriber();
    eventBus.subscribe(subscriber);

    // Assuming you've already defined a listener
    subscriber.registerListener(new ExampleListener());
    ```

    or directly to an event bus.
    ```java hl_lines="4"
    EventBus eventBus = new EventBus();
    
    // Assuming you've already defined a listener
    eventBus.register(new ExampleListener());
    ```

=== "LambdaEventListener"

    Listeners can be registered to a subsciber, 
    
    ```java hl_lines="5-8"
    EventBus eventBus = new EventBus();
    Subscriber subscriber = new Subscriber();
    eventBus.subscribe(subscriber);

    subscriber.registerListener(new LambdaEventListener<>(
            MessageEvent.class,
            event -> {/*...*/}
    ));
    ```

    or directly to an event bus.
    ```java hl_lines="3-6"
    EventBus eventBus = new EventBus();
    
    eventBus.register(new LambdaEventListener<>(
            MessageEvent.class,
            event -> {/*...*/}
    ));
    ```
