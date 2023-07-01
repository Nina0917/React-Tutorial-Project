# Notes of Completing React Tutorial Tic-Tac-Toe

Here is the link: https://react.dev/learn/tutorial-tic-tac-toe

<br>

---

## SSH key not working
I have generated a ssh key under ~/.ssh
Use that one instead of creating new one.

## <></> not support

Fragment syntax is only supported by Babel v7.0.0-beta.31 & above.

- To check global version of Babel:

```css
babel --version
```

- To check the local version of Babel within your project

```css
npx babel --version
```

<br>

---

## ::after

It creates a pseudo-element that is the last child of the selected element. It is inline by default.

<br>

---

## slice()

```javascript
const numbers = [1, 2, 3, 4, 5];
const arr = numbers.slice();
console.log(arr); // [1, 2, 3, 4, 5]
```

<br>

---

## When state changes, what happen to the component

The component and its child component will re-render again.

<br>

---

## How to check if element is null?

```javascript
const numbers = [null, 1, 2];
numbers[0]; // return false
```

<br>

---

## Game Component:

State Variables:

- history

  start:

```
[
    [null, null, null, null, null, null, null, null, null]
]
```

When use clicks Square, update.

- currentMove
  start: 0

When user clicks square, add 1.

When use clicks previous history, it becomes the historical move's index.

<br>

---

## Completing the Game Practice

Lifting state up:

Now every &lt;Square> has a state. Lift states up to the parent component &lt;Board>.

- hint1: You need a array with length 9 to store evry state of each Square component.
- hint2: Now the state variable is inside Board, you also need to lift up click function.

<br>

Now handleClick function does not have paramater. Add paramter i, which represents the index of each Square component.

- hint1: change onSquareClick on every Square component. Make it call handleClick(0), handleClick(1), etc.

<br>

Add state variable xIsNext to determine next step is 'X' or 'O'.

<br>

Add function calculateWinner(Squares) to show when players win. Display text such as “Winner: X” or “Winner: O”. If nobody wins, display "Next player: X" or "Next player: O".

- hint1: you should initiate two variables: winner and status. \
- hint2: The &lt;div className="status">{status}&lt;/div> element will be re-rendered because the status variable is updated based on the new state of squares and xIsNext. The text inside the <div> will reflect the new status.

<br>

Lift things up again to the Game component. Store all squares within a array called history.

- hint1: now you can remove state variable squares.
- hint2: you don't need to move handleClick function but you do need to call setXIsNext or setHistory in Game component, where state variables: history and xIsNext are defined.

<br>

Showing the past moves. Start with "1. Go to game start". Then display "Go to move #1", "Go to move #2", etc.

- hint1: use map
- hint2: use &lt;button> inside &lt;li>

<br>

Add onClick to buttons of past moves. When user clicks it, it can go back to the corresponding state.

- hint1: after call setHistory(newHistory), the history variable does not change immediately. This is because state updates in React are asynchronous. When setHistory is called, React schedules the state update, and the new state value is not immediately available in the subsequent lines of code.
