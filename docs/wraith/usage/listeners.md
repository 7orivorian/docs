# Listeners

For class event listeners, you can define your listeners as follows:

```java
public class ExampleListener extends EventListener<MessageEvent> {

    public ExampleListener() {
        super(MessageEvent.class);
    }

    @Override
    public void invoke(MessageEvent event) {
        event.setMessage("Hello world!");
    }
}
```

```java
public class ExampleSubscriber extends Subscriber {

    public ExampleSubscriber() {
        // Register the listener
        registerListener(new ExampleListener());
    }
}
```

Lambda event listeners provide a more concise way to achieve the same functionality:

```java
public class ExampleSubscriber extends Subscriber {

    public ExampleSubscriber() {
        // Register the listener
        registerListener(
                new LambdaEventListener<>(MessageEvent.class, event -> event.setMessage("Hello world!"))
        );
    }
}
```