## 🤖 AI Agent using AWS Lambda + S3 + Bedrock

An intelligent, serverless AI agent powered by **Amazon Bedrock**, **AWS Lambda**, and **S3**, capable of responding to real-world user queries with contextual data stored in CSVs (e.g., hotels, Airbnbs, restaurants).

This modular AI Agent framework allows seamless integration of data-driven responses for dynamic use cases like listing properties, filtering restaurants, and enabling conversational AI through Amazon Bedrock Agents.

---

### 🚀 Features

* ✅ Modular AI Agent functions for **Hotels**, **Airbnbs**, and **Restaurants**
* ✅ Uses **AWS Lambda** for scalable, serverless compute
* ✅ **Amazon S3** stores structured datasets in CSV format
* ✅ Filters user queries with multiple parameters (e.g., pets allowed, pool availability, fine dining)
* ✅ Integrated with **Amazon Bedrock Agents** for natural conversation
* ✅ JSON-based interaction structure for easy front-end integration
* ✅ Easily extendable to other domains (e.g., Flights, Rentals, etc.)

---

### 🛠️ Installation & Setup

#### 1. Clone this Repository

```bash
git clone https://github.com/yourusername/aws-ai-agent.git
cd aws-ai-agent
```

#### 2. Upload Your Datasets to S3

Upload your CSV files (e.g., `hotel.csv`, `airbnb.csv`, `restaurant.csv`) to an S3 bucket:

```
s3://your-bucket-name/
├── hotel.csv
├── airbnb.csv
└── restaurant.csv
```

Update the `S3_BUCKET` and file keys in each Lambda function accordingly.

---

### 🧠 How It Works

#### 🏨 Hotel and Airbnb Finder Agent

```python
def lambda_handler(event, context):
    function = event.get("function")
    if function == "list-hotels":
        # Filter by location from hotel.csv
    elif function == "list-airbnbs":
        # Filter airbnb.csv by location, pets, pool, sauna
```

#### 🍽️ Restaurant Filter Agent

```python
def lambda_handler(event, context):
    # Filters restaurant.csv based on city and fine dining preference
```

#### 🗣️ Conversational Agent with Bedrock

```python
def lambda_handler(event, context):
    response = client.invoke_agent(
        agentId='your-agent-id',
        inputText=input_text,
        sessionId=session_id
    )
```

---

### 💬 Example Payloads

#### Hotel Query

```json
{
  "agent": "travel-bot",
  "actionGroup": "accommodation",
  "function": "list-hotels",
  "parameters": [
    {"name": "location", "value": "paris"}
  ]
}
```

#### Airbnb Query

```json
{
  "function": "list-airbnbs",
  "parameters": [
    {"name": "location", "value": "berlin"},
    {"name": "pets", "value": "yes"},
    {"name": "pool", "value": "no"},
    {"name": "sauna", "value": "yes"}
  ]
}
```

#### Restaurant Query

```json
{
  "function": "list-restaurants",
  "parameters": [
    {"name": "city", "value": "new york"},
    {"name": "fine_dine", "value": "yes"}
  ]
}
```

---

### 🔐 Bedrock Agent Integration

You'll need to configure your Amazon Bedrock agent and reference:

```python
response = client.invoke_agent(
    agentId='your-agent-id',
    agentAliasId='your-alias-id',
    sessionId=session_id,
    inputText="Find hotels in Tokyo"
)
```

---

### 📌 Requirements

* Python 3.8+
* AWS Lambda
* Amazon S3 Bucket
* Amazon Bedrock Agent (optional, for natural language responses)
* IAM roles with permissions for S3, Lambda, and Bedrock

---

### 🧪 Testing

You can test locally or use AWS Lambda test events with the JSON samples provided.

To test end-to-end:

1. Upload CSVs to your S3 bucket
2. Deploy Lambda functions
3. Configure Bedrock agent (optional)
4. Trigger the function via test event or REST API Gateway

---

### 🧩 Extensibility

You can easily add more domains:

* `flights.csv` → `list-flights`
* `cars.csv` → `list-cars`
* `events.csv` → `list-events`

Just create corresponding functions using the same template.

---

### 🙌 Acknowledgements

Thanks to:

* [AWS Lambda](https://aws.amazon.com/lambda/)
* [Amazon S3](https://aws.amazon.com/s3/)
* [Amazon Bedrock](https://aws.amazon.com/bedrock/)
* [Pandas](https://pandas.pydata.org/)
* [Hugging Face](https://huggingface.co/) *(if used for embeddings)*

---

