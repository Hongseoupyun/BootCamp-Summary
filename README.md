# BootCamp-Summary

## Week 1

- Version Control=>Git

- Git workflow :
```git clone/git init``` --> WORK WORK WORK --> ```git status (to check what files we worked on) ```--> ```git add .(to stage ALL files)``` --> ```git commit``` --> ```git push``` (so our work goes into github)

- Command line argument using ``` process.argv ```

- JavaScript ES6 Template Literal:
```const name = 'Alice';
console.log(`Hello, ${name}!`); // logs: Hello, Alice!
```

- Writting Pseudocode
```for (let num = 100; num <= 200; num++) {
  if (num % 3 === 0 && num % 4 === 0) {
    console.log("LoopyLighthouse");
  } else if (num % 3 === 0) {
    console.log("Loopy");
  } else if (num % 4 === 0) {
    console.log("Lighthouse");
  } else {
    console.log(num);
  }
}
```

```
Loop from 100 to 200:
  Let num = the current step in the loop
  If num % 3 is equal to 0 and num % 4 is equal to 0:
    Print "LoopyLighthouse"
  Else if num % 3 is equal to 0:
    Print "Loopy"
  Else if num % 4 is equal to 0:
    Print "Lighthouse"
  Otherwise
    Print num
  End if
End loop
```

- Scope in JavaScript (Global and Local)

- Truthy and Falsey (==, ===)

``` 
False
// False is False. Makes sense, right?

0
// 0 is the only falsey Number

""
// an empty string is falsey

null
// a null, or empty value, is falsey.

undefined
// an object that has not been defined is considered falsey.

NaN
// Not a Number. You'll learn more about NaN as we go on.

```

- Object in JavaScript

```
let car = {
    brand: 'toyota',
    model: 'GT86',
    year:  2019,
    transmissionType: 'manual'
  }
```
```  
value MUST have a specific key.

Objects are denotes with {} brackets 
```
- Functions in JavaScrit

- Callback Function

```
A callback function is a function, that is a parameter that goes into another function (high order function).

The high order function may call that function.
```

## Week 2

- Test Driven Development(TDD)

``` TDD is the idea of TDD is that the tests are developed for your code before actually writing the code.```

- Automated testing scripts in Mocha and Chai

- Module.exports the function to be tested

- Synchronous and Asynchronous

```
A synchronous waiter would take an order from a customer deliver it to the cooks and then wait for the food to finish before taking another order.

A more typical waiter is asynchronous. They take a customers order, deliver it to the chef then continue to take orders until the food finishes, at which point they give the meal to the customer.
```

- Networking with TCP, HTTP'

- Promises and callback
```
diceRoll().then( (number) => {
  console.log("THE NUMBER IS ", number);
});
```

## Week 3

- Web Servers
```
A server is a program, that is able to serve up information to other computers/programs. A server listens to peoples requests, if the request is valid, then server will respond with information, otherwise it may throw an error, show a warning to the client, or send the client somewhere else.
```
- NodeJS Server

```
const PORT = 8080;
let http = require('http');

// server logic goes in here...
let server = http.createServer((request, response) => {
    response.end('Hello World!!');
})

// listening...
server.listen(PORT, () => {
    console.log("Server listening on port ", PORT);
});
```

- Request <----> Response

```
A client always asks a server for a request, and a server always has to give back a response. This is how the two comunicate with each other.
A typical request/response senario is:
```

- ExpressJS

```
const PORT = 8080;

const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello World!');
})

app.listen(port, () => {
  console.log(`Example app listening at ${PORT}`);
})
```

- CRUD : Create, read, update and delete

- Routes : A route is made up of a ```VERB ```and a P```ATH```.

Verbs: ```GET```, ```POST```,``` PUT```, ```PATCH```, ```DELETE```

- REST : REST means that the path that we are going to should represent the data being transferred.
An API that uses the REST convention is said to be RESTful.

- Cookies : "n HTTP cookie is a small piece of data sent from a website and stored on the user's computer by the user's web browser while the user is browsing. Cookies were designed to be a reliable mechanism for websites to remember stateful information or to record the user's browsing activity." 
- To check your cookies go into Chrome Dev ```tools``` -->``` Application ```--> ```Storage``` ---> ```Cookies``` ---> ```localhost ```or any other website.
- Middleware : Middleware is an action/operation that may happen between the request and the response , Middleware is a subset of chained functions called by the Express js routing layer before the user-defined handler is invoked(eg Nodemon, Morgan, Body-parser) 


- Cookie + (User Authentication & Security)

