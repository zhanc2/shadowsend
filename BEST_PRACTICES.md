# Best Practices

## Using Github

Tracking what needs to be done, what is being done, and what has been done will happen with the Project Board.

When picking up a task, if it is not an issue yet, convert it to an issue. Create a branch for it with the following convention:
[issue number] (your name) [issue title]

For example, if Charles was working on issue #3 which was titled "Create player sprite", the branch name would be:
`3 (Charles) Create player sprite`

When making the pull request for it, follow the same naming convention. The merge should also be squashed.

Try to use the board and pull requests for any task that would involve changing the code base.

If there's a task that isn't code related, ex: brainstorming, DON'T convert it to an issue.

## Naming conventions

The following rules are somewhat arbitrary, but please follow them to keep the codebase organized.

- All files should be in snake_case, e.g. `footman_squad.tscn`, `pause_menu.gd`
- All variables in GDScript should be in snake_case, e.g. `var my_variable = 0`
- All class names in GDScript should be in PascalCase, e.g. `FootmanSquad`
- Functions should have a leading underscore if and only if they are private (i.e. only going to be used in its own script) OR if they are overridable by a subclass
	- E.g. `func _set_some_value(value)` has a leading underscore because it is a private setter
	- E.g. `func _ready()` has a leading underscore because it is intended to be overrided by subclasses
- See the [GDScript style guide](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_styleguide.html) for more details if you're interested for some reason

## Hierarchical node trees

The following rules are more vague and generalized, and also not always true.

- In general, child nodes should NOT know what their parents are
	- The reasoning behind this is that it makes it easier to add the child node to other parents.
	- This also keeps the code more linear, making it easier to understand
- Signals should almost always be sent upwards, i.e. emitted from a child and handled by a parent
- The above rules are sourced from [this page](https://docs.godotengine.org/en/stable/tutorials/best_practices/index.html)

## Other guidelines

- Commenting your code is good, but not required. You only need to comment on complicated code blocks that aren't easy to understand
	- E.g. in `selection_brush.gdshader`, the line `COLOR = clamp(COLOR, vec4(0), vec4(1)) * texture(brush_texture, SCREEN_UV + vec2(.01, .01) * TIME);` should be commented because it is difficult to understand what it does
	- In contrast, a line such as `var selected_squads: Array[Squad] = []` does not need to be commented because it reads like English
- Be wary about using Singletons. Sometimes it's convenient in the short term, but brings problems later

## Tips

- If you are writing a comment for a member variable or a function, you can start your comment with a double hashtag `##` to indicate that it is a [documentation comment](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_documentation_comments.html)
- You can press F1 on your keyboard to access documentation on any class, function, or variable in Godot, including ones you made in the project!
- Feel free to add things to this file
- Thank you to Jay Ren for the coding practices lol
