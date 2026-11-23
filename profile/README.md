# Elyos Racing Team

**Student team from Tecnológico de Monterrey, Guadalajara campus.** Since 2021 we design and build ultra-efficient battery-electric prototypes for the [Shell Eco-marathon](https://www.makethefuture.shell/en-gb/shell-eco-marathon), and since 2026 an autonomy kit for Shell's Autonomous Driving Challenge. We design the car ourselves: chassis and body, circuit boards, motor-control firmware, telemetry and the energy strategy.

| **336 km/kWh** | **30 kg** | **4th** | **12× faster** |
|:---:|:---:|:---:|:---:|
| Best result, Shell Eco-marathon United States 2026 | Lightest car of the 2024 Americas competition | In the Americas, in 2024 and again in 2025 | Motor-control loop after our rework: 68 µs down to 5.4 µs (bench, Nov 2026) |

**Website and portfolio:** <https://elyos-racing.github.io/team-portfolio/> · [elyosracingteam.com](https://www.elyosracingteam.com/)

## Results

| Season | Event | Result | km/kWh |
|---|---|---|---|
| 2026 | Shell Eco-marathon United States, Indianapolis | **6th place**, Prototype Battery Electric | **336** |
| 2025 | Shell Eco-marathon Americas | **4th place** | 293 |
| 2024 | Shell Eco-marathon Americas, Indianapolis | **4th place in the Americas** · lightest car of the competition (30 kg) | 302 |
| 2023 | Shell Eco-marathon Brazil, Rio de Janeiro | **6th place** · most efficient Mexican car in Shell Eco-marathon history | 235 |
| 2023 | Shell Eco-marathon Americas, Indianapolis | Debut · 2nd lightest car in the Americas (31 kg) | — |

On the same track, Indianapolis, we went from 302 km/kWh in 2024 to **336 in 2026 (+11 %)**. Results only compare fairly on the same circuit. Sources and season pages: [`team-portfolio`](https://github.com/ELYOS-Racing/team-portfolio).

## Season 2027

| When | What |
|---|---|
| **6–10 April 2027** | Shell Eco-marathon United States, Indianapolis Motor Speedway: 4 laps, 15.33 km, 35 minutes |
| April 2027 | First public demo of the autonomy kit |
| **June 2027** | Autonomous Driving Challenge, Silesia Ring, Poland. Our aim is to become the first team from the Americas to complete ADC attempts |

**Where the next kilometres come from.** Our 2026 attempts were consistent, five valid runs within about 8 % of each other, so the gap to the winner is in the car, not the driving. Our energy model ranks where it is. For 2027 we are replacing the hub motor with a chain drive and clutch (about 20 % less energy in the model), measuring rolling resistance and drag with coast-down tests, and putting every milliwatt of electronics on a budget.

## What we build

| Area | What it is | Highlights |
|---|---|---|
| **Mechanics** | A three-wheeled monocoque prototype with partial-Ackermann steering and hydraulic brakes | 30 kg in 2024; a chain drive with a clutch for 2027 |
| **Electronics** | Our own 48 V, 45 A motor-driver board and telemetry board | Moved from Altium to KiCad and verified against the original gerbers; electrical and design-rule checks on every change |
| **Motor driver** | Field-oriented control (FOC) of a BLDC motor on an ARM Cortex-M7 at 600 MHz | 10 kHz current loop in a hardware interrupt; current sampling synchronized with the PWM; sensorless observer in development |
| **Telemetry** | Sensors, sensor fusion, logging and a live link to the pits; cockpit display for the driver | A predictive co-pilot trained in simulation that tells the driver when to accelerate and when to coast |
| **Energy strategy** | A metre-by-metre model of the car and the track | Optimal control and genetic algorithms for the speed profile; a loss budget that ranks where every watt goes; motor, gear and clutch choices backed by thousands of simulated attempts |
| **Inter-board protocol** | One versioned binary protocol shared by every board | Frozen golden test vectors, CRC on every frame, C and Python implementations checked byte by byte |
| **Pit dashboard** | Live telemetry, laps and race control for the pit crew | Real-time push to every screen; session export for analysis |
| **Autonomy** | A removable autonomy kit on the 2026 car | ROS 2 stack (localization, perception, planning, control, safety); software-in-the-loop tests and a digital twin in Gazebo and NVIDIA Isaac Sim |

## Technology

| Domain | Tools |
|---|---|
| Embedded | C and C++, Teensy 4.1 (NXP i.MX RT1062), ESP32, FreeRTOS, SimpleFOC, ESP-IDF, PlatformIO |
| Electronics | KiCad 10, automated ERC and DRC, INA240 current sensing, CAN |
| Mechanical | SolidWorks, STEP / DXF releases, a numbered bill of materials checked automatically |
| Simulation and optimization | Python, NumPy, pandas, CasADi with IPOPT, pymoo (NSGA-II), SciPy splines over Shell's official track coordinates |
| Autonomy | ROS 2 Jazzy, Gazebo Harmonic, NVIDIA Isaac Sim and OpenUSD, NVIDIA Jetson Orin, LiDAR and stereo camera, OpenCV |
| Data and web | MQTT, PostgreSQL with TimescaleDB, MCAP and Foxglove, Node.js, Express, Socket.IO, React |
| Engineering practice | Git and GitHub, GitHub Actions CI on every pull request, secret scanning, automated tests from the PC to the bench |

## How we work

- **Every change goes through a pull request** with automated checks. On the firmware that controls 48 V, safety-critical changes also need a recorded bench session before they count as done.
- **Agreements between areas are written down:** interface control documents for connectors and protocols, and architecture decision records for choices that cross areas.
- **Season gates and a code freeze** two weeks before the event, with a guaranteed fallback: the version that raced last season is always kept ready.
- **Measure, don't assume.** Every number in our models says whether it was measured or assumed, and the tests that will replace the assumptions are planned.
- **Built for new members.** Every repository has an entry guide written for first-year students: the minimum theory, the algorithms explained, a reading order and exercises.

## Members

Each member's work, season by season, is in the team's public portfolio: [`team-portfolio`](https://github.com/ELYOS-Racing/team-portfolio). The vehicles' code is private; members' contributions show on their profiles as private contributions.

Team member? Sign in with your GitHub account to see the members-only "Start here" guide.
