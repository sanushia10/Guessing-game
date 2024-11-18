# Guessing-game
import random
import streamlit as st

# Set up the app title
st.title("Number Guessing Game")

# Generate a random number if not already done
if "random_number" not in st.session_state:
    st.session_state.random_number = random.randint(1, 100)

# Input from user
guess = st.number_input("Guess a number between 1 and 100:", min_value=1, max_value=100, step=1)

# Button to submit the guess
if st.button("Submit Guess"):
    if guess < st.session_state.random_number:
        st.write("Too low! Try again.")
    elif guess > st.session_state.random_number:
        st.write("Too high! Try again.")
    else:
        st.write("Congratulations! You guessed the correct number!")
        # Reset the game
        st.session_state.random_number = random.randint(1, 100)
        st.write("A new number has been generated. Try again!")
