---
title: Appointments
page_title: Appointments
position: 4
slug: calendar-appointments
---

RadCalendar can display appointments in its month view by using its **AppointmentsSource** property. It accepts a collection of objects, which implement the **Telerik.XamarinForms.IAppointment** interface. This interface defines 3 members:
- **StartDate**, 
- **EndDate**, 
- **Title**

## Example ##
	calendar.AppointmentsSource = new List<Appointment>() {
		new Appointment() { 
			StartDate = DateTime.Today.AddDays(1), 
			EndDate = DateTime.Today.AddDays(2).AddTicks(-1), 
			Title = "Mom's Birthday"},
		new Appointment() { 
			StartDate = DateTime.Today.AddDays(3).AddHours(17), 
			EndDate = DateTime.Today.AddDays(3).AddHours(22), 
			Title = "Big Game"},
		new Appointment() {
			StartDate = DateTime.Today.AddDays(11).AddHours(20), 
			EndDate = DateTime.Today.AddDays(12).AddHours(4), 
			Title = "Progress Party"}
	};

![Appointments](calendar-appointments.png)