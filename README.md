# Ai_Event-Manager
The AI Event Manager is a Python-based intelligent system designed to simplify and automate event planning and management tasks. It leverages Artificial Intelligence to organize, schedule, and coordinate various aspects of an event — such as venue booking, vendor selection, budget tracking, and guest management etc

# ====================================
# AI EVENT MANAGER 
# Created by: Raj Kumar Chaudhuri and co.
======================================
import datetime

def generate_schedule(event_type):
    schedules = {
        "wedding": [
            "08:00 AM - Venue Setup",
            "10:00 AM - Guest Arrival",
            "11:00 AM - Wedding Ceremony",
            "01:00 PM - Lunch",
            "03:00 PM - Reception",
            "06:00 PM - Wrap Up"
        ],
        "conference": [
            "09:00 AM - Setup & Registration",
            "10:00 AM - Inaugural Speech",
            "11:30 AM - Keynote Session",
            "01:00 PM - Lunch",
            "02:30 PM - Panel Discussion",
            "05:00 PM - Closing Ceremony"
        ],
        "birthday": [
            "10:00 AM - Decoration & Setup",
            "12:00 PM - Guests Arrival",
            "01:00 PM - Cake Cutting",
            "02:00 PM - Lunch",
            "03:00 PM - Games & Fun",
            "05:00 PM - Gift Distribution"
        ]
    }
    return schedules.get(event_type.lower(), ["No schedule available for this event type."])

def ai_suggestions(event_type, budget, guests):
    if event_type.lower() == "wedding":
        venue = "Grand Palace Banquet Hall"
        catering = "Premium Catering (₹500 per guest)"
        decor = "Luxury Floral Theme"
    elif event_type.lower() == "conference":
        venue = "City Convention Center"
        catering = "Standard Buffet (₹250 per guest)"
        decor = "Minimalist Corporate Setup"
    elif event_type.lower() == "birthday":
        venue = "Fun Fiesta Party Hall"
        catering = "Kids & Family Menu (₹200 per guest)"
        decor = "Colorful Balloon Theme"
    else:
        venue = "Community Hall"
        catering = "Basic Buffet (₹150 per guest)"
        decor = "Simple Decoration"

    # Rough cost estimation
    catering_cost = int(catering.split("₹")[1].split(" ")[0]) * guests
    decor_cost = 5000
    venue_cost = 10000
    total = catering_cost + decor_cost + venue_cost

    return venue, catering, decor, total

# main
def main():
    print("=" * 50)
    print("🤖 WELCOME TO AI EVENT MANAGER 🤖")
    print("=" * 50)

    # Input details
    name = input("Enter event name: ")
    event_type = input("Enter event type (wedding/conference/birthday): ").lower()
    date_str = input("Enter date (YYYY-MM-DD): ")
    guests = int(input("Enter number of guests: "))
    budget = int(input("Enter your budget (in ₹): "))

    # Validate date
    try:
        event_date = datetime.datetime.strptime(date_str, "%Y-%m-%d").date()
    except ValueError:
        print("Invalid date format! Please use YYYY-MM-DD.")
        return

    # Generate AI suggestions
    venue, catering, decor, total_cost = ai_suggestions(event_type, budget, guests)

    # Show results
    print("\n--- AI Event Plan ---")
    print(f"Event Name: {name}")
    print(f"Event Type: {event_type.capitalize()}")
    print(f"Date: {event_date.strftime('%d %B %Y')}")
    print(f"Guests: {guests}")
    print(f"Budget: ₹{budget}")
    print("\nAI Suggestions:")
    print(f"Venue: {venue}")
    print(f"Catering: {catering}")
    print(f"Decoration: {decor}")
    print(f"\nEstimated Total Cost: ₹{total_cost}")

    if total_cost <= budget:
        print("✅ Within Budget! Great Planning.")
    else:
        print("⚠️ Over Budget! Try reducing guest count or choosing cheaper options.")

    # Show schedule
    print("\n--- Event Schedule ---")
    schedule = generate_schedule(event_type)
    for item in schedule:
        print(item)

    # Display final summary instead of saving to file
    print("\n" + "=" * 50)
    print("📋 EVENT PLAN SUMMARY 📋")
    print("=" * 50)
    print(f"Event Name: {name}")
    print(f"Event Type: {event_type.capitalize()}")
    print(f"Date: {event_date}")
    print(f"Guests: {guests}")
    print(f"Budget: ₹{budget}")
    print(f"Venue: {venue}")
    print(f"Catering: {catering}")
    print(f"Decoration: {decor}")
    print(f"Estimated Total Cost: ₹{total_cost}")
    print("=" * 50)
    print("Thank you for using AI Event Manager Hope You like our Services !")

# Run the program
if __name__ == "__main__":
    main()


