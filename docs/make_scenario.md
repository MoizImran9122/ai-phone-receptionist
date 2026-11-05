# Make scenario (booking)

1. **Custom webhook**: receives name, phone, address, issue and requested time from Vapi.
2. **Google Calendar: check availability** for the requested slot.
3. **Google Calendar: create event** for the inspection.
4. **Google Sheets: add row** with the booking details.
5. **Email: send confirmation** to the customer.
6. **Webhook response**: returns a short result for the agent to read to the caller.
