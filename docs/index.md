# Hospital Schedule Management System
###### v1.0-beta.1

_Developed by **Akash Bagchi, Akshaya Nadathur, Riya Mary Joseph, Sanchitha N G and Shraavta B K** for the Computational Thinking with Python Mini Project at Dayananda Sagar University, Kudlu Gate_

This is a schedule management system designed for modern hospitals to use as a next-day appointment booking and management application, assigning appointments to patients based on their preferences as well as allowing for cancellation and dynamic(automatic) rescheduling.
Our code employs the implementation of linked lists using classes and methods in python, as well as several python3 modules such as pandas and tkinter to create a fully functioning and intuitive scheduling system with rudimentary GUI.

## Functionality:

1. Appointment Creation
    - Different Schedules for different doctors (eg: X-Rays are handled by the radiologist whereas minor surgeries are handled by the General surgeon.)
    - Mechanisms in place to prevent overwriting of existing appointments by new ones
    - User is given the choice to opt-in for automatic rescheduling
    - Appointment confirmed acknowledgement messages to verify succesful booking
2. Appointment Viewing
    - Any user can review their appointment details simply by entering their contact information as a search parameter.
3. Appointment Cancellation
    - User can cancel their appointment by entering their details.
    - Automatic Rescheduling: Upon cancellation, the schedule is scanned for following appointments that have opted-in for automatic rescheduling. Should such an appointment be encountered that can be accomodated in the number of slots freed by the cancellation, it is automatically moved to the earlier time, and the old times are made available for bookings once more.
4. Admin View
    - Enabled mechanism for hospital staff to access password-protected view of all staff member's schedules, to ensure there is no confusion, and to facilitate manual cancellation by hospital staff in case of disparity or errors (negligible probability).

## Working - Backend

### The Schedule

Our schedule for this system considers a 12-hour working day in a hospital, comprised of 24 half-hour time slots. The Class _node_ is used to create the basic data structure for any one appointment slot, containing the patient's name, contact information, appointment details, timeslot (position in schedule) and link to the next node. The class **linked_list** is then used to envelop several of these _nodes_ in a list structure which when initialized, forms the schedule

### Appointment Creation

The "appointment_details_primaryinput" function takes in the user's Name, Contact information and desired appointment type. Based on type, the user is shown all the unoccupied timeslots of the appropriate doctor's schedule, accounting also for the size of their desired appointment type, to ensure that an appointment doesn't accidentally overwrite another appointment slot, or try to exceed the schedule's total size of 24 slots.
The user is also asked for their automatic rescheduling preferences, which will determine if their appointment is dynamically moved to earlier times that can accomodate them, should any open up.

The script then uses the "insert_new_appointment" and "appointmentconfirmed_acknowledge" methods to update the respective doctor's schedule with the new appointment.

### Appointment Cancellation

The "appointment_deletion_input" function takes all relevant information from the user and calls the "delete_appointment" method to scan through the appropriate schedule for the right slots, and empty the same. The method then makes all the timeslots previously occupied by said appointment available for booking again, to ensure that time is not wasted in the working day.
Further, the method calls the "reschedule_appointment" method when working is complete, to dynamically reschedule any following appointments wishing for earlier times, granted that it can be accomodated in the newly emptied slots.

### Admin View

The admin view function enables any logistical hospital staff with the (customizable by hospital) username and password to view the current state of all staff members' schedules.

## Working - Frontend

The front - end for our program is made possible using the TKinter module, using which we created a rudimentary GUI with buttons for all primary user functions. The front - end code (and thus the scheduling system as a whole) runs until the GUI is closed. This system is designed to always be open on a hospital computer, and refreshed at the start of every working day.
We are currently looking into deployment as a web-application.

###### [View on github](https://github.com/Python-mini-project/hospitalschedulingsystem)
