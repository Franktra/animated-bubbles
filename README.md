# animated-bubbles
# detailed animation of a pack of rectangular gum walking, then blowing bubbles that pop to reveal key words
# The pack of gum moves across the screen, blows bubbles, and words appear in the bubbles as they pop. The axis is turned off for better visual representation.
Animated Action Framework Pack of Gum Popping Bubbles Revealing Key words

import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

# Create a figure and axis
fig, ax = plt.subplots()

# Function to update the plot for each frame
def update(frame):
    # Clear the current plot
    ax.cla()

    # Set the title and labels
    ax.set_title("Animated Bubbles")
    ax.axis('off')  # hide axis

    # Animation logic for each frame
    if frame < 30:
        # Animation for gum pack moving
        x = frame / 10  # Adjust the x-coordinate for each step
        y = 0  # Keep the y-coordinate constant
        ax.add_patch(plt.Rectangle((x-0.5, y-0.5), 1, 2, color='red'))  # Draw a rectangular gum pack
    elif frame < 60:
        # Animation for blowing the bubble
        radius = (frame - 30) / 40  # Increase the size of the bubble
        ax.add_patch(plt.Circle((3, 1.5), radius, color='blue'))  # Draw the bubble
        ax.add_patch(plt.Rectangle((2.5, -0.5), 1, 2, color='red'))  # Keep the gum pack in place
    elif frame < 90:
        # Animation for the first bubble pop
        # Draw the popped bubble with the word "Action"
        ax.text(3, 1.5, 'Action', fontsize=12, ha='center', va='center', color='blue')
        ax.add_patch(plt.Rectangle((2.5, -0.5), 1, 2, color='red'))  # Keep the gum pack in place
    elif frame < 120:
        # Animation for the second bubble pop
        # Draw the popped bubble with the word "Context"
        ax.text(3, 1.5, 'Context', fontsize=12, ha='center', va='center', color='blue')
        ax.add_patch(plt.Rectangle((2.5, -0.5), 1, 2, color='red'))  # Keep the gum pack in place
    else:
        # Animation for the third bubble pop
        # Draw the popped bubble with the word "Prioritize"
        ax.text(3, 1.5, 'Prioritize', fontsize=12, ha='center', va='center', color='blue')
        ax.add_patch(plt.Rectangle((2.5, -0.5), 1, 2, color='red'))  # Keep the gum pack in place

    # Set the limits of the plot
    ax.set_xlim(0, 5)
    ax.set_ylim(-1, 3)

# Create the animation using FuncAnimation
animation = FuncAnimation(fig, update, frames=150, interval=100)

# Display the animation
plt.show()

# Save the animation as a GIF file
try:
    animation.save('animation.gif', writer='pillow')
    print("Animation saved successfully.")
except Exception as e:
    print(f"Failed to save animation: {e}")
