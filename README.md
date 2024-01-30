# Calorie-Counter
Sometimes when you're coding a web application, you'll need to be able to accept input from a user. In this calorie counter project, you'll learn how to validate user input, perform calculations based on that input, and dynamically update your interface to display the results.

In this practice project, you'll learn basic regular expressions, template literals, the addEventListener() method, and more.
		HTML:
	
 	• Step 1:
With the HTML boilerplate add a form element and give it an id set to calorie-counter.

	• Step 2:
Create a label element, give it a for attribute set to budget and the text Budget, then create an input element with the id set to budget.

	• Step 3:
Your input element needs some additional attributes. Give it a type set to number to only allow numeric inputs, a min attribute set to 0 to only allow positive numbers, and a placeholder set to Daily calorie budget.

Finally, mark the input element as required.

	• Step 4:
Create a fieldset element with the id set to breakfast.

Within that element, create a legend with the text Breakfast, and an empty div with the class set to input-container.

	• Step 5:
Now create a fieldset with an id set to lunch, and a corresponding legend and div element.

	• Step 6:
Continuing the pattern, create a fieldset for dinner with the same nested elements.

	• Step 7:
You need two more of these fieldset code blocks – one for snacks and one for exercise.

	• Step 8:
Create a div and give it a class set to controls. Nest a span element within that div.

	• Step 9:
In your span element, create a label element for an entry-dropdown and give it the text Add food or exercise:. Then create a select element with the id set to entry-dropdown and a name set to options. Below that, add a button element with the id set to add-entry and the text Add Entry.

Give your button element a type attribute set to button to prevent automatic form submission.

	• Step 10:
Your select menu needs options for each of the food and exercise fieldset elements you created in the previous steps. Use the option element to create a new option for each fieldset. The value attribute of each option should be the id of the fieldset, and the text of each option should be the text of the legend.

Set the Breakfast option as the selected option.

	• Step 11:
Create another div element. Within it, nest a button to submit the form. This button should have the text Calculate Remaining Calories.

