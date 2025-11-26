# system
system

# 🏋️ DAILY EXERCISE RECOMMENDATION SYSTEM 3.0 🏋️
# Full-week workouts added

user = {
    "admin": "admin123",
    "cloyd": "cloyd123",
    "alex": "alex123"
}

print("=== Login ===")

username = input("Enter Username: ")
password = input("Enter Password: ")

if username in username:
    if user[username] == password:
        print("Login Successful! Welcome,", username)
    else:
        print("Incorrect password or Incorrect username!")
else:
    print("Username not found!")

import datetime

today = datetime.datetime.now()
print(today.strftime("📅 Today is: %B %d, %Y  ⏰ Time: %I:%M %p"))

def show_banner():
    print("\n" + "=" * 45)
    print("🏋️  DAILY EXERCISE RECOMMENDATION SYSTEM  🏋️")
    print("=" * 45)

def calculate_bmi():
    print("\nLet's calculate your BMI first.")
    while True:
        gender = input("Enter your gender (M/F/O): ").strip().lower()
        if gender in ("m", "male"):
            gender_label = "Male"
            break
        elif gender in ("f", "female"):
            gender_label = "Female"
            break
        elif gender in ("other", "o"):
            gender_label = "Other"
            break
        else:
            print("⚠️ Please enter M, F, or O.")

    while True:
        try:
            height = float(input("Enter your height in centimeters (e.g., 100): ").strip())
            if height <= 0:
                raise ValueError
            break
        except ValueError:
            print("⚠️ Invalid height. Please enter a positive number (centimeters).")

    while True:
        try:
            weight = float(input("Enter your weight in kilograms (e.g., 65): ").strip())
            if weight <= 0:
                raise ValueError
            break
        except ValueError:
            print("⚠️ Invalid weight. Please enter a positive number (kilograms).")

    height_m = height / 100

    bmi = weight / (height_m ** 2)
    print(f"\n📊 Your BMI is: {bmi:.2f}")

    if bmi < 18.5:
        category = "Underweight"
        base_advice = "Focus on balanced meals and light strength exercises to gain healthy weight."
    elif 18.5 <= bmi < 25:
        category = "Normal"
        base_advice = "Keep it up! Continue maintaining a balanced routine of cardio and strength."
    elif 25 <= bmi < 30:
        category = "Overweight"
        base_advice = "Add more cardio, control calorie intake, and include strength training."
    else:
        category = "Obese"
        base_advice = "Start with low-impact exercises (walking, swimming) and consult a professional if needed."

    if gender_label == "Male":
        advice = base_advice + " Men often respond well to resistance training for muscle and metabolism."
    elif gender_label == "Female":
        advice = base_advice + " Women benefit from strength training too — it supports bone health and metabolism."
    else:
        advice = base_advice + " Choose exercises you enjoy and consider professional guidance for a personalized plan."

    print(f"🏷️ BMI Category: {category}")
    print(f"🔎 Gender: {gender_label}")
    print(f"💡 Advice: {advice}")
    return category, gender_label

def get_fitness_goals():
    goals_list = {
        "1": "weight loss",
        "2": "muscle gain",
        "3": "maintain weight",
        "4": "add weight"
    }

    print("\n=== FITNESS GOALS ===")
    print("1. Weight Loss")
    print("2. Muscle Gain")
    print("3. Maintain Weight")
    print("4. Add Weight")
    print("0. Exit")

    while True:
        choice = input("Enter your fitness goals (e.g. 1,2 or 2,3): ").replace(" ", "")
        if choice == "0":
            return None

        selected_goals = []
        for num in choice.split(","):
            if num in goals_list:
                selected_goals.append(goals_list[num])

        if selected_goals:
            return selected_goals
        else:
            print("⚠️ Invalid choice. Please enter valid goal numbers separated by commas.")

def get_difficulty_level():
    print("\n=== SELECT DIFFICULTY LEVEL ===")
    print("1. Beginner")
    print("2. Intermediate")
    print("3. Advanced")

    while True:
        level = input("Enter your level (1-3): ")
        if level == "1":
            return "beginner"
        elif level == "2":
            return "intermediate"
        elif level == "3":
            return "advanced"
        else:
            print("⚠️ Invalid choice. Please enter 1, 2, or 3.")

