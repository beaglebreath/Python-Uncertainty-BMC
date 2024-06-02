This script calculates and updates the measurement uncertainty for calibration measurements in a Sybase database.

Synopsis:
- The script connects to a Sybase database using the pyodbc library.
- It fetches the MTAG (instrument tag) for a given ID number from the inventory table.
- It then retrieves the corresponding CTAG (calibration tag) from the Calibration table.
- Using the CTAG, the script fetches all relevant rows from the CalResults table.
- For each row, the script calculates the deviation between the unit under test (UUT) measurement and the calibration standard measurement.
- The script calculates the combined standard uncertainty using the provided Best Measurement Capability (BMC) value and the resolution of the UUT.
- The combined standard uncertainty is rounded to two significant figures and formatted to include a leading zero if the value is between -1 and 1.
- The script updates the CalResults table with the calculated measurement uncertainty.

Usage:
1. Ensure you have the pyodbc library installed in your Python environment.
   You can install it using pip:
   pip install pyodbc

2. Update the database connection string in the script to match your Sybase DSN, UID, and PWD.

3. Run the script and provide the following inputs when prompted:
   - ID number: The ID number for which you want to update the measurement uncertainty.
   - Best Measurement Capability (BMC) value: The BMC value from your scope of accreditation.
   - Resolution of the device under test: The resolution of the unit under test.

Example:
$ python update_uncertainty.py
Enter the ID number: test
Enter the Best Measurement Capability (BMC) value: 0.05
Enter the resolution of the device under test: 1.0
