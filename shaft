import math
import streamlit as st

# Set page configuration
st.set_page_config(
    page_title="Mechanical Shaft Design Calculator",
    page_icon="⚙️",
    layout="centered"
)

st.title("⚙️ Mechanical Shaft Design Calculator")
st.write("Perform standard mechanical calculations for shaft power, torque, stress, and sizing.")

# Sidebar Navigation
option = st.sidebar.radio(
    "Select Calculation Type:",
    (
        "Calculate Torque",
        "Calculate Power",
        "Calculate Shear Stress",
        "Calculate Required Shaft Diameter"
    )
)

st.divider()

# Option 1: Calculate Torque
if option == "Calculate Torque":
    st.header("1. Calculate Torque")
    
    col1, col2 = st.columns(2)
    with col1:
        power = st.number_input("Enter Power (kW):", min_value=0.0, value=10.0, step=0.5)
    with col2:
        speed = st.number_input("Enter Speed (rpm):", min_value=0.1, value=1500.0, step=10.0)

    if st.button("Calculate Torque", type="primary"):
        torque = (9550 * power) / speed
        st.success(f"**Torque:** {round(torque, 2)} N·m")

# Option 2: Calculate Power
elif option == "Calculate Power":
    st.header("2. Calculate Power")
    
    col1, col2 = st.columns(2)
    with col1:
        torque = st.number_input("Enter Torque (N·m):", min_value=0.0, value=63.66, step=1.0)
    with col2:
        speed = st.number_input("Enter Speed (rpm):", min_value=0.1, value=1500.0, step=10.0)

    if st.button("Calculate Power", type="primary"):
        power = (2 * math.pi * speed * torque) / (60 * 1000)
        st.success(f"**Power:** {round(power, 2)} kW")

# Option 3: Calculate Shear Stress
elif option == "Calculate Shear Stress":
    st.header("3. Calculate Shear Stress")
    
    col1, col2 = st.columns(2)
    with col1:
        torque = st.number_input("Enter Torque (N·m):", min_value=0.0, value=100.0, step=5.0)
    with col2:
        diameter = st.number_input("Enter Shaft Diameter (mm):", min_value=0.1, value=25.0, step=1.0)

    if st.button("Calculate Shear Stress", type="primary"):
        torque_nmm = torque * 1000  # Convert N·m to N·mm
        stress = (16 * torque_nmm) / (math.pi * (diameter ** 3))
        st.success(f"**Shear Stress:** {round(stress, 2)} MPa")

# Option 4: Calculate Required Shaft Diameter
elif option == "Calculate Required Shaft Diameter":
    st.header("4. Calculate Required Shaft Diameter")
    
    col1, col2 = st.columns(2)
    with col1:
        torque = st.number_input("Enter Torque (N·m):", min_value=0.0, value=100.0, step=5.0)
    with col2:
        allowable_stress = st.number_input("Enter Allowable Shear Stress (MPa):", min_value=0.1, value=50.0, step=1.0)

    if st.button("Calculate Diameter", type="primary"):
        torque_nmm = torque * 1000  # Convert N·m to N·mm
        diameter = ((16 * torque_nmm) / (math.pi * allowable_stress)) ** (1 / 3)
        st.success(f"**Required Shaft Diameter:** {round(diameter, 2)} mm")
