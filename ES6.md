## __Template Literal__ 
```javascript
console.log(`Hello! Im a string
continues on this line`)

var name = "Jimmy"
var day = "Wednesday"


var instructor = {
    name: "Chris",
    lesson: "ES6",
    greet: function() {return `Hello ${this.name} I hope ${this.lesson} goes well`}

}

console.log(instructor.greet())

console.log(`Our instructor is ${instructor.name} and today we are learning ${instructor.lesson}`)

function foo() {

    let x = true
    if (x) {
        var usingVar = "im using var";
    }
    console.log(usingVar);
    
}
foo()

const INSTRUCTORS = ["Jimm", "Christopher"];
INSTRUCTORS = ["Jim","Chris"];       Throws a Type Error
INSTRUCTORS.push("Jack", "Jill");
console.log(INSTRUCTORS)

function hello(name = "Mystery Person") {
    console.log(`Hello ${name}!`)
}

hello("Bobby");
hello();
```

## __Arrow Functions__
```javascript
const teacher = {
    name: "Jimm",
    speak: function() {
        let boundFunction = function(){
        console.log(`later my name is ${this.name}`)
        }.bind(this)
        setTimeout(boundFunction, 1000)
}
}
teacher.speak();

const teacher = {
    name: "Jimm",
    speak() {
        let boundFunction = () => {
            console.log(`later my name is ${this.name}`)
        }
        setTimeout(boundFunction, 1000);
    } 
}
teacher.speak();
```

## __Lexical Binding__ - they bind to scope where defined not where they are used

```javascript
let students = [
    {name:"Hugo"},
    {name:"Candace"},
    {name:"Taylor"},
    {name:"Dimitri"}
]

let names = students.map((student) => student.name);
console.log(names)

function add() {
    console.log('arguments object:', arguments);
    

    var numbers = Array.prototype.slice.call(arguments)

    var sum = 0;

    numbers.forEach(number => {
        sum += number
    });
    return sum;
}

console.log(add(1,2,3,4,5,6,7,8));



let add = (...numbers) => {
    console.log("rest parameters", numbers)

    let sum = 0;

    numbers.forEach(number => sum += number)
    return sum;
}

console.log(add(1,2,3,4,5,6,7,8));


let add = (...numbers) => numbers.reduce((sum, number) => sum += number, 0);
console.log(add(1,2,3,4,5,6,7,8))


function addStuff(x,y, ...z){
    return (x+y) * z.length
}

console.log(addStuff(1,2, "hello", "world", true, 99))

let random = ["Hello", "World", true, 99]
let newArray = [1,2, ...random, 3]

console.log(newArray);

var student =["Julian", "AJ", "Matt"]
var x = student [0]
var y = student [1]
var z = student [2]

console.log(x,y,z)

var students =["Julian", "AJ", "Matt"]
let[x,y,z] = student
let[ ,y,z] = student
console.log(y,z)

let[x, ...rest] = students
console.log(x, rest)

let completedHomework = () => {
    return ["Julian", "AJ", "Matt"]
}
let [x,y,z] = completedHomework();
console.log(x,y,z);

//also works with objects

let instructor = {
    name: "jimmy",
    email: "askdlma.com"
}
let {name: x, email: y} = instructor;

console.log(x);

let car = {
    make: "Honda"
}

function something ({make, year = 2001}){
console.log (make, year);
}

something(car);
```

## __Prototypes__

```javascript
function Person (name, job) {
    this.name = name;
    this.job = job;
}

Person.prototype.getName = function getName() { return this.name}
Person.prototype.getJob = function getJob() { return this.job}

var person1 = new Person("Joe", "Cook")
console.log(`Hello ${person1.getName()}, your job is ${person1.getJob()}`)
```
## __Classes__
```javascript
class Person {
    constructor (name, job){
        this.name = name;
        this.job = job;
    }
    getName() {
        return this.name
    }
    getJob() {
        return this.job
    }
}

let goodGuy = new Person ("Neo", "Matrix");
console.log(goodGuy);

class Person {
    constructor (name, job){
        this.name = name;
        this.job = job;
    }
    getName() {
        return this.name
    }
    getJob() {
        return this.job
    }
}

class SuperHero extends Person {
    constructor (name, heroName, superPower){
        super(name)
        this.heroName = heroName;
        this.superPower = superPower;
    }
    secretIdentity() {
        return `${this.name} is ${this.heroName}`;
    }
}

let batman= new SuperHero("Bruce Wayne", "Batman")
console.log(batman.secretIdentity())

class Person {
    constructor(name){
        this.name = name;
    }
    set name (name){
        this._name = name;
    }
    get name (){
        return this._name
    }
}

var goodGuy = new Person('Jim Gordon');
console.log(goodGuy.name)
goodGuy.name = "James Gordon";
console.log(goodGuy.name)

let student = {name: "A-aron"};
let status = new Map();

status.set(student.name, "D-nice")
status.set ("feeling", "churlish")
console.log(status.get(student.name))
console.log(status.get("feeling"))

```

