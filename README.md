# GridSaver: Smart Home Power Optimization
Final project for the Building AI course

## Summary
This project is an idea for a smart home application that uses machine learning to stop households from wasting money during peak electricity hours. It connects to your smart meter data, learns your daily routines, and predicts exactly when your local power grid is going to be slammed. Once it knows a peak is coming, it automatically tells high-drain appliances—like your water heater or EV charger—to take a brief break or slow down for a few minutes. This Building AI course project aims to cut down utility bills automatically without forcing people to change how they live day-to-day.

## Background
Right now, the way we handle electricity grids is pretty outdated. When everyone gets home from work, turns on the AC, and starts cooking at the exact same time, the grid hits a massive spike. To keep the lights on, power companies have to turn on backup fossil-fuel plants, which are terrible for the environment, and they jack up the prices during those hours to penalize you. 

I wanted to work on this because checking energy prices before you run your dishwasher is incredibly annoying. Nobody actually does it. The goal here is to automate that entire process. If we can make homes a little bit smarter about *when* they draw heavy power, we can save people a ton of money and keep the grid stable as more people switch to electric cars and electric heating.
* **Insane Bills:** Regular families get hit the hardest by dynamic or surging electricity rates.
* **Dirty Energy:** The backup power plants turned on during peak hours are usually the oldest and dirtiest ones available.
* **Grid Stress:** Overloaded local transformers break down faster, leading to blackouts and expensive repairs.

## How is it used?
The idea is for GridSaver to run completely in the background, either as a plug-in for existing smart home hubs (like Home Assistant or Google Home) or built right into the smart meter itself. 

**How it works in real life:**
1. **Learning Phase:** The app silently tracks how much power your house uses throughout the day and checks the local weather forecast.
2. **Smart Tweaking:** If the system sees that a massive price spike is coming at 6:00 PM, it might pre-heat your water tank at 5:15 PM and then throttle the heater down while you are cooking dinner. You won't even notice the temperature change.
3. **User Control:** If you ever need maximum power right away (like if you need to charge your car quickly before a trip), you just hit a giant override button on a simple dashboard to turn the AI off for the day.

## Data sources and AI methods
To make accurate predictions, the system needs a few simple data streams:
* **Your Smart Meter:** Historical usage data so the model knows your specific habits (e.g., you do laundry on Sundays, or your AC runs heavy on Tuesdays).
* **The Weather:** Local temperature forecasts, since weather is the number one thing that drives energy spikes.
* **Price Feeds:** An API connection to your local utility company to get real-time pricing data.

### The AI Part:
We will use supervised learning for this. I plan to use a Random Forest Regressor or a basic Neural Network. The model takes inputs like the current time, day of the week, and outside temperature, and uses them to forecast the home's power demand for the next few hours. A straightforward optimization script then looks at that forecast alongside the upcoming prices to schedule the best times to run the heavy appliances.

* Base dataset idea: [Open Power System Data](https://open-power-system-data.org/)
* Weather data source: Public local meteorological feeds

## Challenges
Technology has limits, so it's important to be realistic about what this can and cannot do:
* **Appliance Compatibility:** The software can't do anything if your appliances are old and don't have smart features or APIs to connect to.
* **Privacy Issues:** Smart meter data tells a story. If someone hacks your energy data, they can figure out exactly when you aren't home. Because of this, the AI needs to run locally inside the house, not on a random cloud server.
* **Unexpected Routines:** If you throw an impromptu party or use a heavy power tool out of nowhere, the AI will get confused and might make a bad prediction until it adapts to the new pattern.

## What next?
If I wanted to take this past a course concept, the next steps would look like this:
* **Neighborhood Sharing:** Creating a system where houses with solar panels can automatically share or sell their excess battery power to neighbors during peak hours.
* **Better Integrations:** Working directly with brands like Tesla, Nest, or Samsung so the app works out of the box without needing complicated setups.
* **Cheap Hardware:** Looking into how to package this onto a cheap, low-power microchip that anyone can clip onto their breaker box.

## Acknowledgments
* The core logic for handling the data and setting up regression loops comes from what I learned in the University of Helsinki's *Building AI* course.
* Big thanks to the open-source smart home community and the creators of public energy datasets for making this kind of data accessible to regular developers.


*LLM has been used for spell check only!