```
// now we are secure !! 
app.post('/login', (req,res) => {
    console.log(req.body);
    const user = findUserByEmail(req.body.email);
    if (user) {
        req.session.user_id = user.id; // <-------- GOOD WAY
        res.redirect(`/`);
    } else {
        res.send("FAILED LOGIN");
    }
})
```
- next();

```Next is a callback function that will send the response to the next middleware or to the route it was supposed to hit. Without it, the app will simply hang because we have hijacked the entire workflow of express.```

```
app.use('/urls', function (req, res, next) {
  if (req.session.user_id) {
    res.redirect('/login');
  } else {
    next();
  }
});
```
- Restful Routing
```
|   NAME   |     PATH        |   HTTP VERB     |            PURPOSE                   |
|----------|-----------------|-----------------|--------------------------------------|
| Index    | /blogs          |      GET        | Displays all blog post               |
| New      | /blogs/new      |      GET        | Shows new form for new blog entry    |
| Create   | /blogs          |      POST       | Creates a new blog post              |
| Show     | /blogs/:id      |      GET        | Shows one specified blog post        |
| Edit     | /blogs/:id/edit |      GET        | Shows edit form for one blog post    |
| Update   | /blogs/:id      |      PUT        | Updates a particular blog post       |
| Destroy  | /blogs/:id      |      DELETE     | Deletes a particular blog post       |
```
## Week 4

- HTML/CSS
- DOM

```
DOM is like a tree structure of your HTML elements. The DOM lets us traverse through this tree structure to easily find specific nodes
( and when we say nodes we are talking about the p, div, title, article, h2, etc... tags)
```

- JQuery/AJAX

```
Ajax is a set of web development techniques using many web technologies on the client side to create asynchronous web applications. 
With Ajax, web applications can send and retrieve data from a server asynchronously without interfering with the display and 
behavior of the existing page. 
```
```
 $('form').on('submit', (evt) => {
        evt.preventDefault();
        // How do I get the value of what i typed INTO my search URL?
        // How do i bundle the data i need to send to the user  ( hint hint serilize? )
        $.ajax({
            url: `http://api.tvmaze.com/search/shows?q=${evt.target.search.value}`,
            method: 'GET',
            dataType: 'JSON'
        }).then(function(response) {
            console.log(response);
            // const item = createItem(response[0])
            $('#results').empty();
            createItems(response);
        })
    })
```
- Responsive Design
- SASS
- Media Queries

```
@media only screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```


## Week 5

- DATABASE

```
A database is a structured set of data held in a computer, especially one that is accessible in various ways.

```

- SQL
```Structured Query Language (SQL) is used to issue commands to our RBDMS servers```

- ERD

```An ERD entity is a definable thing or concept within a system, such as a person/role.```

![image](https://user-images.githubusercontent.com/89428637/195510924-ca726c44-6bed-4f48-a878-190801f9bfe7.png)

- SQL Queries
```SELECT```
```WHERE```
```LIKE```
```JOIN```
![image](https://user-images.githubusercontent.com/89428637/195511152-3d99592a-209d-46ea-b50a-d4b84639bc1e.png)
```GROUP BY```
```SUB```

- Primary Keys
- Foreign Keys
- Data Types
![image](https://user-images.githubusercontent.com/89428637/195511542-a0d0ce23-bd3b-4adc-815b-09ac1aa7140b.png)
- Relationship Types
One to one
![image](https://user-images.githubusercontent.com/89428637/195511803-902fb7a2-2f05-49f6-8955-0d4037aba0cb.png)

One to many
![image](https://user-images.githubusercontent.com/89428637/195511829-eeaca561-cf23-4540-a8a1-60bb3308b84a.png)

Many to many
![image](https://user-images.githubusercontent.com/89428637/195511860-f8da9a3d-bdbc-4a4b-b9f9-caa3357818ce.png)

- Node(express)-PSQL Basic Connection

```
// dbInitializeConnection.js

const { Pool } = require('pg');
// Setup a connection to PSQL with the correct credentials.
const pool = new Pool({
    user: 'development',
    password: 'development',
    database: 'w05d03',
    host: 'localhost',
    port: 5432
})

console.log("connection establishing...");

module.exports = pool;
```
```
// server.js

