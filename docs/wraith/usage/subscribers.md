# Subscribers

## Definition

To define a subscriber, you have multiple options.

Extend the Subscriber class:

```java
public class ExampleSubscriber extends Subscriber {
    // ...
}
```

Implement the ISubscriber interface:

```java
public class ExampleSubscriber implements ISubscriber {
    // ...
}
```

## Subscription

Once you've defined your subscriber, you can subscribe it to an event bus
in a variety of ways.

Inside the subscriber itself.

```java hl_lines="8"
public class Consts {
    private static final IEventBus EVENT_BUS = new EventBus();
}

public class ExampleSubscriber extends Subscriber {

    public ExampleSubscriber() {
        Consts.EVENT_BUS.subscribe(this);
    }
}
```

```java hl_lines="12"
public class Consts {
    private static final IEventBus EVENT_BUS = new EventBus();
}

public class ExampleSubscriber extends Subscriber {

    public ExampleSubscriber() {
        
    }
    
    public void subscribe() {
        Consts.EVENT_BUS.subscribe(this);
    }
}
```

Or externally.

```java hl_lines="6"
public class Example {
    
    private static final IEventBus EVENT_BUS = new EventBus();

    public void handleSubscription() {
        EVENT_BUS.subscribe(new ExampleSubscriber());
    }
}
```

```java hl_lines="4 7"
public class Example {
    
    private static final IEventBus EVENT_BUS = new EventBus();
    private final ExampleSubscriber subscriber = new ExampleSubscriber();

    public void handleSubscription() {
        EVENT_BUS.subscribe(subscriber);
    }
}
```