# Calorie-Counter
Sometimes when you're coding a web application, you'll need to be able to accept input from a user. In this calorie counter project, you'll learn how to validate user input, perform calculations based on that input, and dynamically update your interface to display the results.

In this practice project, you'll learn basic regular expressions, template literals, the addEventListener() method, and more.

		HTML:

With the HTML boilerplate add a form element and give it an id set to calorie-counter.

Create a label element, give it a for attribute set to budget and the text Budget, then create an input element with the id set to budget.

Your input element needs some additional attributes. Give it a type set to number to only allow numeric inputs, a min attribute set to 0 to only allow positive numbers, and a placeholder set to Daily calorie budget.

Finally, mark the input element as required.

Create a fieldset element with the id set to breakfast.

Within that element, create a legend with the text Breakfast, and an empty div with the class set to input-container.

Now create a fieldset with an id set to lunch, and a corresponding legend and div element.

Continuing the pattern, create a fieldset for dinner with the same nested elements.

You need two more of these fieldset code blocks – one for snacks and one for exercise.

Create a div and give it a class set to controls. Nest a span element within that div.

In your span element, create a label element for an entry-dropdown and give it the text Add food or exercise:. Then create a select element with the id set to entry-dropdown and a name set to options. Below that, add a button element with the id set to add-entry and the text Add Entry.

Give your button element a type attribute set to button to prevent automatic form submission.

Your select menu needs options for each of the food and exercise fieldset elements you created in the previous steps. Use the option element to create a new option for each fieldset. The value attribute of each option should be the id of the fieldset, and the text of each option should be the text of the legend.

Set the Breakfast option as the selected option.

Create another div element. Within it, nest a button to submit the form. This button should have the text Calculate Remaining Calories.

