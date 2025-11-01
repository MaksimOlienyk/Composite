# Composite - Патерн Проєктування

Патерн **Composite** дозволяє працювати з групою об’єктів **так само, як і з одним об’єктом**.  
Тобто ми можемо об’єднувати об’єкти у деревоподібну структуру і викликати методи рекурсивно.

---

## Ідея патерна

> Дати можливість як **простим** об’єктам (листкам), так і **складеним** (вузлам) мати однаковий інтерфейс.

---

## Структура

| Роль | Опис |
|------|------|
| `IComponent` | Спільний інтерфейс для всіх елементів |
| `Leaf` | Прості елементи (листки), які не містять дітей |
| `Composite` | Складні елементи, що можуть містити інші компоненти |

---

## Код:

```csharp
interface IComponent { 
    void Operation(); 
}

class Leaf : IComponent {
    public void Operation() => Console.WriteLine("Leaf");
}

class Composite : IComponent {
    private List<IComponent> _children = new();
    public void Add(IComponent c) => _children.Add(c);

    public void Operation() {
        Console.WriteLine("Composite");
        foreach (var c in _children)
            c.Operation();
    }
}

class Program {
    static void Main() {
        var root = new Composite();
        root.Add(new Leaf());
        root.Operation();
    }
}

