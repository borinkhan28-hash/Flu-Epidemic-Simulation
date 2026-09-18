# Flu Epidemics in the City — Presentation Script

**Estimated speaking time:** 10–12 minutes, excluding questions  
**Presentation style:** clear, natural, and suitable for a university project presentation

---

## Slide 1 — Title

**Speaker script**

Good morning, Professor Alexis and everyone.

We are **The Boys**, and today we are presenting our project, **“Flu Epidemics in the City.”** Our group members are Chea Keang, Ros Bunna, Yon Kim Kosal, Soeun Thynasothea, and Khan Borin.

The objective of this project is to explore how influenza spreads through a city when people follow normal daily routines. We use an agent-based model built with the GAMA platform. In our simulation, individual people move between homes, workplaces, and schools, meet other people, and may transmit the virus through those contacts.

We also study how targeted interventions—especially testing, isolation, and vaccination—can reduce the spread of infection.

**Transition:** First, I will briefly introduce the structure of our presentation.

---

## Slide 2 — Contents

**Speaker script**

Our presentation is divided into four parts.

First, we explain the problem and why daily movement creates chains of infection.

Second, we present our intervention strategy, which uses testing and local isolation.

Third, we describe the current implementation of the model in GAMA, including the GIS environment, agent movement, infection process, and recovery.

Finally, we discuss the next extensions and the experiments that can be used to compare different vaccination scenarios.

**Transition:** Let us begin with the core problem: how contact between people allows the virus to spread.

---

## Slide 3 — The Core Problem: Contact Chains

**Speaker script**

The central problem is the creation of **contact chains**.

Influenza is transmitted through contact between infected and susceptible people. One infected person may infect several others, and each newly infected person can continue that chain.

In a city, these contacts are strongly connected to daily routines. People leave home, travel on the road network, spend time at work or school, and then return home. This behavior creates repeated opportunities for transmission in different locations.

Another difficulty is that an infected person may continue their normal routine without knowing that they are infected. During this period, they can expose family members, coworkers, students, and other people nearby.

The maps on this slide represent the spatial character of the problem. The risk is not distributed evenly. Areas with more buildings, roads, movement, and activity can create more opportunities for contact and therefore more opportunities for transmission.

This is why an agent-based model is useful: instead of treating the whole population as one uniform group, it allows us to represent where individuals go, whom they meet, and how infection emerges from those interactions.

**Transition:** To model those interactions, we first represent a typical day in the life of each person.

---

## Slide 4 — Daily Population Movement

**Speaker script**

This diagram shows the daily movement cycle used in our model.

People begin the day at home, where they may have contact with family members. In the morning, they leave home and travel through the road network.

Adults commute to workplaces, where they interact with coworkers and other people. Children travel to school, where they meet other students. These destinations create groups of people who may not normally meet at home, so they connect different households through shared locations.

In the evening, the agents return home. If a person became infected at work or school, they may then bring the infection back to their household. The same pattern repeats on following days, creating a connection between home, travel, work, and school.

In the GAMA animation, people do not move directly across buildings or empty space. They follow the GIS road network to reach their destination. This makes their movement more realistic and allows us to observe where agents gather during their commute.

The important point is that mobility is not only a visual feature. It determines which agents can meet, and therefore it directly affects the epidemic.

**Transition:** Once we understand this movement cycle, we can introduce an intervention that breaks some of these contact chains.

---

## Slide 5 — Local Isolation as an Intervention

**Speaker script**

Our main intervention is **local isolation based on daily testing**.

The process has four steps.

First, each day, one percent of the population is selected for testing.

Second, if an infected person receives a positive result, that person is identified as a detected case.

Third, the detected person enters isolation for twelve days. During isolation, the agent remains at home and does not travel to work or school.

Fourth, because the isolated agent no longer joins normal daily movement, the number of contacts decreases. This reduces the chance that the person will transmit the virus to coworkers, students, or people encountered during travel.

This intervention is targeted rather than citywide. Most people continue their normal routine, while detected infected people temporarily stop commuting. The model therefore lets us observe whether a relatively small daily testing program can reduce transmission by removing infectious agents from major contact locations.

Isolation does not immediately cure the disease. Its purpose is to reduce exposure while the infected person is recovering.

**Transition:** Now I will explain how these ideas are implemented in the GAMA simulation.

---

## Slide 6 — Current GAMA Implementation

**Speaker script**

Our current implementation combines geographic data, mobile agents, and epidemic rules.

First, the environment is created from GIS shapefiles containing buildings and roads. The buildings provide the agents’ homes, workplaces, and school, while the roads form the network used for movement.

Second, each person is represented as an individual agent. Agents belong to families, start from a home building, and receive a daily destination. Adults travel to workplaces, while children travel to school. In the simulation display, we can watch them leave in the morning, follow the roads, reach their destinations, and return home in the evening.

