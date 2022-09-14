# Exercises 1.6.-1.14

- **NB** Exercises 1.6 - 1.11 were done in the **unicafe folder**
- **NB** Exercises 1.12 - 1.14 were done in the **anecdotes folder**

**WARNING** create-react-app will automatically turn your project into a git-repository unless you create your application inside of an existing git repository. **Most likely you do not want each of your projects to be a separate repository**, so simply run the `rm -rf .git` command at the root of your application.

In some situations you may also have to run the command below from the root of the project:

```js
rm -rf node_modules/ && npm i
```

## 1.6: unicafe step1

Like most companies, Unicafe collects feedback from its customers. Your task is to implement a web application for collecting customer feedback. There are only three options for feedback: good, neutral, and bad.

The application must display the total number of collected feedback for each category. Your final application could look like this:

![Unicafe step1](images/p1d-unicafe_step1.png)

Note that your application needs to work only during a single browser session. Once you refresh the page, the collected feedback is allowed to disappear.

It is advisable to use the same structure that is used in material and previous exercise. File _index.js_ is as follows:

```js
import React from 'react'
import ReactDOM from 'react-dom/client'

import App from './App'

ReactDOM.createRoot(document.getElementById('root')).render(<App />)
```

You can use the code below as a starting point for the _App.js_ file:

```js
import { useState } from 'react'

const App = () => {
  // save clicks of each button to its own state
  const [good, setGood] = useState(0)
  const [neutral, setNeutral] = useState(0)
  const [bad, setBad] = useState(0)

  return (
    <div>
      code here
    </div>
  )
}

export default App
```

## 1.7: unicafe step2

Expand your application so that it shows more statistics about the gathered feedback: the total number of collected feedback, the average score (good: 1, neutral: 0, bad: -1) and the percentage of positive feedback.

![unicafe step2](images/p1d-unicafe_step2.png)

## 1.8: unicafe step3

Refactor your application so that displaying the statistics is extracted into its own _Statistics_ component. The state of the application should remain in the _App_ root component.

Remember that components should not be defined inside other components:

```js
// a proper place to define a component
const Statistics = (props) => {
  // ...
}

const App = () => {
  const [good, setGood] = useState(0)
  const [neutral, setNeutral] = useState(0)
  const [bad, setBad] = useState(0)

  // do not define a component within another component
  const Statistics = (props) => {
    // ...
  }

  return (
    // ...
  )
}
```

## 1.9: unicafe step4

Change your application to display statistics only once feedback has been gathered.

## 1.10: unicafe step5

Let's continue refactoring the application. Extract the following two components:

- _Button_ for defining the buttons used for submitting feedback
- _StatisticLine_ for displaying a single statistic, e.g. the average score.

To be clear: the _StatisticLine_ component always displays a single statistic, meaning that the application uses multiple components for rendering all of the statistics:

```js
const Statistics = (props) => {
  /// ...
  return(
    <div>
      <StatisticLine text="good" value ={...} />
      <StatisticLine text="neutral" value ={...} />
      <StatisticLine text="bad" value ={...} />
      // ...
    </div>
  )
}
```

The application's state should still be kept in the root _App_ component.

## 1.11*: unicafe step6

Display the statistics in an HTML [table](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics), so that your application looks roughly like this:

![unicafe step6](images/p1d-unicafe_step6.png)

Remember to keep your console open at all times. If you see this warning in your console:

![unicafe step6 - warning](images/p1d-unicafe_step6_warning.png)

Then perform the necessary actions to make the warning disappear. Try passing the error message into a search engine if you get stuck.

_Typical source of an error_ `Unchecked runtime.lastError: Could not establish connection. Receiving end does not exist`. _is Chrome extension. Try going to_ `chrome://extensions/` _and try disabling them one by one and refreshing React app page; the error should eventually desappear_.

**Make sure that from now on you don't see any warnings in your console!**

## 1.12*: anecdotes step1

The world of software engineering is filled with [anecdotes](http://www.comp.nus.edu.sg/~damithch/pages/SE-quotes.htm) that distill timeless truths from our field into short one-liners.

Expand the following application by adding a button that can be clicked to display a _random_ anecdote from the field of software engineering:

```js
import { useState } from 'react'

const App = () => {
  const anecdotes = [
    'If it hurts, do it more often.',
    'Adding manpower to a late software project makes it later!',
    'The first 90 percent of the code accounts for the first 10 percent of the development time...The remaining 10 percent of the code accounts for the other 90 percent of the development time.',
    'Any fool can write code that a computer can understand. Good programmers write code that humans can understand.',
    'Premature optimization is the root of all evil.',
    'Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it.',
    'Programming without an extremely heavy use of console.log is same as if a doctor would refuse to use x-rays or blood tests when diagnosing patients.'
  ]
   
  const [selected, setSelected] = useState(0)

  return (
    <div>
      {anecdotes[selected]}
    </div>
  )
}

export default App
```

Content of the file _index.js_ is same as in previous exercises.

Find out how to generate random numbers in JavaScript, eg. via search engine or on [Mozilla Developer Network](https://developer.mozilla.org/). Remember that you can test generating random numbers e.g. straight in the console of your browser.

Your finished application could look something like this:

![anecdotes step1](images/p1d-anecdotes_step1.png)

**WARNING** create-react-app will automatically turn your project into a git-repository unless you create your application inside of an existing git repository. **Most likely you do not want each of your projects to be a separate repository**, so simply run the `rm -rf .git` command at the root of your application.

## 1.13*: anecdotes step2

Expand your application so that you can vote for the displayed anecdote.

![anecdotes step2](images/p1d-anecdotes_step2.png)

**NB** store the votes of each anecdote into an array or object in the component's state. Remember that the correct way of updating state stored in complex data structures like objects and arrays is to make a copy of the state.

You can create a copy of an object like this:

```js
const points = { 0: 1, 1: 3, 2: 4, 3: 2 }

const copy = { ...points }
// increment the property 2 value by one
copy[2] += 1   
```

OR a copy of an array like this:

```js
const points = [1, 4, 6, 3]

const copy = [...points]
// increment the value in position 2 by one
copy[2] += 1 
```

Using an array might be the simpler choice in this case. Searching the Internet will provide you with lots of hints on how to [create a zero-filled array of a desired length](https://stackoverflow.com/questions/20222501/how-to-create-a-zero-filled-javascript-array-of-arbitrary-length/22209781).

## 1.14*: anecdotes step3

Now implement the final version of the application that displays the anecdote with the largest number of votes:

![anecdotes step3](images/p1d-anecdotes_step3.png)

If multiple anecdotes are tied for first place it is sufficient to just show one of them.

This was the last exercise for this part of the course and it's time to push your code to GitHub and mark all of your finished exercises to the [exercise submission system](https://studies.cs.helsinki.fi/stats/courses/fullstackopen).