# BreatheSafe

air quality apps say 154 AQI, dominant pollutant PM10 and just expect you to know what that means. this tells you what to actually do about it, and how many cigarettes you basically smoked by standing outside.

## what it does
- search a city or click the map, get live AQI, pollutants, pollen
- put in your health stuff (asthma, heart, pregnancy, age, how active you are) and the advice actually changes
-  a runner breathes ~2.6 m³ of air an hour, someone sitting at a desk ~0.42. same street, very different lungs
-  the exact hours in the next 48 when it's fine for you to go out
- trends, alerts, push notifications
- a route planner that scores a jog on real roads
- an AI chat that gets fed your real conditions before it answers

## screenshots

<img width="974" alt="dashboard" src="https://github.com/user-attachments/assets/30770f90-0d7d-4154-a02d-b37cb1f7dcd1" />

<img width="894" alt="health guidance" src="https://github.com/user-attachments/assets/44222143-c05a-421c-8429-e38fa55daf75" />
<img width="1064" alt="exposure" src="https://github.com/user-attachments/assets/b87c85d9-46b8-4f03-b324-3fd632359f6d" />
<img width="1256" alt="map" src="https://github.com/user-attachments/assets/62372949-d86c-4c30-949f-0dd9722bf582" />
<img width="914" alt="route planner" src="https://github.com/user-attachments/assets/50d7fbbb-084e-4181-8b67-63ce79203d3c" />
<img width="1216" alt="forecast" src="https://github.com/user-attachments/assets/63e3140a-3b62-4a70-8527-929a9e4fbbce" />
<img width="370" alt="ai chat" src="https://github.com/user-attachments/assets/6d8945e9-bb00-4fd2-b68d-660358e62d20" />

## how it works
next.js + mongodb, google's air quality API for the data, groq for the chat.

## stuff that broke
- half the time google gives you an index with no PM2.5 number
- pollen just doesn't cover india
- the maps key goes to every visitor's browser so it can't be the same key that spends your air quality quota
- averaging the forecast per day made the advice wrong most days since AQI swings 2 3 bands within one day

## run it
needs node 18+, mongodb, a google cloud project

turn on Air Quality, Pollen, Geocoding, Directions and Maps JavaScript in google cloud. make two keys a server one and a browser one locked to Maps JS. also a vector Map ID in Maps Studio.


## ai usage
ai was used to reduce the repetitive tasks and do the boring work, the main conceptual work and the directions were provided by me  keeping the risk engine a plain readable function instead of asking an LLM, the cigarette and dose math, deciding what this should even be. the testing part took a lot of time still, mostly checking it against real readings in real cities to find out where the advice was wrong. i made sure this isn't just AI slop but a actually usefull tool!


## disclaimer
not medical advice. the cigarette thing is a rule of thumb, not a real clinical measure, and the dose is an estimate. if you actually have asthma listen to your doctor not a dashboard.

