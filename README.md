import tkinter as tk
from tkinter import messagebox

# Function to calculate BMI
def calculate_bmi():
    try:
        name = entry_name.get()  # Get the name input
        weight = float(weight_entry.get())  # Get the weight input in kg
        height = float(height_entry.get()) / 100  # Get the height input and convert from cm to meters

        bmi = weight / (height ** 2)  # BMI formula

        # Display BMI result
        result_label.config(text=f"Your BMI: {bmi:.2f}")

        # Determine BMI category
        if bmi < 18.5:
            category = "Underweight"
        elif 18.5 <= bmi < 24.9:
            category = "Normal weight"
        elif 25 <= bmi < 29.9:
            category = "Overweight"
        else:
            category = "Obesity"

        category_label.config(text=f"Category: {category}")

    except ValueError:
        messagebox.showerror("Input Error", "Please enter valid numbers for weight and height")

# Create the main window
window = tk.Tk()
window.title("BMI Calculator")
window.configure(bg="lightblue")

# Add labels and entry fields for name, weight, and height
tk.Label(window, text="Enter Your Name:").grid(row=0, column=0, padx=10, pady=5)
entry_name = tk.Entry(window)
entry_name.grid(row=0, column=1, padx=10, pady=5)

tk.Label(window, text="Enter Your Age:").grid(row=1, column=0, padx=10, pady=5)
entry_age = tk.Entry(window)
entry_age.grid(row=1, column=1, padx=10, pady=5)

tk.Label(window, text="Gender:").grid(row=2, column=0, padx=10, pady=5)

tk.Label(window, text="Weight (kg):").grid(row=3, column=0, padx=10, pady=5)
weight_entry = tk.Entry(window)
weight_entry.grid(row=3, column=1, padx=10, pady=5)

tk.Label(window, text="Height (cm):").grid(row=4, column=0, padx=10, pady=5)
height_entry = tk.Entry(window)
height_entry.grid(row=4, column=1, padx=10, pady=5)

# Button to calculate BMI
calculate_button = tk.Button(window, text="Calculate BMI", command=calculate_bmi, activebackground="red", activeforeground="white")
calculate_button.grid(row=5, column=0, columnspan=2, pady=15)

# Labels to display results
result_label = tk.Label(window, text="Your BMI: ")
result_label.grid(row=6, column=0, columnspan=2, pady=5)

category_label = tk.Label(window, text="Category: ")
category_label.grid(row=7, column=0, columnspan=2, pady=4)

# Gender radio buttons
gender_var = tk.StringVar()
radio_male = tk.Radiobutton(window, text="Male", variable=gender_var, value="Male")
radio_female = tk.Radiobutton(window, text="Female", variable=gender_var, value="Female")
radio_male.grid(row=2, column=1, padx=10, pady=5, sticky="w")
radio_female.grid(row=2, column=2, padx=10, pady=5, sticky="w")

# Start the Tkinter main event loop
window.mainloop()