const db = require('./db/db'); // require our connection to PSQL
const dbHelpers = require('./dbHelpers/index');
const { getUsers, getMarks } = dbHelpers(db);
```
```
//dbhelpers.js
module.exports = (db) => {
    const getUsers = () => {
        return db.query("SELECT * FROM students").then(response => {
            return response.rows;
        })
    }

    const getMarks = () => {
        return db.query(`
          SELECT name, students, mark, total FROM
          students JOIN quiz_results ON quiz_results.student_id = students.id
          JOIN quizes ON quiz_results.quiz_id = quizes.id;`
        ).then(response => {
            console.log(response);
            return response.rows;
        })
    }

    return { getUsers, getMarks };
}
```
## Week 6
- Midterm Project
## Week 7
- React
- Passing props

```
<Card number={3} suit={'clubs'}/>
```

- Conditional Rendering
```
      return (
          <div className={'card' + ' ' + (props.color && 'red')}>
              <h2>{props.number ? props.number : 'A'}</h2>
              <h1 className="symbol">{props.suit ? suits[props.suit] : suits.spades}</h1>
              <h2 className="right">{props.number ? props.number : 'A'}</h2>
          </div>
      )
 ```
 ```
 function Navbar() {
    const isLogged = false;
    return (
        {isLogged ? <UserInfo/> : <Login/>}
    )
}
```
 
- Fragment

```
return (
  <Fragment>
    <p><Hello world/p>
  </Fragment>
);
```
- Managing State
```
import React, { useState } from "react";

export default function example (props) {
  const [number, numberEvent] = useState(0);
  return (
    <div>
      {number}
      <button onClick={e => numberEvent(number + 1)}>Add +1 </button>
    </div>
  )
}
```
- Looping pattern
```
    return (    
        <div>
            {props.cards.map((card) => <Card number={card.number} suit={card.suit} color={card.color}/>)}

            <h1>{number}</h1>
            <button onClick={addUp}>add</button>
        </div>
    )
```
- Passing chileren with JSX
```
import React from "react";
import ListItem from "./ListItem";

export default function List(props) {
  return (
    <ul>
      <ListItem>I AM THE CHILD</ListItem>
    </ul>
  );
};

```
```
export default function ListItem(props) {
  return (
    <li className="list-item">
      {props.children}
    </li>
  );
};
```
- Handling Events
```
const handleClick = () => {
  console.log("CLICKED!!!")
}

return (
  <div>
    <button onClick={handleClick}>Click Me</button>
  </div>
)

```
- Controlled Inputs
```
import React, { useState } from "react";

export default function List(props) {


  const [input, handleInput] = useState("");

  const handleForm = (evt) => {
    evt.preventDefault();
    props.addItem(input);
    handleInput("");
  }

  return (
    <form className="ItemForm" onSubmit={handleForm} >
      <input value={input} onChange={evt => handleInput(evt.target.value)} className="itemAdd" type="text"/>
      <button className="add-btn">Add</button>
    </form>
  )
}
```

- Data Fetching & Other Side Effects : Use ```axios``` library to fetch data from backend, ```UseEffect```
```
//setting up useEffect like this make the app render only when the state siren changes

useEffect( () => {
  console.log("woop woop")
}, [siren] )// notice the array now has one value which is a state
```

- Custom Hook

```The idea of a custom hook is logic re-usability. Imagine you have a state, that has logic built in that you cause in a component somewhere else. Well now you can take state and refactor it into its own file. You can then pass that state into multiple files as a new instance, and have all the logic written.```

```

import { useState } from 'react';


export default function useVisualButton(initial) {
    const [num, setNum] = useState(initial);

    const increaseNum = () => {
        setNum(num+1);
    }

    const decreaseNum = () => {
        setNum(num+1);
    }



	return { num, increaseNum, decreaseNum }
}

```

- React Context

```Context is a way to share a specific state between components without prop-drilling.
Context is primarily used when some data needs to be accessible by many components at different nesting levels. 
Apply it sparingly because it makes component reuse more difficult.
```

```
import React, { createContext, useState } from 'react';
// step 1: make a context -- which makes the default shareable state
const GlobalContext = createContext({count: 0});

// step 2: make a provider from the context we made. We need the provider, to
// WRAP around all of Components(Children) that may use this global state.
export function GlobalContextProvider(props) {
  // Step 3: add a state and pass it into the Provider value prop
  const [state, setState] = useState({count: 0});
  return (
    <GlobalContext.Provider value={[state, setState]}>
      {props.children}
    </GlobalContext.Provider>
  )
}

export default GlobalContext;
```
```import React, { useContext } from 'react';
import GlobalContext from '../Context/GlobalContext';


export default function Dogs(props){
  const [state, setState] = useContext(GlobalContext);
  const clickDown = () => setState(prev => ({...prev, count: prev.count - 1}));
  return (
    <div>
      <h2>Dogs Page</h2>
      <h1>Count is: {state.count}</h1>
      <button onClick={clickDown}>click me</button>
    </div>
  )
}
```
## Week 8

- Testing
```
Unit testing means testing individual modules of an application in isolation (without any interaction with dependencies) to confirm that the code is doing things right.

Integration testing means checking if different modules are working fine when combined together as a group.

Functional testing means testing a slice of functionality in the system (may interact with dependencies) to confirm that the code is doing the right things.


