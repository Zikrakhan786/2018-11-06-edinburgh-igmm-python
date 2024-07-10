



  
   class FoodItem:
       def __init__(self, name, calories, protein, fat, carbs):
           self.name = name
           self.calories = calories
           self.protein = protein
           self.fat = fat
           self.carbs = carbs

       def __str__(self):
           return f"{self.name}: {self.calories} kcal, {self.protein}g protein, {self.fat}g fat, {self.carbs}g carbs"
   ```
ic    ### Step 2: Create a Tracker
   ```python
   class HealthyEatingTracker:
       def __init__(self):
           self.food_items = []

       def add_food_item(self, food_item):
           self.food_items.append(food_item)

       def calculate_totals(self):
           total_calories = sum(item.calories for item in self.food_items)
           total_protein = sum(item.protein for item in self.food_items)
           total_fat = sum(item.fat for item in self.food_items)
           total_carbs = sum(item.carbs for item in self.food_items)
           return total_calories, total_protein, total_fat, total_carbs

       def display_totals(self):
           total_calories, total_protein, total_fat, total_carbs = self.calculate_totals()
           print(f"Total for today: {total_calories} kcal, {total_protein}g protein, {total_fat}g fat, {total_carbs}g carbs")

       def provide_feedback(self):
           total_calories, total_protein, total_fat, total_carbs = self.calculate_totals()
           feedback = []
           if total_calories > 2000:
               feedback.append("You have consumed more than 2000 calories today. Try to reduce your intake.")
           if total_protein < 50:
               feedback.append("You should increase your protein intake.")
           if total_fat > 70:
               feedback.append("Your fat intake is too high.")
           if total_carbs > 300:
               feedback.append("You have consumed too many carbohydrates.")
           return feedback
   ```

   ### Step 3: Implement the Main Program
   ```python
   def main():
       tracker = HealthyEatingTracker()
       
       while True:
           print("\nHealthy Eating Tracker")
           print("1. Add Food Item")
           print("2. Display Totals")
           print("3. Get Feedback")
           print("4. Exit")
           choice = input("Enter your choice: ")

           if choice == '1':
               name = input("Enter food name: ")
               calories = float(input("Enter calories: "))
               protein = float(input("Enter protein (g): "))
               fat = float(input("Enter fat (g): "))
               carbs = float(input("Enter carbs (g): "))
               food_item = FoodItem(name, calories, protein, fat, carbs)
               tracker.add_food_item(food_item)
               print("Food item added!")
           elif choice == '2':
               tracker.display_totals()
           elif choice == '3':
               feedback = tracker.provide_feedback()
               if feedback:
                   for note in feedback:
                       print(note)
               else:
                   print("Great job! You're on track with your healthy eating goals.")
           elif choice == '4':
               break
           else:
               print("Invalid choice. Please try again.")

   if __name__ == "__main__":
       main()
   ```

