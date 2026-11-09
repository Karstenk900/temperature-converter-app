
# ============================================
# TEMPERATURE CONVERTER WEB APP
# Built using Python and Streamlit
# ============================================

# 1. Import Streamlit
import streamlit as st


# 2. Configure the webpage
st.set_page_config(
    page_title="Temperature Converter",
    page_icon="🌡️",
    layout="centered"
)


# 3. Create the webpage title and introduction
st.title("🌡️ Temperature Converter")

st.write(
    "Welcome to the Temperature Converter! "
    "Enter a temperature below and choose which "
    "conversion you would like to perform."
)

st.divider()


# 4. Create a temperature input box
temperature = st.number_input(
    "Enter Temperature:",
    value=0.0,
    step=1.0,
    format="%.2f"
)


# 5. Create a dropdown menu for conversion options
conversion_type = st.selectbox(
    "Select Conversion Type:",
    [
        "Celsius to Fahrenheit",
        "Fahrenheit to Celsius"
    ]
)


# 6. Create the Convert button
if st.button("Convert Temperature", use_container_width=True):

    # Convert Celsius to Fahrenheit
    if conversion_type == "Celsius to Fahrenheit":

        converted_temperature = (temperature * 9 / 5) + 32

        formula = "°F = (°C × 9/5) + 32"

        result_unit = "°F"

        original_unit = "°C"

    # Convert Fahrenheit to Celsius
    else:

        converted_temperature = (temperature - 32) * 5 / 9

        formula = "°C = (°F - 32) × 5/9"

        result_unit = "°C"

        original_unit = "°F"


    # 7. Display a success message
    st.success("Temperature converted successfully!")


    # 8. Display the conversion result
    st.subheader("Conversion Result")

    st.metric(
        label="Converted Temperature",
        value=f"{converted_temperature:.2f} {result_unit}"
    )


    # 9. Show the original temperature and conversion
    st.write(
        f"Original Temperature: {temperature:.2f} {original_unit}"
    )

    st.write(
        f"Converted Temperature: "
        f"{converted_temperature:.2f} {result_unit}"
    )


    # 10. Display the formula used
    st.subheader("Formula Used")

    st.code(formula, language="text")


# 11. Add a divider and information section
st.divider()

st.subheader("About This App")

st.write(
    "This application converts temperatures between "
    "Celsius and Fahrenheit using standard mathematical formulas."
)

st.caption("Temperature Converter | Created with Python and Streamlit")