```

- Storybook/ Cypress/ Jest

- Integration testing with Jest

```
import React, { useState } from 'react';
import Item from '../Components/Item';

//render <- to do render of the component
//fireEvent <- for clicking
import { render, fireEvent } from '@testing-library/react';

describe( "items", () => {
  //xIt
  //test vs it ( same thing )

  it('The Component mounts', () => {
    // render returns an object with a bunch of functions that will let us query the DOM
    render(<Item item={'buy apples'} done={false}/>)
  })

  it('should have "buy apples" text', () => {
    // render returns an object with a bunch of functions that will let us query the DOM
    const { getByText } = render(<Item item={'buy apples'} done={false}/>)
    // should find the text "buy apples"
    expect( getByText('buy apples') )
  })

  it('should have be className "todo-item"', () => {
    // Container has alot of methods that gives us ways to traverse the Item DOM
    const { container } = render(<Item item={'buy apples'} done={false}/>)
    // our item should have a className todo-item which we can get out firstChild
    expect(container).toHaveClass('todo-item')
  })

  it('should have be className "todo-item"', () => {
    // Container has alot of methods that gives us ways to traverse the Item DOM
    const { container } = render(<Item item={'buy apples'} done={false}/>)
    // our item should have a className todo-item which we can get out firstChild
     expect(container).toHaveClass('todo-item')
  })

  it('Clicked! Should be checked now', () => {
    //  but more of show you how to click an event
    let status = false;
    const toggleClick = jest.fn();
    const { container, getByTestId } = render(<Item item={'buy apples'} done={status} toggleDone={toggleClick}/>)
    const checkbox = getByTestId('checkbox');
    fireEvent.click(checkbox)
    expect(toggleClick).toHaveBeenCalled();
    expect(toggleClick).toHaveBeenCalledTimes(1);
  })


})
```
## Week 9

- Ruby and Rails

- MVC with Rails

```
MVC - What is it?
The Model-View-Controller is a pattern that separates an app into 3 parts:

Model - all data related logic. This can be fetching data from the database, creating queries, etc.

View - all the UI logic of the app. This is how the client/user will view the app itself.

Controller - the logic between the Model and the View. This is where specific buisness logic happens. Controllers get incoming requests, manipulate data ( using Models ), and interact with the Views to render the final output to the 
```
## Week 10

- Whiteboard Interviews

```
Don't Fear the Whiteboard!
The big question before going into a whiteboarding interview you should be asking, is WHY? Why am I doing this? What does this exercise show the company that isn’t already on my resume?

It turns out it’s less about your ability to get the right answer, and more about your problem-solving skills.

What do I do when I'm at the interview ?
1 - Ask Questions

Once you see the question, take a second, to understand what the question is asking, If something is unclear, or you need additional information, you can ask the interviewer for it.

2 - Explain your solution/thought process

After you have a game plan on solving the problem, talk through your solution. Talk it outloud. Being able to explain how you would approach an issue is the first way of showing how your brain thinks, this is great for the interviewer/developer to assess your method of thinking.

How to Practice these
1 - Buy a whiteboard 2 - Simulate an enviroment 3 - Write code without compiling it to assume what needs to happen
```

- Take home assesment
```
Always approach the challenge with a plan. Create little milestones that will get you the final product.

TIME BOX EVERYTHING. Remember, to keep the project within the scope, and once the specs are met, then move on to stretch goals.

This is a great opportunity to learn new libraries, frameworks, and languages. Do not bite off more than you can chew. ( For instance if they ask for a frontend react, and backend to be watver you want it to be, but you learn that the backend of the company is ran on elixir, dont try to learn elixir in a week while trying to do the tech interview, it maybe too much)

ALWAYS take the time to review the requirements and make sure you fully understand them. And, if you have any questions at all, always ask.

Dont code right away!!!! ( YOU ARE NOT READY TO CODE!!!!!!) Remember our 2 lectures? First plan, then user stories, then draw erd, then draw mocks, then start!

Keep in mind that initial setup may take you a good chunk of your time, but it is very important because the intial setup of the project will structure how well everything else onward will go.

What to Do
Understand the requirements and ask any questions

Identify technical decisions you need to make

Technical design & whiteboarding

Test plan

App setup plan

Organize your tasks

Should I add testing?
Why should you include tests in your take-home coding challenge? It’s simple: your tests will make your submission shine.

What questions should i be asking when doing this
Asking yourself: what is the employer really looking to get out of this exercise? Just my coding skills? What about inquiry? Communication? Estimation / scope management?

What position was the challenge for? ( Front, Back, Full Stack )
```
## Week 11
- FINAL PROJECT
## Week 12
- FINAL PROJECT
