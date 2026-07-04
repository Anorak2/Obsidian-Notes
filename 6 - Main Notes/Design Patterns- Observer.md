
2026-06-03

Tags: [[Software Engineering (SWE)]] [[Java]] [[OOP Design Patterns]]
# Design Patterns- Observer
Observer Design Pattern is a behavioral pattern that creates a one-to-many relationship between a subject and its observers. When the subject's state changes, all dependent observers are notified and updated automatically, ensuring synchronized communication.

- Enables automatic updates to multiple objects when one object changes, useful for event-driven or publish-subscribe systems.
- Promotes loose coupling between the subject and its observers.

examples: Social media notifications, stock market apps on price change, GUI event listeners, severe weather monitoring alerts.

**pros:**
- Provides loose coupling between subject and observers.
- Allows easy addition or removal of observers at runtime.
- Ensures automatic and consistent updates to all dependents.

**cons:**
- Can lead to performance issues if there are many observers.
- Debugging becomes harder due to indirect communication.
- Observers may receive unnecessary updates if not managed carefully.

## Example code

```java
import java.util.ArrayList;
import java.util.List;

// Observer interface
interface Observer {
    void update(String weather);
}

// Subject interface
interface Subject {
    void addObserver(Observer observer);
    void removeObserver(Observer observer);
    void notifyObservers();
}

// Concrete Subject
class WeatherStation implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private String weather = "";

    @Override
    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    @Override
    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(weather);
        }
    }

    public void setWeather(String newWeather) {
        this.weather = newWeather;
        notifyObservers();
    }
}
```
# References
- 