Then add a button with the id set to clear to clear the form (don't forget to give it a type attribute that prevents it from submitting the form). This button needs the text Clear.

Your form needs somewhere to display the results. Add an empty div element and give it an id of output and the class values of output and hide.

Finally, you need to link your JavaScript file to your HTML. Create a script element to do so.


		JavaScript:

Begin by getting the form element (using the id) and storing it in a variable called calorieCounter.

Get your #budget element and assign it to budgetNumberInput, and your #entry-dropdown element and assign it to entryDropdown.

Following the same pattern, assign your #add-entry element to addEntryButton, your #clear element to clearButton, and your #output element to output.

Declare an isError variable and set it to false, but use let so you can reassign it later.

Declare a cleanInputString function that takes a str parameter.

Split the string passed into the cleanInputString function into an array of individual characters and assign it to a variable named strArray.

Declare a cleanStrArray variable and assign it an empty array. You will use this to store your valid number characters.

Use a for loop to iterate through each character in your strArray array.

Within your loop, you need to check if the character in strArray at index i is not a +, -, or a space. If it is not, push it to the cleanStrArray.

Remove your existing code within the cleanInputString function. Declare a regex variable.

You want to look for +, -, or spaces. Replace the pattern in your regex variable with \+- to look for plus and minus characters.

The character class \s will match any whitespace character. Add this to your regex pattern.

Turn your +-\s pattern into a character class.

Add the g flag to your regex pattern.

Use your regex to replace all instances of +, -, and a space in str with an empty string. Return this value.

Create a function called isInvalidInput – it should take a single str parameter.

Declare a regex variable, and assign it a regex that matches the character e.

This flag makes your pattern case-insensitive. Add the i flag to your regex pattern. 

To match any number, you can use the character class [0-9]. This will match any digit between 0 and 9.

Add this character class before and after e in your pattern.

To match your digit pattern one or more times, add a plus after each of the digit character classes. For example: [0-9]+.

There is a shorthand character class to match any digit: \d. Replace your [0-9] character classes with this shorthand.

Return the result of calling the .match() method on str and passing your regex variable as the argument. You'll use this match result later on.

Declare an empty function addEntry. This function should not take any parameters.

Use concatenation to add a # to the beginning of the value property of entryDropdown, and assign that result to a targetId variable.

Now you need to target the .input-container element within the element that has your targetId. Declare a new targetInputContainer variable, and assign it the value of document.querySelector(). Use concatenation to separate targetId and '.input-container' with a space, and pass that string to querySelector().

Replace your concatenated string in the querySelector with a template literal – be sure to keep the space between your targetId variable and .input-container.

Thanks to template literals, you actually don't need the targetId variable at all. Remove that variable, and update your template literal to replace targetId with entryDropdown.value – remember to add # before that, in the string.

Declare an entryNumber variable and give it the value of targetInputContainer.querySelectorAll(). You do not need to pass an argument to the query selector yet.

Pass the string input[type="text"] to the querySelectorAll() method. 

Return a NodeList of all the text inputs in the form. You can then access the length property of the NodeList to get the number of entries. Do this on the same line.

Now you need to build your dynamic HTML string to add to the webpage. Declare a new HTMLString variable, and assign it an empty template literal string.

Start your HTMLString with a new line, then create a label element. Give that element the text Entry # Name, using your template literal syntax to replace # with the value of entryNumber

Give your label element a for attribute with the value X-#-name, where X is the value of the entryDropdown element and # is the value of entryNumber. Remember that HTML attributes should be wrapped in double quotes.

After your label element, and on a new line in your template string, create an input element. Give it a type attribute set to text, a placeholder attribute set to Name, and an id attribute that matches the for attribute of your label element.

Create another label element (on a new line) at the end of your HTMLString. This label should have the text Entry # Calories, using your template literal syntax to replace # with the value of entryNumber, and the for attribute set to X-#-calories, where X is the value of entryDropdown and # is the value of entryNumber.

Finally, on a new line after your second label, create another input element. Give this one a type attribute set to number, a min attribute set to 0 (to ensure negative calories cannot be added), a placeholder attribute set to Calories, and an id attribute that matches the for attribute of your second label element.

Add your new HTMLString to the targetInputContainer by using the innerHTML property. Remember to use the += operator to add to the existing HTML instead of replacing it.

Call the .addEventListener() method of the addEntryButton. It takes two arguments. The first is the event to listen to – you should pass the string click. The second is the callback function, or the function that runs when the event is triggered. Pass the addEntry function as the second argument. Note that you should not call addEntry, but pass the variable (or function reference) directly.

the first entry should have a count of 1, not 0.
This bug occurs because you are querying for input[type="text"] elements before adding the new entry to the page. To fix this, update your entryNumber variable to be the value of the length of the query plus 1. Add this on your declaration line, not in your template strings.

Change your innerHTML assignment to use the insertAdjacentHTML() method of targetInputContainer instead. Do not pass any arguments yet.

For the first argument, pass the string beforeend to insert the new element as the last child of targetInputContainer.

For the second argument, pass your HTMLString variable.

Declare a getCaloriesFromInputs function, and give it a parameter called list.

In your new function, declare a calories variable and assign it the value 0. Use let to declare it, since you will be reassigning it later.

Create a for loop. Your iterator i should start at 0, continue while it is less than the length of the list, and increment by 1 each iteration.

Assign the value of the element in list at index i to a variable called currVal.

Update your currVal declaration to be the result of calling cleanInputString with list[i].value.

You also need to confirm the input is valid. Declare an invalidInputMatch variable, and assign it the result of calling your isInvalidInput function with currVal as the argument.

Add an if statement that checks if invalidInputMatch is truthy.

Using a template literal, in your if block, call the alert() function to tell the user Invalid Input: , followed by the first value in the invalidInputMatch array.

Still within your if block, set isError to true and return null.

Use the addition assignment operator to add currVal to your calories total. You'll need to use the Number constructor to convert currVal to a number.

The Number constructor is a function that converts a value to a number. If the value cannot be converted, it returns NaN

After your for loop has completed, return the calories value.

Now it's time to start putting it all together. Declare an empty calculateCalories function, which takes a parameter named e.

Add a line to your calculateCalories function that calls the preventDefault() method on the e parameter. Then, reset your global error flag to false.

Declare a breakfastNumberInputs variable, and give it the value of calling document.querySelectorAll() with the selector #breakfast input[type=number]. This will return any number inputs that are in the #breakfast element.

Using that same syntax, query your number inputs in the #lunch element and assign them to lunchNumberInputs.

Following the same pattern, query for your number inputs in the #dinner, #snacks, and #exercise elements. Assign them to variables following the naming scheme of the previous two.

Declare a breakfastCalories variable, and assign it the result of calling getCaloriesFromInputs with breakfastNumberInputs as the argument

Now declare a lunchCalories variable, and give it the value of calling getCaloriesFromInputs with your lunchNumberInputs.

Following this same pattern, declare variables for the number inputs in the #dinner, #snacks, and #exercise elements. Assign them the appropriate getCaloriesFromInputs calls.

Declare a budgetCalories variable and set it to the result of calling getCaloriesFromInputs – pass an array containing your budgetNumberInput as the argument.

Your getCaloriesFromInputs function will set the global error flag to true if an invalid input is detected. Add an if statement to your calculateCalories function that checks the truthiness of your global error flag, and if it is truthy then use return to end the function execution.

t is time to start preparing your calculations. Start by declaring a consumedCalories variable, and assign it the sum of breakfastCalories, lunchCalories, dinnerCalories, and snacksCalories (note that order matters for the tests). Be sure to do this after your if statement.

Now declare a remainingCalories variable, and give it the value of subtracting consumedCalories from budgetCalories and adding exerciseCalories.

You need to know if the user's calories are a surplus or a deficit. Declare a surplusOrDeficit variable.

Use a ternary operator to set surplusOrDeficit to the string Surplus or Deficit depending on whether remainingCalories is greater than or equal to 0. If it is greater than or equal to 0, then surplusOrDeficit should be Surplus. Otherwise, it should be Deficit.

You need to construct the HTML string that will be displayed in the output element. Start by assigning an empty template literal to the innerHTML property of the output element.

Your output.innerHTML string will need a span element. Create that, and give it a class attribute set to the surplusOrDeficit variable, but lowercased.

Strings have a .toLowerCase() method that can help you with this. Do not give your span any text yet.

Give your span the text remainingCalories Calorie surplusOrDeficit, using interpolation to replace remainingCalories and surplusOrDeficit with the appropriate variables.

When the user has a calorie deficit, the remainingCalories value will be negative. You don't want to display a negative number in the result string.

Math.abs() is a built-in JavaScript method that will return the absolute value of a number. In your span text, wrap your remainingCalories reference in Math.abs() to ensure that the value is positive.

After your span element, add an hr element to create a horizontal line.

To keep your code clean and readable, you should add this on a new line in the template literal.

Now create a p element with the text budgetCalories Calories Budgeted, using interpolation to replace budgetCalories with the appropriate variable.

This should come after your hr element.

Using the same interpolation syntax, add a second p element with the text consumedCalories Calories Consumed and a third with the text exerciseCalories Calories Burned. Remember to replace your consumedCalories and exerciseCalories variables with the appropriate values.

Finally, you need to make the #output element visible so the user can see your text. Your output variable is an Element, which has a classList property. This property has a .remove() method, which accepts a string representing the class to remove from the element.

Use the .remove() method of the output variable's classList property to remove the hide class. Don't forget to place the word hide inside quotes.

Add an event listener to your calorieCounter element. The event type should be submit, and the callback function should be calculateCalories.

Your final feature to add is the ability for a user to clear the form. Start by declaring an empty function called clearForm – it should not take any arguments.

You need to get all of the input containers. Declare an inputContainers variable, and assign it to the value of querying the document for all elements with the class input-container.

Remember that document.querySelectorAll returns a NodeList, which is array-like but is not an array. However, the Array object has a .from() method that accepts an array-like and returns an array. This is helpful when you want access to more robust array methods, which you will learn about in a future project.

Wrap your inputContainers query selector in Array.from(). Do this on the same line as your declaration.

It is time for another loop. Use a for loop to iterate through the inputContainers array.

Inside the loop, set the innerHTML property of the element at the current index to an empty string. This will clear all of the contents of that input container.

After your loop completes, you need to clear the budgetNumberInput. Set the value property of budgetNumberInput to an empty string.

You also need to clear the output element's text. You can do this by setting the innerText property to an empty string.

The difference between innerText and innerHTML is that innerText will not render HTML elements, but will display the tags and content as raw text.

To finish off this function, you need to restore the hide class to the output element. The classList property has an .add() method which is the opposite of the .remove() method. It accepts a string representing the class to add to the element.

Add the hide class to your output.

To complete this project, add an event listener to the clearButton button. When the button is clicked, it should call the clearForm function.
