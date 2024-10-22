___
[[custom_tkinter]]
#project 
___
#chatgpt 
```python
import os

from tkinter import filedialog, messagebox

  

import customtkinter as ctk

import pandas as pd

# Create the main application class

class CSVEditorApp(ctk.CTk):

    def __init__(self):

        super().__init__()

        self.title("CSV File Cleaner")

        self.geometry("400x300")

  

        self.df = None  # DataFrame to store the CSV file

  

        # Create buttons and labels

        self.upload_button = ctk.CTkButton(self, text="Upload CSV", command=self.upload_csv)

        self.upload_button.pack(pady=10)

  

        self.drop_duplicates_button = ctk.CTkButton(self, text="Drop Duplicates", command=self.drop_duplicates, state="disabled")

        self.drop_duplicates_button.pack(pady=10)

  

        self.drop_na_button = ctk.CTkButton(self, text="Drop Missing Values", command=self.drop_na, state="disabled")

        self.drop_na_button.pack(pady=10)

  

        self.save_button = ctk.CTkButton(self, text="Save CSV", command=self.save_csv, state="disabled")

        self.save_button.pack(pady=10)

  

        self.label = ctk.CTkLabel(self, text="No file loaded")

        self.label.pack(pady=10)

  

    # Function to upload a CSV file

    def upload_csv(self):

        file_path = filedialog.askopenfilename(filetypes=[("CSV Files", "*.csv")])

        if file_path:

            try:

                self.df = pd.read_csv(file_path)

                self.label.configure(text=f"File Loaded: {os.path.basename(file_path)}")

                # Enable buttons once file is loaded

                self.drop_duplicates_button.configure(state="normal")

                self.drop_na_button.configure(state="normal")

                self.save_button.configure(state="normal")

            except Exception as e:

                messagebox.showerror("Error", f"Could not load CSV file.\nError: {e}")

  

    # Function to drop duplicate rows

    def drop_duplicates(self):

        if self.df is not None:

            self.df.drop_duplicates(inplace=True)

            messagebox.showinfo("Success", "Duplicates dropped successfully.")

  

    # Function to drop missing values

    def drop_na(self):

        if self.df is not None:

            self.df.dropna(inplace=True)

            messagebox.showinfo("Success", "Missing values dropped successfully.")

  

    # Function to save the cleaned CSV

    def save_csv(self):

        if self.df is not None:

            file_path = filedialog.asksaveasfilename(defaultextension=".csv", filetypes=[("CSV Files", "*.csv")])

            if file_path:

                try:

                    self.df.to_csv(file_path, index=False)

                    messagebox.showinfo("Success", f"File saved successfully at {file_path}")

                except Exception as e:

                    messagebox.showerror("Error", f"Could not save CSV file.\nError: {e}")

  

# Run the app

if __name__ == "__main__":

    ctk.set_appearance_mode("System")  # Set the appearance mode of the app

    ctk.set_default_color_theme("blue")  # Set the color theme

    app = CSVEditorApp()

    app.mainloop()
```