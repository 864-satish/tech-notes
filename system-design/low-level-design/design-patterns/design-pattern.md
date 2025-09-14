# GoF Design Patterns in TypeScript
## 1. Creational Patterns
1.1 Singleton

Ensures only one instance of a class exists and provides a global point of access.
```typescript
class Singleton {
  private static instance: Singleton;
  private constructor() {}
  static getInstance() {
    if (!this.instance) this.instance = new Singleton();
    return this.instance;
  }
}
const s1 = Singleton.getInstance();
```

1.2 Factory Method

Defines an interface for creating an object but lets subclasses decide which class to instantiate.

```typescript
interface Button { render(): void; }
class HTMLButton implements Button { render() { console.log("HTML Button"); } }
class Dialog {
  createButton(): Button { return new HTMLButton(); }
}
const dialog = new Dialog();
dialog.createButton().render();
```
1.3 Abstract Factory

Provides an interface for creating families of related objects without specifying concrete classes.
```typescript
interface GUIFactory { createButton(): Button; }
class WinFactory implements GUIFactory {
  createButton(): Button { return new HTMLButton(); }
}
const factory: GUIFactory = new WinFactory();
factory.createButton().render();
```
1.4 Builder

Separates object construction from representation, allowing different representations.
```typescript
class Car { parts: string[] = []; }
class CarBuilder {
  private car = new Car();
  addWheel() { this.car.parts.push("Wheel"); return this; }
  build() { return this.car; }
}
const car = new CarBuilder().addWheel().build();
```
1.5 Prototype

Creates new objects by cloning an existing object.

class Prototype {
  constructor(public field: string) {}
  clone() { return new Prototype(this.field); }
}
const p1 = new Prototype("data");
const p2 = p1.clone();

## 2. Structural Patterns
2.1 Adapter

Allows incompatible interfaces to work together.
```typescript
class OldSystem { oldRequest() { return "old"; } }
class Adapter {
  constructor(private old: OldSystem) {}
  request() { return this.old.oldRequest(); }
}
const adapter = new Adapter(new OldSystem());
console.log(adapter.request());
```
2.2 Bridge

Separates abstraction from implementation.
```typescript
interface Device { powerOn(): void; }
class TV implements Device { powerOn() { console.log("TV on"); } }
class Remote {
  constructor(private device: Device) {}
  toggle() { this.device.powerOn(); }
}
new Remote(new TV()).toggle();
```
2.3 Composite

Treats individual objects and compositions uniformly.
```typescript
interface Component { operation(): void; }
class Leaf implements Component {
  operation() { console.log("Leaf"); }
}
class Composite implements Component {
  children: Component[] = [];
  add(c: Component) { this.children.push(c); }
  operation() { this.children.forEach(c => c.operation()); }
}
const root = new Composite();
root.add(new Leaf());
root.operation();
```
2.4 Decorator

Adds new functionality dynamically without altering structure.
```typescript
class Coffee { cost() { return 5; } }
class MilkDecorator extends Coffee {
  constructor(private coffee: Coffee) { super(); }
  cost() { return this.coffee.cost() + 2; }
}
console.log(new MilkDecorator(new Coffee()).cost());
```
2.5 Facade

Provides a simplified interface to a complex subsystem.
```typescript
class CPU { start() { console.log("CPU start"); } }
class Computer {
  private cpu = new CPU();
  start() { this.cpu.start(); }
}
new Computer().start();
```
2.6 Flyweight

Shares common state across many objects to save memory.
```typescript
class Flyweight {
  constructor(public shared: string) {}
}
class FlyweightFactory {
  private pool: { [key: string]: Flyweight } = {};
  get(key: string) {
    if (!this.pool[key]) this.pool[key] = new Flyweight(key);
    return this.pool[key];
  }
}
const factory = new FlyweightFactory();
console.log(factory.get("A") === factory.get("A")); // true
```
2.7 Proxy

Controls access to another object.
```typescript
interface Service { request(): void; }
class RealService implements Service {
  request() { console.log("Real service"); }
}
class ProxyService implements Service {
  private real = new RealService();
  request() { console.log("Proxy check"); this.real.request(); }
}
new ProxyService().request();
```
## 3. Behavioral Patterns
3.1 Chain of Responsibility

