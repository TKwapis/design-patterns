# Design Patterns – Deutsch + C# Beispiele

**Design Patterns** (Entwurfsmuster) sind bewährte Lösungen für wiederkehrende Probleme in der Softwareentwicklung. Sie sind keine fertigen Klassen oder Bibliotheken, sondern Denkansätze, wie man bestimmte Probleme in verschiedenen Kontexten lösen kann.

> **⚠️ Hinweis:** Design Patterns sind kein Allheilmittel. Verwende sie sinnvoll, nicht zwanghaft.

---

## 📦 Arten von Design Patterns

- **Erzeugungsmuster** (Creational)
- **Strukturmuster** (Structural)
- **Verhaltensmuster** (Behavioral)

---

## 🏗️ Creational Patterns – Erzeugungsmuster

Diese Muster betreffen die Art und Weise, wie Objekte erstellt werden. Sie helfen dabei, den Code flexibler und einfacher wartbar zu gestalten.

### 🏠 Simple Factory (Einfache Fabrik)

#### Beispiel aus der echten Welt

Statt Türen selbst zu bauen, lässt du sie dir von einer Türfabrik liefern. Du kümmerst dich nicht um Details, sondern bekommst ein fertiges Objekt.

#### In einfachen Worten

Stellt Objekte bereit, ohne dem Aufrufer die Logik der Erstellung zu zeigen.

#### C# Beispiel

```csharp
public interface IDoor
{
    float GetWidth();
    float GetHeight();
}

public class WoodenDoor : IDoor
{
    private float width;
    private float height;

    public WoodenDoor(float width, float height)
    {
        this.width = width;
        this.height = height;
    }

    public float GetWidth() => width;
    public float GetHeight() => height;
}

public static class DoorFactory
{
    public static IDoor MakeDoor(float width, float height)
    {
        return new WoodenDoor(width, height);
    }
}

// Anwendung
var door = DoorFactory.MakeDoor(100, 200);
Console.WriteLine("Breite: " + door.GetWidth());
Console.WriteLine("Höhe: " + door.GetHeight());
