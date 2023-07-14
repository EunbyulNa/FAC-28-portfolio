# Testing portfolio

## 1. Check that passing a given input into our tests returns the expected output

We used `test.helper.js`. Each test case has an expected result that is compared to the actual result of the code being tested using the equal or notEqual assertion methods.

For example, in the test case test`('Passing test: Adding 1st task replaces the placeholder', () => { ... })`, the input is the user-entered task title and description, and the expected output is that the placeholder task in the tasks array should be replaced by the user-entered task. The test checks whether the actual result (the task at index 0 in the tasks array) is not equal to the placeholder task, indicating that the task has been added successfully.

Similarly, other test cases in the code have expected results defined, and the tests compare those expected results with the actual results to ensure that the code behaves as expected.

## 2. Write tests to mimic the behaviour of a user performing different actions

```js
test('Update list to be completed, () => { 
  //Get completed icon
  const completedIcon= document.querySelector('.completed-icon');

  //Create mock Event, event object, modify target property
  const mockEvent = {
  target: completedIcon
  };
  //Execute changeToCompleted with mockevent object parameter
  changeToCompleted(mockEvent);
  const checkCompleted = completedIcon.parentElement.parentElement.firstElementChild;
  const actualAfter = checkCompleted.classList.contains('line-through');
  //Check class list contain line-through 
  equal(actualAfter, true);
  //Reset classList
  checkCompleted.classList.remove('line-through');
});
```
This test simulates the user clicking on a completed icon. The test creates a mock event object with the target set to the completed icon and calls the changeToCompleted function with this mock event object. After that, the test checks whether the task is marked as completed by verifying that the relevant CSS class (line-through) is added to the task's element

## 3. Write testable, modular functions
Each function in the code has a specific responsibility and performs a well-defined task. For example, `renderTasksDOM()` is responsible for rendering tasks in the DOM, `openCreateTaskPopUp()` handles the opening of the create task pop-up, `addUserTask()` adds a user task to the tasks array, and so on. This modular approach allows for easier testing and maintenance of the codebase.


## 4. Write functions that add, remove or modify DOM nodes

1. `renderTasksDOM()`: This function is responsible for rendering tasks in the DOM. It generates HTML code for each task and inserts it into the taskContainer element using `insertAdjacentHTML()`. It adds new task elements to the DOM.

2. `openCreateTaskPopUp(), cloaseAddPopUp()`: This function displays the create task pop-up by setting the display property of addTaskPop element to 'grid' or 'none'. It modifies the DOM by showing or hiding the pop-up.

3. `addUserTask()`: This function adds a user task to the tasks array and updates the DOM accordingly. It creates a new task object with user-provided values, pushes it to the tasks array, and then calls `renderTasksDOM()` to update the DOM with the new task.

4. `deleteTask(e)`: This function removes a task from the DOM when the delete icon is clicked. It accesses the parent elements of the delete icon using parentElement and calls the remove() method to delete the corresponding task element from the DOM.


## 5. Apply event listeners to HTML form elements

1. `addTaskForm.addEventListener('submit', (e) => {...})`: This event listener is applied to the submit event of the addTaskForm form element. It listens for form submission and prevents the default form submission behavior. The listener function handles the form submission by calling the `addUserTask()` function.

2. `addTaskBtn.addEventListener('click', (event) => {...})`: This event listener is applied to the click event of the addTaskBtn element. It listens for a click on the button and triggers the listener function, which calls the `openCreateTaskPopUp()` function to open the create task pop-up.

3. `toggleSwitch.addEventListener('click', showOutStanding)`: This event listener is applied to the click event of the toggleSwitch element. It listens for a click on the toggle switch and triggers the showOutStanding() function, which handles the logic for showing or hiding completed tasks based on the switch state.


## 6. Use scope to control what variables are accessible inside functions and blocks

1. Function Scope: Variables declared within functions have function scope, meaning they are only accessible within that function. For example, variables like taskItemHTML, addUserTask, and activateUserControls are defined within the renderTasksDOM function and can only be accessed within that function.

2. Block Scope: Variables declared within blocks (e.g., if statements, for loops) have block scope, meaning they are only accessible within that block. For instance, variables like checkCompleted and checkCompletedElement are defined within the changeToCompleted function block and can only be accessed within that block.

3. Global Scope: Variables declared outside of any function or block have global scope, meaning they are accessible throughout the entire code. For example, variables like tasks, taskContainer, and toggleSwitch are defined outside of any function and can be accessed by any function within the code.


## 7. Use CSS grid to create complex layouts

```css
.item-list {
    cursor: pointer;
    grid-template-columns: 4fr 0.7fr;
    padding: 1em 0;
}
```

We made an item-list as a grid display. 

## 8. Use CSS grid to make layouts that adapt to the viewport size

```css
@media (min-width: 300px) {
    .header { padding:var(--s-spacing); }
    .title-container{text-align: center;}
    .list-type-container { grid-template-columns: repeat(2, 1fr); }
    .card {padding: 1rem};
  }

  @media (min-width: 600px) {

    .title-container{ text-align: center;}
    .list-type-container  { grid-template-columns: repeat(3, 1fr); }
    
  }

  @media (min-width: 768px) {
    .list-type-container  { grid-template-columns: repeat(3, 1fr); }
    .card {padding: 2rem};
  }
```

The grid-template-columns property is used in the media queries for specific breakpoints, such as min-width: 300px and min-width: 600px, to adjust the number of columns based on the viewport width.
