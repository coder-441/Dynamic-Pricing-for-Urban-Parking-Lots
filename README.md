Dynamic Pricing for Urban Parking Lots

This repository contains the implementation of a dynamic, data-driven pricing engine for urban parking spaces. It simulates real-time price adjustments based on demand, vehicle type, environmental conditions, and optional competitive behavior using the Pathway streaming framework.

📦 Project Structure

├── dataset.csv                   # Input dataset with parking lot status over time
├── stream_pipeline.py            # Main pipeline using Pathway
├── output/                       # Folder where real-time pricing predictions are saved
│   └── price_predictions.jsonl   # Output file with streaming price data
├── README.md                     # Project documentation

🚦 Features

Real-time data processing using Pathway

Three pricing models:

Model 1: Linear pricing based on occupancy

Model 2: Demand-based pricing using multiple real-time factors

Model 3: Optional competition-aware pricing using geographic distance

Streaming predictions to a .jsonl file

Custom UDFs to preprocess vehicle type and traffic conditions

🧪 How to Run

Prerequisites

Python 3.8+

Install dependencies:

pip install pathway pandas numpy matplotlib

Run the Stream Pipeline

python stream_pipeline.py

The pipeline will stream data from dataset.csv and output predictions to:

output/price_predictions.jsonl

🧠 Pricing Logic

Demand Function:

Demand = α*(Occupancy/Capacity) + β*Queue - γ*Traffic + δ*SpecialDay + ε*VehicleType
Price = Base * (1 + λ * NormalizedDemand)

Prices are clipped between $5 and $20

Vehicle types are weighted: car = 1.0, bike = 0.5, truck = 1.5

Traffic: low = 1, medium = 2, high = 3

📁 Dataset Fields

SystemCodeNumber: Unique lot ID

Capacity, Occupancy, QueueLength

VehicleType: car, bike, or truck

TrafficConditionNearby: low, medium, high

IsSpecialDay: 1 or 0

LastUpdatedDate, LastUpdatedTime

📈 Output Format

Each output row is written as JSON:

{
  "SystemCodeNumber": "BHMBCCMKT01",
  "LastUpdatedDate": "04-10-2016",
  "LastUpdatedTime": "09:59:00",
  "price": 13.25
}

📚 Resources

Pathway Docs

Summer Analytics 2025
