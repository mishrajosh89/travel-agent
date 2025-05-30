START

DISPLAY "1. I know where I want to go"
DISPLAY "2. I don't know where I want to go" 
GET user_choice

IF user_choice == 1 THEN
  GOTO function_one

ELSE IF user_choice == 2 THEN
  // Tool 2: Recommend destination
  DISPLAY "When do you want to travel? (eg.- July 4th - 8th)"
  GET travel_dates

  DISPLAY "What weather do you prefer? (eg.- warm, rainy, snowy)"
  GET weather_pref

  DISPLAY "What is your budget? (eg.- luxury, moderate, budget-friendly)"
  GET budget

  DISPLAY "What are your interests in a destination? (eg.- culture, food, nature)"
  GET interests

  CALL find_matching_destination(weather_pref, budget, interests, travel_dates)
  CALL display_destination_recommendations()

  SET selected_destination = top_match
  DISPLAY "Would you like to plan your trip to [selected_destination]?"
  DISPLAY "1. Yes 2. No"
  GET response

  IF response==1 THEN
    GOTO function_one_using(selected_destination)
  ELSE
    DISPLAY "Thank you for using Travel Planner"
    END
  END IF
ELSE
  DISPLAY "Inavlid choice. Please select 1 or 2."
  END
END IF

END

LABEL FUNCTION_ONE
Display "Enter your departure location"
GET departure

DISPLAY "Enter your destination"
GET destination

DISPLAY "Enter your travel dates"
GET travel_dates

DISPLAY "Select your travel budget level:"
DISPLAY "1. Luxury 2. Moderate 3. Budget-Friendly"
GET budget_level

CALL get_travel_options(departure, destination, travel_dates)
CALL filter_transport_by_budget(budget_level)
CALL display_top_transport_options()

CALL get_top_hotels(destination, budget level)
CALL get_top_attractions(destination)

DISPLAY recommendations
END

-------------------------------------------------------------

LABEL FUNCTION_ONE_USING(selected_destination)
DISPLAY "Enter your departure location:"
GET departure

SET destination = selected_destination

DISPLAY "Enter travel dates:"
GET travel_dates

DISPLAY "Select your travel budget level:"
DISPLAY "1. Budget  2. Moderate  3. Luxury"
GET budget_level

CALL get_travel_options(departure, destination, travel_dates)
CALL filter_transport_by_budget(budget_level)
CALL display_top_transport_options()

CALL get_top_hotels(destination, budget_level)
CALL get_top_attractions(destination)

DISPLAY recommendations
END




  
  