Passes requests along a chain until handled.
```typescript
abstract class Handler {
  next?: Handler;
  setNext(h: Handler) { this.next = h; return h; }
  handle(req: string) { if (this.next) this.next.handle(req); }
}
class ConcreteHandler extends Handler {
  handle(req: string) { console.log("Handled: " + req); super.handle(req); }
}
const h1 = new ConcreteHandler(), h2 = new ConcreteHandler();
h1.setNext(h2).handle("Request");
```
3.2 Command

Encapsulates requests as objects.
```typescript
interface Command { execute(): void; }
class Light { on() { console.log("Light on"); } }
class OnCommand implements Command {
  constructor(private light: Light) {}
  execute() { this.light.on(); }
}
new OnCommand(new Light()).execute();
```
3.3 Interpreter

Defines a grammar and interpreter for language.
```typescript
interface Expression { interpret(): number; }
class NumberExpr implements Expression {
  constructor(private value: number) {}
  interpret() { return this.value; }
}
class AddExpr implements Expression {
  constructor(private left: Expression, private right: Expression) {}
  interpret() { return this.left.interpret() + this.right.interpret(); }
}
console.log(new AddExpr(new NumberExpr(2), new NumberExpr(3)).interpret());
```
3.4 Iterator

Provides sequential access without exposing structure.
```typescript
class Iterator<T> {
  private index = 0;
  constructor(private items: T[]) {}
  next() { return this.items[this.index++]; }
}
const it = new Iterator([1, 2, 3]);
console.log(it.next());
```
3.5 Mediator

Centralizes complex communications between objects.
```typescript
class Mediator {
  notify(sender: string, event: string) { console.log(`${sender} -> ${event}`); }
}
class Colleague {
  constructor(private mediator: Mediator) {}
  send(event: string) { this.mediator.notify("Colleague", event); }
}
new Colleague(new Mediator()).send("Hello");
```
3.6 Memento

Captures and restores object’s state.
```typescript
class Memento { constructor(public state: string) {} }
class Originator {
  state = "";
  save() { return new Memento(this.state); }
  restore(m: Memento) { this.state = m.state; }
}
const origin = new Originator();
origin.state = "A";
const saved = origin.save();
origin.state = "B";
origin.restore(saved);
```
3.7 Observer

Defines a one-to-many dependency for updates.
```typescript
class Subject {
  private observers: (() => void)[] = [];
  attach(o: () => void) { this.observers.push(o); }
  notify() { this.observers.forEach(o => o()); }
}
const subject = new Subject();
subject.attach(() => console.log("Updated!"));
subject.notify();
```
3.8 State

Changes behavior based on internal state.
```typescript
interface State { handle(): void; }
class OnState implements State { handle() { console.log("On"); } }
class OffState implements State { handle() { console.log("Off"); } }
class Context {
  constructor(private state: State) {}
  setState(s: State) { this.state = s; }
  request() { this.state.handle(); }
}
const ctx = new Context(new OffState());
ctx.request();
ctx.setState(new OnState());
ctx.request();
```
3.9 Strategy

Defines a family of algorithms and makes them interchangeable.
```typescript
interface Strategy { execute(a: number, b: number): number; }
class Add implements Strategy { execute(a: number, b: number) { return a + b; } }
class ContextS {
  constructor(private strategy: Strategy) {}
  run(a: number, b: number) { return this.strategy.execute(a, b); }
}
console.log(new ContextS(new Add()).run(2, 3));
```
3.10 Template Method

Defines skeleton of algorithm, allowing subclasses to redefine steps.
```typescript
abstract class Game {
  play() { this.start(); this.end(); }
  abstract start(): void;
  abstract end(): void;
}
class Chess extends Game {
  start() { console.log("Chess start"); }
  end() { console.log("Chess end"); }
}
new Chess().play();
```
3.11 Visitor

Separates algorithms from objects they operate on.
```typescript
interface Visitor { visit(element: Element): void; }
interface Element { accept(v: Visitor): void; }
class ConcreteElement implements Element {
  accept(v: Visitor) { v.visit(this); }
}
class ConcreteVisitor implements Visitor {
  visit(e: Element) { console.log("Visited"); }
}
new ConcreteElement().accept(new ConcreteVisitor());
```

✅ That’s all 23 GoF Design Patterns in TypeScript with brief description.