Third, the health process follows the SIR idea. A person begins as susceptible, may become infected after contact with an infectious person, and eventually becomes recovered. The baseline probability of infection is set to thirty-three percent for an eligible contact. This is a model parameter, so it can be changed when we run experiments.

For recovery, the model can represent recovery using a fixed infection duration or a probability-based rule, depending on the experiment design. Recovery must be evaluated for every infected agent, including agents who are isolated at home. Isolation changes movement and contact; it must not prevent the recovery process.

Finally, we extend the basic epidemic model with family groups, a school population, and baseline vaccination. These additions make it possible to compare transmission across households, workplaces, and school contacts, and to test how vaccination changes the epidemic curve.

The simulation also provides visual outputs, such as the map, health-state counts, and epidemic charts. These outputs help us compare the number of susceptible, infected, recovered, isolated, and vaccinated agents over time.

**Optional live-demonstration line**

On the map, the agents’ colors show their current health state. When the simulation runs, you can see them moving along the roads rather than crossing the map directly. At the same time, the charts update to show how the epidemic changes over time.

**Transition:** The current implementation gives us the foundation, but several extensions can make the analysis more realistic and more useful.

---

## Slide 7 — Future Model Extensions

**Speaker script**

Our roadmap focuses on three areas.

The first is **viral evolution**. Instead of assuming that every infection is caused by the same virus, we can introduce variants. A mutation may create a new variant with a different transmission probability. Variant-specific immunity also allows us to represent reinfection when a recovered person encounters a different strain.

The second area is **batch experimentation**. We plan to test vaccination coverage at ten percent, fifty percent, and ninety percent. Each scenario should be repeated with different random seeds because agent movement and infection are stochastic. Repetition allows us to compare average results instead of relying on only one simulation run.

The third area is **result analysis**. For each vaccination scenario, we can compare indicators such as the peak number of infected people, total infections, number of isolated cases, time of the infection peak, and remaining susceptible population.

The final graphs will show how increasing vaccination coverage changes the epidemic. This will help us draw a strategic conclusion about which intervention level produces the greatest reduction in transmission within the assumptions of our model.

**Transition:** This brings us to the end of our presentation.

---

## Slide 8 — Thank You

**Speaker script**

To conclude, our project demonstrates that flu transmission in a city is shaped by both health status and daily mobility.

By representing people as individual agents, we can observe how movement between homes, workplaces, and schools creates contact chains. We can then test how interventions such as daily testing, isolation, and vaccination interrupt those chains.

The GAMA platform is especially useful for this project because it combines agent behavior, GIS road movement, epidemic rules, animation, and experimental analysis in one model.

Thank you for listening. We are now ready for your questions and discussion.

---

# Short Q&A Preparation

## Why did you use an agent-based model?

An agent-based model lets us represent different people, destinations, schedules, and contacts. It helps us observe how a citywide epidemic emerges from individual behavior instead of assuming that everyone mixes uniformly.

## Why do agents move on roads?

Road-based movement represents realistic commuting paths. It also ensures that contact opportunities are related to the city’s spatial structure rather than agents moving directly through buildings.

## What does the 33% infection value mean?

It is the baseline probability that an eligible contact between an infectious agent and a susceptible agent causes infection. It is a configurable model assumption, not a universal clinical estimate.

## Why test only 1% of the population each day?

It represents a limited testing capacity. It allows us to study whether targeted detection and isolation can still reduce spread when universal daily testing is not possible.

## Why isolate people for 12 days?

The twelve-day period is an experimental policy parameter. During that period, detected agents stop commuting, which reduces their opportunities to transmit the virus outside the household.

## Why can an isolated person still recover?

Isolation and recovery are separate mechanisms. Isolation controls movement and contact, while recovery depends on infection duration or the recovery rule. Therefore, an infected agent must continue progressing toward recovery even while remaining at home.

## Why compare 10%, 50%, and 90% vaccination?

These three values represent low, medium, and high coverage. Comparing them helps us measure how the epidemic changes as population protection increases.

## What are the main limitations?

The model simplifies real human behavior and disease biology. Contact probabilities, daily schedules, test selection, recovery, and vaccine protection are assumptions. The results should therefore be interpreted as comparisons between simulated scenarios, not as exact forecasts for a real city.

---

# Presenter Notes

- Do not read the bullets word for word; use them as visual support while speaking.
- Point to the movement flow on Slide 4 while explaining home, work or school, and return travel.
- Pause briefly after each of the four intervention steps on Slide 5.
- If giving a live demo after Slide 6, show road-following movement first, then point to the health-state chart.
- Use the phrase **“within the assumptions of our model”** when discussing results.
- The title slide says **SIER**, while the description and implementation slide say **SIR**. Confirm the intended acronym before presenting and use it consistently throughout the deck.