Then add a button with the id set to clear to clear the form (don't forget to give it a type attribute that prevents it from submitting the form). This button needs the text Clear.

	• Step 12:
Your form needs somewhere to display the results. Add an empty div element and give it an id of output and the class values of output and hide.

	• Step 13:
Finally, you need to link your JavaScript file to your HTML. Create a script element to do so.


		JavaScript:

	• Step 14:
Begin by getting the form element (using the id) and storing it in a variable called calorieCounter.

	• Step 15:
Get your #budget element and assign it to budgetNumberInput, and your #entry-dropdown element and assign it to entryDropdown.

	• Step 16:
Following the same pattern, assign your #add-entry element to addEntryButton, your #clear element to clearButton, and your #output element to output.

	• Step 17:
Declare an isError variable and set it to false, but use let so you can reassign it later.

	• Step 18:
Declare a cleanInputString function that takes a str parameter.

	• Step 19:
Split the string passed into the cleanInputString function into an array of individual characters and assign it to a variable named strArray.

	• Step 20:
Declare a cleanStrArray variable and assign it an empty array. You will use this to store your valid number characters.

	• Step 21:
Use a for loop to iterate through each character in your strArray array.

	• Step 22:
Within your loop, you need to check if the character in strArray at index i is not a +, -, or a space. If it is not, push it to the cleanStrArray.

	• Step 23:
Remove your existing code within the cleanInputString function. Declare a regex variable.

	• Step 24:
You want to look for +, -, or spaces. Replace the pattern in your regex variable with \+- to look for plus and minus characters.

	• Step 25:
The character class \s will match any whitespace character. Add this to your regex pattern.

	• Step 26:
Turn your +-\s pattern into a character class.

	• Step 27:
Add the g flag to your regex pattern.

	• Step 28:
Use your regex to replace all instances of +, -, and a space in str with an empty string. Return this value.

	• Step 29:
Create a function called isInvalidInput – it should take a single str parameter.

	• Step 30:
Declare a regex variable, and assign it a regex that matches the character e.

	• Step 31:
This flag makes your pattern case-insensitive. Add the i flag to your regex pattern. 

	• Step 32:
To match any number, you can use the character class [0-9]. This will match any digit between 0 and 9.

Add this character class before and after e in your pattern.

	• Step 33:
To match your digit pattern one or more times, add a plus after each of the digit character classes. For example: [0-9]+.

	• Step 34:
There is a shorthand character class to match any digit: \d. Replace your [0-9] character classes with this shorthand.

	• Step 35:
Return the result of calling the .match() method on str and passing your regex variable as the argument. You'll use this match result later on.

	• Step 36:
Declare an empty function addEntry. This function should not take any parameters.

	• Step 37:
Use concatenation to add a # to the beginning of the value property of entryDropdown, and assign that result to a targetId variable.

	• Step 38:
Now you need to target the .input-container element within the element that has your targetId. Declare a new targetInputContainer variable, and assign it the value of document.querySelector(). Use concatenation to separate targetId and '.input-container' with a space, and pass that string to querySelector().

	• Step 39:
Replace your concatenated string in the querySelector with a template literal – be sure to keep the space between your targetId variable and .input-container.

	• Step 40:
Thanks to template literals, you actually don't need the targetId variable at all. Remove that variable, and update your template literal to replace targetId with entryDropdown.value – remember to add # before that, in the string.

	• Step 41:
Declare an entryNumber variable and give it the value of targetInputContainer.querySelectorAll(). You do not need to pass an argument to the query selector yet.

	• Step 42:
Pass the string input[type="text"] to the querySelectorAll() method. 

Return a NodeList of all the text inputs in the form. You can then access the length property of the NodeList to get the number of entries. Do this on the same line.

	• Step 43:
Now you need to build your dynamic HTML string to add to the webpage. Declare a new HTMLString variable, and assign it an empty template literal string.

	• Step 44:
Start your HTMLString with a new line, then create a label element. Give that element the text Entry # Name, using your template literal syntax to replace # with the value of entryNumber

	• Step 45:
Give your label element a for attribute with the value X-#-name, where X is the value of the entryDropdown element and # is the value of entryNumber. Remember that HTML attributes should be wrapped in double quotes.

	• Step 46:
After your label element, and on a new line in your template string, create an input element. Give it a type attribute set to text, a placeholder attribute set to Name, and an id attribute that matches the for attribute of your label element.

	• Step 47:
Create another label element (on a new line) at the end of your HTMLString. This label should have the text Entry # Calories, using your template literal syntax to replace # with the value of entryNumber, and the for attribute set to X-#-calories, where X is the value of entryDropdown and # is the value of entryNumber.

	• Step 48:
Finally, on a new line after your second label, create another input element. Give this one a type attribute set to number, a min attribute set to 0 (to ensure negative calories cannot be added), a placeholder attribute set to Calories, and an id attribute that matches the for attribute of your second label element.

	• Step 49:
Add your new HTMLString to the targetInputContainer by using the innerHTML property. Remember to use the += operator to add to the existing HTML instead of replacing it.

	• Step 50:
Call the .addEventListener() method of the addEntryButton. It takes two arguments. The first is the event to listen to – you should pass the string click. The second is the callback function, or the function that runs when the event is triggered. Pass the addEntry function as the second argument. Note that you should not call addEntry, but pass the variable (or function reference) directly.

	• Step 51:
the first entry should have a count of 1, not 0.
This bug occurs because you are querying for input[type="text"] elements before adding the new entry to the page. To fix this, update your entryNumber variable to be the value of the length of the query plus 1. Add this on your declaration line, not in your template strings.

	• Step 52:
Change your innerHTML assignment to use the insertAdjacentHTML() method of targetInputContainer instead. Do not pass any arguments yet.

	• Step 53:
For the first argument, pass the string beforeend to insert the new element as the last child of targetInputContainer.

For the second argument, pass your HTMLString variable.

	• Step 54:
Declare a getCaloriesFromInputs function, and give it a parameter called list.

	• Step 55:
In your new function, declare a calories variable and assign it the value 0. Use let to declare it, since you will be reassigning it later.

	• Step 56:
Create a for loop. Your iterator i should start at 0, continue while it is less than the length of the list, and increment by 1 each iteration.

	• Step 57:
Assign the value of the element in list at index i to a variable called currVal.

	• Step 58:
Update your currVal declaration to be the result of calling cleanInputString with list[i].value.

	• Step 59:
You also need to confirm the input is valid. Declare an invalidInputMatch variable, and assign it the result of calling your isInvalidInput function with currVal as the argument.

	• Step 60:
Add an if statement that checks if invalidInputMatch is truthy.

	• Step 61:
Using a template literal, in your if block, call the alert() function to tell the user Invalid Input: , followed by the first value in the invalidInputMatch array.

	• Step 62:
Still within your if block, set isError to true and return null.

	• Step 63:
Use the addition assignment operator to add currVal to your calories total. You'll need to use the Number constructor to convert currVal to a number.

The Number constructor is a function that converts a value to a number. If the value cannot be converted, it returns NaN

	• Step 64:
After your for loop has completed, return the calories value.

	• Step 65:
Now it's time to start putting it all together. Declare an empty calculateCalories function, which takes a parameter named e.

	• Step 66:
Add a line to your calculateCalories function that calls the preventDefault() method on the e parameter. Then, reset your global error flag to false.

	• Step 67:
Declare a breakfastNumberInputs variable, and give it the value of calling document.querySelectorAll() with the selector #breakfast input[type=number]. This will return any number inputs that are in the #breakfast element.

	• Step 68:
Using that same syntax, query your number inputs in the #lunch element and assign them to lunchNumberInputs.

	• Step 69:
Following the same pattern, query for your number inputs in the #dinner, #snacks, and #exercise elements. Assign them to variables following the naming scheme of the previous two.

	• Step 70:
Declare a breakfastCalories variable, and assign it the result of calling getCaloriesFromInputs with breakfastNumberInputs as the argument

	• Step 71:
Now declare a lunchCalories variable, and give it the value of calling getCaloriesFromInputs with your lunchNumberInputs.

	• Step 72:
Following this same pattern, declare variables for the number inputs in the #dinner, #snacks, and #exercise elements. Assign them the appropriate getCaloriesFromInputs calls.

	• Step 73:
Declare a budgetCalories variable and set it to the result of calling getCaloriesFromInputs – pass an array containing your budgetNumberInput as the argument.

	• Step 74:
Your getCaloriesFromInputs function will set the global error flag to true if an invalid input is detected. Add an if statement to your calculateCalories function that checks the truthiness of your global error flag, and if it is truthy then use return to end the function execution.

	• Step 75:
t is time to start preparing your calculations. Start by declaring a consumedCalories variable, and assign it the sum of breakfastCalories, lunchCalories, dinnerCalories, and snacksCalories (note that order matters for the tests). Be sure to do this after your if statement.

	• Step 76:
Now declare a remainingCalories variable, and give it the value of subtracting consumedCalories from budgetCalories and adding exerciseCalories.

	• Step 77:
You need to know if the user's calories are a surplus or a deficit. Declare a surplusOrDeficit variable.

Use a ternary operator to set surplusOrDeficit to the string Surplus or Deficit depending on whether remainingCalories is greater than or equal to 0. If it is greater than or equal to 0, then surplusOrDeficit should be Surplus. Otherwise, it should be Deficit.

	• Step 78:
You need to construct the HTML string that will be displayed in the output element. Start by assigning an empty template literal to the innerHTML property of the output element.

	• Step 79:
Your output.innerHTML string will need a span element. Create that, and give it a class attribute set to the surplusOrDeficit variable, but lowercased.

Strings have a .toLowerCase() method that can help you with this. Do not give your span any text yet.

	• Step 80:
Give your span the text remainingCalories Calorie surplusOrDeficit, using interpolation to replace remainingCalories and surplusOrDeficit with the appropriate variables.

	• Step 81:
When the user has a calorie deficit, the remainingCalories value will be negative. You don't want to display a negative number in the result string.

Math.abs() is a built-in JavaScript method that will return the absolute value of a number. In your span text, wrap your remainingCalories reference in Math.abs() to ensure that the value is positive.

	• Step 82:
After your span element, add an hr element to create a horizontal line.

To keep your code clean and readable, you should add this on a new line in the template literal.

	• Step 83:
Now create a p element with the text budgetCalories Calories Budgeted, using interpolation to replace budgetCalories with the appropriate variable.

This should come after your hr element.

	• Step 84:
Using the same interpolation syntax, add a second p element with the text consumedCalories Calories Consumed and a third with the text exerciseCalories Calories Burned. Remember to replace your consumedCalories and exerciseCalories variables with the appropriate values.

	• Step 85:
Finally, you need to make the #output element visible so the user can see your text. Your output variable is an Element, which has a classList property. This property has a .remove() method, which accepts a string representing the class to remove from the element.

Use the .remove() method of the output variable's classList property to remove the hide class. Don't forget to place the word hide inside quotes.

	• Step 86:
Add an event listener to your calorieCounter element. The event type should be submit, and the callback function should be calculateCalories.

	• Step 87:
Your final feature to add is the ability for a user to clear the form. Start by declaring an empty function called clearForm – it should not take any arguments.

	• Step 88:
You need to get all of the input containers. Declare an inputContainers variable, and assign it to the value of querying the document for all elements with the class input-container.

	• Step 89:
Remember that document.querySelectorAll returns a NodeList, which is array-like but is not an array. However, the Array object has a .from() method that accepts an array-like and returns an array. This is helpful when you want access to more robust array methods, which you will learn about in a future project.

Wrap your inputContainers query selector in Array.from(). Do this on the same line as your declaration.

	• Step 90:
It is time for another loop. Use a for loop to iterate through the inputContainers array.

Inside the loop, set the innerHTML property of the element at the current index to an empty string. This will clear all of the contents of that input container.

	• Step 91:
After your loop completes, you need to clear the budgetNumberInput. Set the value property of budgetNumberInput to an empty string.

	• Step 92:
You also need to clear the output element's text. You can do this by setting the innerText property to an empty string.

The difference between innerText and innerHTML is that innerText will not render HTML elements, but will display the tags and content as raw text.

	• Step 93:
To finish off this function, you need to restore the hide class to the output element. The classList property has an .add() method which is the opposite of the .remove() method. It accepts a string representing the class to add to the element.

Add the hide class to your output.

	• Step 94:
To complete this project, add an event listener to the clearButton button. When the button is clicked, it should call the clearForm function.
![image](https://github.com/FrankySuazo/Calorie-Counter/assets/114836913/740d6aa2-efaf-4f74-bfe5-4fc00cbfdbfc)