def get_weekly_routine(goal, level):
    """Returns a dictionary with workouts for each day of the week."""
    routine = {}

    if goal == "weight loss":
        if level == "beginner":
            routine = {
                "Monday": "🏃 Jogging 20 mins + 🧘 Stretching 10 mins",
                "Tuesday": "🚶 Brisk walk 15 mins + 🏋️ Bodyweight squats 3x10",
                "Wednesday": "🧘 Yoga 20 mins + 🚴 Cycling 15 mins",
                "Thursday": "🏃 Jogging 20 mins + 🏋️ Push-ups 3x10",
                "Friday": "🚶 Walk 15 mins + 🧘 Stretching 10 mins",
                "Saturday": "🏃 HIIT 15 mins (light) + Core 3x10",
                "Sunday": "💤 Rest / light walk 10 mins"
            }
        elif level == "intermediate":
            routine = {
                "Monday": "🏃 Jogging 30 mins + 🚴 Cycling 20 mins",
                "Tuesday": "🏋️ Circuit training 25 mins",
                "Wednesday": "🏃 Jogging 25 mins + Core 15 mins",
                "Thursday": "🚴 Cycling 30 mins + Stretching 10 mins",
                "Friday": "🏋️ HIIT 20 mins + Cardio 15 mins",
                "Saturday": "🏃 Running 20 mins + Core 20 mins",
                "Sunday": "💤 Rest / light walk 15 mins"
            }
        else:
            routine = {
                "Monday": "🏃 HIIT 25 mins + Jump rope 15 mins",
                "Tuesday": "🏋️ Circuit training 40 mins",
                "Wednesday": "🏃 Sprint intervals 20 mins + Core 20 mins",
                "Thursday": "🚴 Cycling 45 mins",
                "Friday": "🏋️ Strength & HIIT combo 40 mins",
                "Saturday": "🏃 Running 30 mins + Core 25 mins",
                "Sunday": "💤 Active recovery: Yoga or walking 20 mins"
            }

    elif goal == "muscle gain":
        if level == "beginner":
            routine = {
                "Monday": "🏋️ Push-ups 3x10 + Squats 3x10 + Plank 30s",
                "Tuesday": "🏋️ Dumbbell curls 3x10 + Lunges 3x10",
                "Wednesday": "🏋️ Bench dips 3x12 + Stretching 10 mins",
                "Thursday": "🏋️ Push-ups 3x12 + Squats 3x12",
                "Friday": "🏋️ Dumbbell press 3x10 + Lunges 3x12",
                "Saturday": "🏋️ Full body circuit 20 mins",
                "Sunday": "💤 Rest / light walk 10 mins"
            }
        elif level == "intermediate":
            routine = {
                "Monday": "🏋️ Bench press 4x10 + Squats 4x12",
                "Tuesday": "🏋️ Deadlifts 4x8 + Pull-ups 3x8",
                "Wednesday": "🏋️ Dumbbell press 4x10 + Bicep curls 3x12",
                "Thursday": "🏋️ Circuit training 30 mins",
                "Friday": "🏋️ Bench press 5x10 + Squats 5x10",
                "Saturday": "🏋️ HIIT + Strength combo 30 mins",
                "Sunday": "💤 Active recovery: Yoga or light walk"
            }
        else:
            routine = {
                "Monday": "🏋️ Bench press 5x10 + Deadlifts 5x8 + Pull-ups 4x10",
                "Tuesday": "🏋️ Squats 5x8 + Dumbbell press 4x10 + Bicep curls 3x10",
                "Wednesday": "🏋️ Circuit training 40 mins",
                "Thursday": "🏋️ HIIT + Strength 45 mins",
                "Friday": "🏋️ Deadlift 5x8 + Bench press 5x10",
                "Saturday": "🏋️ Full body heavy lifting 50 mins",
                "Sunday": "💤 Active recovery / light cardio"
            }

    elif goal == "maintain weight":
        if level == "beginner":
            routine = {
                "Monday": "🚶 Brisk walk 20 mins + Yoga 10 mins",
                "Tuesday": "🏋️ Light strength 2x10 + Stretch 10 mins",
                "Wednesday": "🚶 Cycling 15 mins + Yoga 15 mins",
                "Thursday": "🏋️ Light circuit 20 mins",
                "Friday": "🏃 Jog 20 mins + Stretch 10 mins",
                "Saturday": "🏋️ Bodyweight full body 15–20 mins",
                "Sunday": "💤 Rest / light activity"
            }
        elif level == "intermediate":
            routine = {
                "Monday": "🏃 Jog 25 mins + Light circuit 25 mins",
                "Tuesday": "🏋️ Full body training 30 mins",
                "Wednesday": "🚴 Cycling 20 mins + Core 15 mins",
                "Thursday": "🏋️ Circuit training 30 mins",
                "Friday": "🏃 Jog 30 mins + Stretching 15 mins",
                "Saturday": "🏋️ Full body workout 30 mins",
                "Sunday": "💤 Active recovery: Yoga or walking"
            }
        else:
            routine = {
                "Monday": "🏋️ Circuit training 40 mins + Cardio 20 mins",
                "Tuesday": "🏃 HIIT 30 mins + Strength 30 mins",
                "Wednesday": "🏋️ Full body 45 mins",
                "Thursday": "🚴 Cycling 40 mins + Core 20 mins",
                "Friday": "🏋️ Strength & HIIT combo 50 mins",
                "Saturday": "🏃 Running 30 mins + Stretching 20 mins",
                "Sunday": "💤 Active recovery / Yoga"
            }

    elif goal == "add weight":
        if level == "beginner":
            routine = {
                "Monday": "🏋️ Bodyweight squats 3x10 + Push-ups 3x8",
                "Tuesday": "🏋️ Dumbbell press 3x10 + Lunges 3x10",
                "Wednesday": "🏋️ Bicep curls 3x10 + Squats 3x12",
                "Thursday": "🏋️ Push-ups 4x10 + Plank 45s",
                "Friday": "🏋️ Full body dumbbell circuit 20 mins",
                "Saturday": "🏋️ Barbell squats 3x8 + Bench press 3x10",
                "Sunday": "💤 Rest / light activity"
            }
        elif level == "intermediate":
            routine = {
                "Monday": "🏋️ Squats 4x8 + Bench press 4x10 + Deadlift 4x8",
                "Tuesday": "🏋️ Dumbbell press 4x10 + Lunges 4x12 + Core 15 mins",
                "Wednesday": "🏋️ Pull-ups 4x8 + Bicep curls 4x10",
                "Thursday": "🏋️ Full body circuit 30 mins",
                "Friday": "🏋️ Squats 5x8 + Bench press 5x10",
                "Saturday": "🏋️ Deadlift 5x8 + Dumbbell press 4x10",
                "Sunday": "💤 Active recovery / light cardio"
            }
        else:
            routine = {
                "Monday": "🏋️ Heavy squats 5x8 + Bench press 5x10 + Deadlift 4x8",
                "Tuesday": "🏋️ Full body dumbbell & barbell circuit 50 mins",
                "Wednesday": "🏋️ Pull-ups 4x12 + Core 20 mins",
                "Thursday": "🏋️ HIIT + Strength combo 45 mins",
                "Friday": "🏋️ Deadlift 5x8 + Bench press 5x10",
                "Saturday": "🏋️ Full body heavy lifting 50 mins",
                "Sunday": "💤 Active recovery / Yoga"
            }

    return routine

