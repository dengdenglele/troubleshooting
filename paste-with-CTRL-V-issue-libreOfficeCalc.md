# Issue
- Platform: Linux with GNOME Desktop environment
- Copy something from a Cell in Libre Office Calc and paste it into Ctrl+F search field has a delay
- Sometimes Ctrl+V must be pressed repeatedly

# Solution
- Check in GNOME `Settings` -> `Accessibility` -> `Locate Pointer`
- Deactivate `Locate Pointer`
- When pasting something with Ctrl+V, `Locate Pointer` will be triggered first, thus leading to press Ctrl+V twice instead of once 
