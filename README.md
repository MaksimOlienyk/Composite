# Composite
```cs
interface IComponent { void Operation(); }

class Leaf : IComponent { public void Operation()=>Console.WriteLine("Leaf"); }

class Composite : IComponent {
    private List<IComponent> _children=new();
    public void Add(IComponent c)=>_children.Add(c);
    public void Operation(){ Console.WriteLine("Composite"); foreach(var c in _children) c.Operation(); }
}

class Program {
    static void Main() {
        var root=new Composite(); root.Add(new Leaf()); root.Operation();
    }
}
