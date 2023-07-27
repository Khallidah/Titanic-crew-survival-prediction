# Titanic-crew-survival-prediction
import streamlit as st
import pandas as pd
import numpy as np
import pickle


pickle_in = open('model.pkl', 'rb')
model = pickle.load(pickle_in)
pickle_in.close()

st.title("Titanic crew survival prediction")
st.write("Developed by: Khallidah Idris")
### inputing variables

name = st.text_input("Name of the individual") 
Pclass = st.number_input("Passenger Class")
Sex = st.number_input("Sex") 
Age = st.number_input("Age") 
SibSp = st.number_input("Number of Siblings and Spouses") 
Parch = st.number_input("Number of Parents and Children") 
Fare = st.number_input("Fare") 
Cabin = st.number_input("Cabin Number")
Embarked_Q = st.number_input("Embarked from Queens") 
Embarked_S = st.number_input("Embarked from Southampton")

button = st.button("Predict")

### making predictions
if button:
    predictions = model.predict([[Pclass,Sex,Age,SibSp,Parch,Fare,Cabin,Embarked_Q,Embarked_S]])
if predictions == 0:
    st.write("Unfortunately",name,"did not survive.")
else:
    st.write(name,"survived.")
    
