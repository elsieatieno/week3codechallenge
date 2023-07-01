# week3codechallenge

## Author
-[Elsie Atieno](https://github.com/elsieatieno)

## Objectives
For this code challenge
-See the first movie's details
-See a menu of all movies on the left side of the page
-Buy a ticket for a movie.

## Introduction
For this assessment, you'll be working on Flatdango.
Flatiron Movie Theater is open for business! You will be building out an
application, Flatdango, that allows a user to purchase movie tickets from the
theater.

## Setting up server
First i went to the terminal and installed JSOn server using:
 npm install -g json-server
Second, i got the backend starting using:
 json-server --watch db.json
Third, i visited the server using:

## DOM Manipulation
To achieve this, in the index.js i did the following:
    function displayTitles(movie){
    let titles = document.getElementById('films')
    movie.forEach(movie =>{
        let titleList = document.createElement('li')
        titleList.classList = 'movie_list'
        titleList.innerText = movie.title
        titles.appendChild(titleList)
    })
    }

For the first function titled `displayTitles`, it has a parameter `movie`. It gives titles a variable that `gets the element by id` and the parameter movies takes a method of forEach. The method iterates movie and in it it gives `titleList` a variable that creates a `li` element. The li element takes a class of `movie_list` and its text that is displayed is the titles of the movies. The id with the title films appends the li element created.

    function displayInfo(movie){
    document.querySelector('#title').innerText = movie.title
    document.querySelector('#description').innerText = `Description: ${movie.description}`
    document.querySelector('#runtime span').innerText = `Runtime: ${movie.runtime}`
    document.querySelector('#capacity span').innerText = `Capacity: ${movie.capacity}`
    document.querySelector('#showtime span').innerText = `Showtime: ${movie.showtime}`
    document.querySelector('#tickets span').innerText = `Tickets: ${movie.tickets_sold}`
    document.querySelector('#images').setAttribute('src', movie.poster)
    let btn = document.getElementById('buy_ticket')
    }
For the second function titled `displayInfo`, it has a parameter `movie`. It uses the `.querySelector` to grab the ids of elements in the HTML file. for each of the querySelectors it takes a `.innerText` which displays the info an=bout the movie. It declares a variable named `let` which gets the element by id.

    function buyTicket(){
    let tickets= document.getElementById('available');
    let availableTickets = parseInt(tickets.textContent.split(' ')[2]);
    if (availableTickets > 0) {
        availableTickets--;
        tickets.textContent = `Available Tickets: ${availableTickets}`;
      } else {
        alert('Sorry, the showing is sold out!')
      }
    } 
For the third function titled `buyTicket`, it doesn't take a parameter. It creates a variable `tickets` which uses get elements by id  an another variable `availableTickets` which uses `parseInt` and it takes the tickets variable and adds a `.textContent` which takes a `.split(' ')` meaning it splits the texts into arrays and it takes the second array via `[2]`.

## Events
To achieve this, in the index.js i did the following:
   document.addEventListener('DOMContentLoaded', function(){
    fetchData()
   })
 In this it adds an event listener to the document and it listens for the event type`DOMContentLoaded` and it listens for the function `fetchData()`

   titleList.addEventListener('click', function(){
    fetchInfo(movie)
    })
In this it adds an event listener to the variable declared and it listens for the event type `click` and it listens for the function with the parameter movie as `fetchInfo(movie)`

  btn.addEventListener('click', function(){
    buyTicket()
  })  
In this it adds an event listener to the variable declared and it listens for the event type `click` and it listens for the function `buyTicket()`

## Communicating with the server
To achieve this, in the index.js i did the following:
   function fetchInfo(movie){
    fetch(`http://localhost:3000/films/${movie.id}`)
    .then(res => res.json())
    .then(data => {
        displayInfo(data)
    })
}
For this function titled `fetchInfo(movies)` it takes in movies as the parameter. It first fetches the db.json file `http://localhost:3000/films/${movie.id}`. It then takes a .then which passes response and takes returns the response in accordance to the file type `res.json()`. It then takes another .then which passes the output data and returns it through a function as `displayInfo(data)`

   function fetchData(){
    fetch(`http://localhost:3000/films`)
    .then(res => res.json())
    .then(data => {
        displayTitles(data)
    })
}
For this function titled `fetchData()` it takes in nothing as the parameter. It first fetches the db.json file `http://localhost:3000/films`. It then takes a .then which passes response and takes returns the response in accordance to the file type `res.json()`. It then takes another .then which passes the output data and returns it through a function as `displayTitles(data)`

## Conclusion
In this week's code challenge i have managed to combine the skills i learned in week 1, week 2 and also this week to create this project. I learnt asynchronous javascript, context and algorithms.