
# LAB | Beers

Our end goal is creating something like this:

<div style="display: flex; justify-content: center">
<img src="https://user-images.githubusercontent.com/23629340/45887951-2ca0bb80-bdbd-11e8-91a4-08b66d88a7c7.gif" />
</div>


## Requirements

- Fork this repo
- Clone this repo

## Submission

- Upon completion, run the following commands:

  ```
  git add .
  git commit -m "done"
  git push origin master
  ```

- Create Pull Request so your TAs can check up your work.

## Introduction

We will be building a React app so the API (server) needs to be built somewhere for us, right? You are completely right, it's deployed on *heroku* and the root fo the API is: **`https://punkapi.com/documentation/v2`**.
The available endpoints are the following:

| Method | Endpoint | Response (200)     | Action |
| ------ | -------- | ------------------ | ------ |
| GET    | /     | [beers]            | Get all the beers from the DB |
| GET    | /:id | { beer }        | Get the a single/specific beer      |
| GET    | /random     | { beer }        | Get a random beer from the DB |
| POST   | /new        | { message: "New beer successfully saved to database!"}| Create a new beer (the fields are specified in the instructions)|
| GET    | /search?q=`{query}` | [beers] | Get beers from the DB whose name contains the search term. For example `/search?q=lager` searches for all beers with lager in the name. |


### Pagination
Requests that return multiple items will be limited to 25 results by default. You can access other pages using the `?page` paramater, you can also increase the amount of beers returned in each request by changing the `?per_page` paramater.

```
$ curl https://api.punkapi.com/v2/beers?page=2&per_page=80
```

On each iteration, we will explain which endpoint you should use!

The **Beers** project will include the following features:

- A **Home** page with three different options:
  - *All Beers*
  - *Random Beer*
  - *New Beer*
- A **List Beers** page where you should display all the beers
- A **Single Beer** page to display the details of the beer the user clicked on
- A **Random Beer** page to display a Random Beer
- A **New Beer** page to show a form where a user can create new beers

## Instructions

:exclamation: At the very beginning we will offer you to shoot for the stars: as a **bonus** focus on **mobile first** design! As we said this is bonus, so it's up to you. :+1:

### Iteration 1: Create the App

Well, at this point, this comes natural: we will use `create-react-app` to build a new app. Feel free to name it as you wish, but if you need some inspiration, we called it **Reactive BeersJS**.

### Iteration 2: Home Page

Create a **Home Page**. This view should include three links to separate pages:

- `/beers`
- `/random-beer`
- `/new-beer`

Feel free to design it however you wish, but here is how we did it:

<div style="display: flex; justify-content: center">
<img src="https://user-images.githubusercontent.com/23629340/40706572-933439b8-63ee-11e8-8d65-538fb59f79ab.png" height="600px" />
</div>

### Iteration 3: Header

On every view (except for the `home`), we should add a **header** with a `link` to the root of the `app`.

<div style="display: flex; justify-content: center">
<img src="https://user-images.githubusercontent.com/23629340/40707029-cb2fce12-63ef-11e8-939c-f673ff3b965d.png" height="100px" />
</div>

### Iteration 4: List the Beers

On the `/beers` route, we should display all the beers from the database. So, in this case, you need to "hit" the API's route `https://ih-beer-api.herokuapp.com/beers` and the API will return an **array of beers**.

*Hint*: The array of beers is array of objects. We strongly advise you to **console log the response** from the API so you can see the structure of it.

You should display the following from each of the beers:
  - `image`
  - `name`
  - `tagline`
  - `contributed_by`
  - **Also, add the link to check the details of each beer. The link should navigate to `/beers/:beerId`.**

<div style="display: flex; justify-content: center">
<img src="https://user-images.githubusercontent.com/23629340/40706960-96223ade-63ef-11e8-9375-b7b6d091e716.png" height="600px" />
</div>

The first time you call the API, it might take a bit to respond. It's hosted on Heroku, and it goes to sleep after 30 minutes, you know! :wink:


### Iteration 5: Single Beer

When a user click on one of the beers, you should display a detailed view of it, including the following fields:

  - `image`
  - `name`
  - `tagline`
  - `first_brewed`
  - `attenuation_level`
  - `description`
  - `contributed_by`

Again, we **strongly recommend to console log the response from the API**.

<div style="display: flex; justify-content: center">
<img src="https://user-images.githubusercontent.com/23629340/40707269-84bedd78-63f0-11e8-86c3-b14efb9323a7.png" height="600px" />
</div>

### Iteration 6: Random Beer

On the `/random-beer` route, we will render a single beer that will be retrieved from the database. The endpoint will do all the job for us, all we need to do is to call `https://ih-beer-api.herokuapp.com/beers/random`. We should receive an object including all the info about a beer.
The same way we did with the **Single Beer** view, we should render the following fields:

  - `image`
  - `name`
  - `tagline`
  - `first_brewed`
  - `attenuation_level`
  - `description`
  - `contributed_by`

<div style="display: flex; justify-content: center">
<img src="https://user-images.githubusercontent.com/23629340/40707457-05a22990-63f1-11e8-84b2-a86143b7b821.png" height="600px" />
</div>

### (Extra) Bonus Iteration: Filter the Beers

Yes! One endpoint left! On the `/beers` route, add an `input` where users can search for beers. Every time a new letter is typed, you should call to `https://ih-beer-api.herokuapp.com/beers/search?q={query}` passing the value of the input in the `q` param.

**We are done!** :trophy:

Awesome! Grab a beer (if you're not underage :wink: )! Now you are a **React Warrior**, keep training to become the Ninja!


Happy coding! :heart:
