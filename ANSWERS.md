# ANSWERS

## 1. Why do we write `onPress={handlePress}` and not `onPress={handlePress()}`?

React executes `onPress={handlePress}` only when the event occurs. If you write `onPress={handlePress()}`, the function would execute immediately, at the exact moment the component is rendered on the screen.

## 2. What is the difference between `Button` and `Pressable`? When would you choose each one?

`Pressable` is a more flexible element in terms of customization and styling, as well as responding to the pressed state, while `Button` is a basic component with a fixed appearance for a quick, standard action.

## 3. What does the `style` function of `Pressable` receive and what does it return? Give an example.

It takes an object containing the component’s state, such as `{pressed}`, where `pressed` is `true` as long as the component is pressed. It returns a style, which can be an object or an array of styles. For example: `style={({ pressed }) => [styles.button, pressed && styles.pressed]}`.

## 4. Why can you not change a state variable directly (`isFollowing = true`) and what do you do instead?

If you assign the variable manually, React doesn’t receive any notification and doesn’t re-render the component; furthermore, the value is lost on the next render. It’s better to use the setter function returned by `useState`, which stores the new value and tells React to re-render.

## 5. Why is `followers` not a second `useState`? What is a *derived value*?

The number of followers can be calculated from “isFollowing”; storing it in a second state would duplicate the information and could cause desynchronization. A derived value is a value that is calculated from existing state or props during each render,

## 6. What does *controlled input* mean for `TextInput`? Which two props make it controlled?

It is an input whose text is stored in React’s state, so it is the state—and not the input field itself—that determines what is displayed. It becomes controlled through the `value` property, which displays the current state, and the `onChangeText` property, which updates the state every time the user types.

## 7. Why is `selectedSkills.push(skill)` wrong when `selectedSkills` is state? Write the correct code.

`push` modifies the array but keeps the same reference, and React may not re-render it. The state must be updated with a new array. The correct code is `setSelectedSkills([...selectedSkills, skill])` to add a skill, and `setSelectedSkills(selectedSkills.filter((item) => item !== skill))` to remove it.