def show_exercise_routine(goals, level, bmi_category):
    print("\n==============================")
    print("🏁 YOUR FULL WEEK EXERCISE PLAN")
    print("==============================")

    print(f"🎯 Selected goals: {', '.join(goals).upper()}")
    print(f"💪 Level: {level.capitalize()}")
    print(f"📊 BMI Category: {bmi_category}\n")

    for goal in goals:
        print(f"--- {goal.upper()} ROUTINE ---")
        routine = get_weekly_routine(goal, level)
        for day, exercises in routine.items():
            print(f"{day}: {exercises}")
        print("💡 Tip: Stay consistent and eat a balanced diet!\n")

    print("✅ Keep training, stay consistent, and track your progress!\n")

def main():
    show_banner()
    name = input("\nEnter your name: ").strip().capitalize()
    print(f"\n👋 Welcome, {name}! Let's plan your personalized workout today.")

    bmi_category, gender_label = calculate_bmi()

    while True:
        goals = get_fitness_goals()
        if goals is None:
            print("\n👋 Goodbye! Stay active and healthy!")
            break

        level = get_difficulty_level()
        show_exercise_routine(goals, level, bmi_category)

        cont = input("\nDo you want to create another plan? (y/n): ").strip().lower()
        if cont != "y":
            print("\n👋 Goodbye! Stay strong and keep training!")
            break
main()
