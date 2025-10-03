# AfriHub CLI: Your Local African API Hub

## Description:
AfriHub CLI is a command-line interface and local server for simulating African-specific APIs and generating mock datasets. It features an advanced AI-powered translation system with machine learning capabilities for 20+ African languages. It's designed for developers who need to test and build applications without relying on external services or an internet connection.

## Features:
*   **Comprehensive African API Simulation**: Simulate APIs for banks, telcos (USSD), weather, language translation, and currency exchange across 20+ African countries.
*   **Advanced Banking System**: 57 banks across 4 African countries with USSD codes, session management, secure PIN validation, and comprehensive banking operations.
*   **Enhanced Telecom System**: 15+ African telecom providers across 6 countries with advanced USSD flows, mobile money integration, and provider identification.
*   **AI-Powered Weather System**: Advanced machine learning weather prediction engine with forecasting, anomaly detection, and trend analysis for 100+ African cities.
*   **CLI API Testing**: Test APIs directly from the command line with the `afrihub api` command.
*   **Extensive Mock Data Generation**: Generate realistic mock data for African names, phone numbers, addresses, and bank details from multiple African regions.
*   **AI-Powered Translation**: Advanced machine learning translation with 200+ vocabulary words per language, sentence translation, and intelligent confidence scoring.
*   **Multi-Language Support**: Translation support for 20+ African languages including Yoruba, Swahili, Zulu, Amharic, Wolof, and more.
*   **Sandbox Environment**: Run a local server for rapid testing and development.
*   **Interactive Documentation**: Built-in documentation website with API testing interface. (coming soon)
*   **Offline Development**: Develop and test your applications entirely offline.

## Installation:

### Install from NPM Registry

**Quick Installation:**
```bash
npm install -g afrihub-cli
```

**Alternative Installation Methods:**
```bash
# Using npx (no global installation required)
npx afrihub-cli --help

# Using yarn
yarn global add afrihub-cli

# Using pnpm
pnpm add -g afrihub-cli
```

**Verify Installation:**
```bash
afrihub --help
```

**Windows Users Note:** If you encounter any issues with the CLI not being recognized, ensure your npm global bin directory is in your PATH. You can check this by running `npm config get prefix` and adding that directory to your system PATH.

## Usage:

The `afrihub` CLI provides several commands: `start`, `docs - (coming soon)`, `generate`, and `api`.

---

### `afrihub docs` - Serve Documentation Website (coming soon)

This command serves the interactive documentation website with API testing interface.

**Syntax:**
```bash
afrihub docs [options]
```

**Options:**
*   `--port <number>`: Specify the port for the docs server (default: 5173).
*   `--no-open`: Don't automatically open the browser.

**Examples:**
*   Start the docs server on the default port:
    ```bash
    afrihub docs
    ```
*   Start the docs server on a custom port:
    ```bash
    afrihub docs --port 8080
    ```
*   Start the docs server without opening browser:
    ```bash
    afrihub docs --no-open
    ```

### `afrihub api` - Simulate API Calls

This command allows you to simulate API calls directly from the command line without needing a browser or HTTP client.

**Syntax:**
```bash
afrihub api --endpoint <endpoint> [options]
```

**Options:**
*   `--endpoint <endpoint>`: API endpoint to simulate (`weather`, `bank`, `telco`, `currency`, `translation`, `mock`)
*   `--format <format>`: Output format (`json`, `table`) (default: `table`)
*   `--params <json>`: JSON string of parameters
*   Endpoint-specific options:
    *   `--city <city>`: City name for weather API
    *   `--from <from>`: Source currency/account for conversion/transfer
    *   `--to <to>`: Target currency/account for conversion/transfer
    *   `--amount <amount>`: Amount for conversion/transfer
    *   `--text <text>`: Text to translate
    *   `--phone <phone>`: Phone number for telco operations
    *   `--code <code>`: USSD code for telco operations
    *   `--bank <bank>`: Bank name for banking operations
    *   `--account <account>`: Account number for banking operations
    *   `--operation <operation>`: Banking operation (`info`, `balance`, `transfer`)
    *   `--type <type>`: Type of mock data to generate (20+ types available)
    *   `--count <count>`: Number of items to generate
    *   `--region <region>`: Region for mock data generation

**Examples:**

*   **Get weather for Lagos:**
    ```bash
    afrihub api --endpoint weather --city Lagos
    ```

*   **Convert USD to NGN:**
    ```bash
    afrihub api --endpoint currency --from USD --to NGN --amount 100
    ```

*   **Check bank balance:**
    ```bash
    afrihub api --endpoint bank --bank gtb --operation balance --account 0123456789
    ```

*   **Start USSD session:**
    ```bash
    afrihub api --endpoint telco --phone +2348031234567 --code "*131#"
    ```

*   **Translate text:**
    ```bash
    afrihub api --endpoint translation --text "hello" --from "en" --to "yo"
    ```

*   **Translate sentences with AI (Yoruba):**
    ```bash
    afrihub api --endpoint translation --text "good morning my friend" --from "en" --to "yo"
    ```

*   **Translate sentences with AI (Swahili):**
    ```bash
    afrihub api --endpoint translation --text "I want to buy food at the market" --from "en" --to "sw"
    ```

*   **Translate sentences with AI (Hausa):**
    ```bash
    afrihub api --endpoint translation --text "how are you today" --from "en" --to "ha"
    ```

*   **Translate sentences with AI (Zulu):**
    ```bash
    afrihub api --endpoint translation --text "I love my family" --from "en" --to "zu"
    ```

*   **Translate sentences with AI (Amharic):**
    ```bash
    afrihub api --endpoint translation --text "thank you very much" --from "en" --to "am"
    ```

*   **Translate sentences with AI (French):**
    ```bash
    afrihub api --endpoint translation --text "where is the hospital" --from "en" --to "fr"
    ```

*   **Generate mock data (20+ types available):**
    ```bash
    # Identity Documents
    afrihub api --endpoint mock --type passports --count 5 --region kenya
    afrihub api --endpoint mock --type driver-licenses --count 3 --region ghana
    afrihub api --endpoint mock --type national-ids --count 2 --region southafrica
    
    # Medical Data
    afrihub api --endpoint mock --type patients --count 5 --region nigeria
    afrihub api --endpoint mock --type prescriptions --count 3 --region kenya
    afrihub api --endpoint mock --type lab-results --count 4 --region ghana
    
    # Educational Records
    afrihub api --endpoint mock --type certificates --count 3 --region southafrica
    afrihub api --endpoint mock --type transcripts --count 2 --region nigeria
    afrihub api --endpoint mock --type student-ids --count 5 --region kenya
    
    # Property Documents
    afrihub api --endpoint mock --type property-deeds --count 3 --region ghana
    afrihub api --endpoint mock --type rental-agreements --count 4 --region nigeria
    afrihub api --endpoint mock --type property-values --count 2 --region southafrica
    
    # Financial Records
    afrihub api --endpoint mock --type credit-scores --count 3 --region kenya
    afrihub api --endpoint mock --type loan-applications --count 5 --region ghana
    afrihub api --endpoint mock --type insurance-claims --count 2 --region nigeria
    
    # Traditional Data
    afrihub api --endpoint mock --type names --count 5 --region nigeria
    afrihub api --endpoint mock --type phones --count 3 --region kenya
    afrihub api --endpoint mock --type addresses --count 4 --region ghana
    afrihub api --endpoint mock --type banks --count 2 --region southafrica
    afrihub api --endpoint mock --type currencies --count 5
    ```

*   **Output as JSON:**
    ```bash
    afrihub api --endpoint currency --from USD --to NGN --amount 100 --format json
    ```

### Translation API Examples

**Simple Word Translation:**
```bash
afrihub api --endpoint translation --text "hello" --from "en" --to "yo"
```
**Response:**
```json
{
  "originalText": "hello",
  "translatedText": "bawo",
  "confidence": 0.95,
  "translationMethod": "direct",
  "complexity": "simple"
}
```

**Sentence Translation with AI:**
```bash
afrihub api --endpoint translation --text "good morning my friend" --from "en" --to "yo"
```
**Response:**
```json
{
  "originalText": "good morning my friend",
  "translatedText": "o dara aro ile ore",
  "confidence": 0.95,
  "translationMethod": "machine_learning",
  "complexity": "basic",
  "suggestions": ["For complex sentences, consider breaking into shorter phrases"]
}
```

**Complex Sentence with ML:**
```bash
afrihub api --endpoint translation --text "I want to buy food at the market" --from "en" --to "yo"
```
**Response:**
```json
{
  "originalText": "I want to buy food at the market",
  "translatedText": "i fẹ to ra ounje at te ọja",
  "confidence": 0.7,
  "translationMethod": "machine_learning",
  "complexity": "intermediate",
  "suggestions": [
    "For complex sentences, consider breaking into shorter phrases",
    "Use simpler grammar patterns for better accuracy"
  ]
}
```

### Multi-Language Sentence Translation Examples

**Hausa Translation:**
```bash
afrihub api --endpoint translation --text "how are you today" --from "en" --to "ha"
```
**Response:**
```json
{
  "originalText": "how are you today",
  "translatedText": "yaya kake yau",
  "confidence": 0.85,
  "translationMethod": "machine_learning",
  "complexity": "basic"
}
```

**Zulu Translation:**
```bash
afrihub api --endpoint translation --text "I love my family" --from "en" --to "zu"
```
**Response:**
```json
{
  "originalText": "I love my family",
  "translatedText": "ngi thanda umndeni wami",
  "confidence": 0.8,
  "translationMethod": "machine_learning",
  "complexity": "basic"
}
```

**Amharic Translation:**
```bash
afrihub api --endpoint translation --text "thank you very much" --from "en" --to "am"
```
**Response:**
```json
{
  "originalText": "thank you very much",
  "translatedText": "ameseginalehu be'irgachew",
  "confidence": 0.75,
  "translationMethod": "machine_learning",
  "complexity": "basic"
}
```

**Wolof Translation:**
```bash
afrihub api --endpoint translation --text "welcome to senegal" --from "en" --to "wo"
```
**Response:**
```json
{
  "originalText": "welcome to senegal",
  "translatedText": "dalal ak jam senegal",
  "confidence": 0.7,
  "translationMethod": "machine_learning",
  "complexity": "basic"
}
```

**French Translation:**
```bash
afrihub api --endpoint translation --text "where is the hospital" --from "en" --to "fr"
```
**Response:**
```json
{
  "originalText": "where is the hospital",
  "translatedText": "où est l'hôpital",
  "confidence": 0.9,
  "translationMethod": "machine_learning",
  "complexity": "basic"
}
```

**Portuguese Translation:**
```bash
afrihub api --endpoint translation --text "good evening everyone" --from "en" --to "pt"
```
**Response:**
```json
{
  "originalText": "good evening everyone",
  "translatedText": "boa noite todos",
  "confidence": 0.85,
  "translationMethod": "machine_learning",
  "complexity": "basic"
}
```

---

## AI-Powered Weather API Features

AfriHub now includes an advanced Machine Learning weather prediction engine with comprehensive forecasting capabilities for African cities.

### Weather API Features:
- **Machine Learning Prediction Engine**: Advanced ML algorithms with pattern recognition and trend analysis
- **Real-time Weather with Confidence Scoring**: 60-95% accuracy based on known vs unknown patterns
- **5-day ML-powered Forecasts**: Detailed forecasts with temperature, humidity, wind, and pressure predictions
- **Weather Anomaly Detection**: Automatic detection of unusual weather patterns and alerts
- **Comprehensive Weather Reports**: Detailed analysis with insights and recommendations
- **Historical Pattern Analysis**: ML-based predictions using historical weather data
- **Climate-specific Modeling**: Tailored predictions for tropical, desert, savanna, and temperate climates
- **Multi-city Support**: Weather data for 100+ African cities across all major regions

### Weather API Endpoints:

#### 1. Basic Weather Information
```bash
afrihub api --endpoint weather --city Lagos
```
**Response:**
```json
{
  "success": true,
  "data": {
    "city": "Lagos",
    "temp": 28,
    "humidity": 85,
    "condition": "Partly Cloudy",
    "windSpeed": 12,
    "pressure": 1013,
    "confidence": 0.87,
    "trend": "rising",
    "timestamp": "2024-01-15T10:30:00.000Z"
  }
}
```

#### 2. ML-Powered Weather Forecast
```bash
# Get 5-day forecast (default)
curl http://localhost:3000/api/weather/lagos/forecast

# Get 7-day forecast
curl http://localhost:3000/api/weather/lagos/forecast?days=7
```
**Response:**
```json
{
  "success": true,
  "data": {
    "city": "Lagos",
    "forecast": [
      {
        "day": "1/16/2024",
        "temperature": 29,
        "condition": "Partly Cloudy",
        "confidence": 0.89,
        "trend": "rising",
        "humidity": 82,
        "windSpeed": 10,
        "pressure": 1012
      }
    ],
    "generatedAt": "2024-01-15T10:30:00.000Z",
    "method": "ml_prediction"
  }
}
```

#### 3. Comprehensive Weather Report
```bash
curl http://localhost:3000/api/weather/lagos/report
```
**Response:**
```json
{
  "success": true,
  "data": {
    "city": "Lagos",
    "current": {
      "temperature": 28,
      "humidity": 85,
      "windSpeed": 12,
      "pressure": 1013,
      "condition": "Partly Cloudy",
      "confidence": 0.87,
      "trend": "rising"
    },
    "forecast": [...],
    "anomalies": [
      {
        "timestamp": 1705312200000,
        "anomaly": "Rapid temperature change: 25°C → 32°C",
        "severity": "medium"
      }
    ],
    "insights": [
      "High humidity: May feel warmer than actual temperature",
      "Temperature trend: Warming up over the next few hours",
      "Tropical climate: High chance of afternoon thunderstorms"
    ],
    "generatedAt": "2024-01-15T10:30:00.000Z",
    "method": "ml_analysis"
  }
}
```

#### 4. Weather Anomaly Detection
```bash
curl http://localhost:3000/api/weather/lagos/anomalies
```
**Response:**
```json
{
  "success": true,
  "data": {
    "city": "Lagos",
    "anomalies": [
      {
        "timestamp": 1705312200000,
        "anomaly": "Rapid temperature change: 25°C → 32°C",
        "severity": "medium"
      },
      {
        "timestamp": 1705298400000,
        "anomaly": "Rapid humidity change: 70% → 95%",
        "severity": "high"
      }
    ],
    "detectedAt": "2024-01-15T10:30:00.000Z",
    "method": "ml_anomaly_detection"
  }
}
```

#### 5. Time-based Weather Prediction
```bash
# Predict weather in 6 hours
curl http://localhost:3000/api/weather/lagos/predict?hours=6

# Predict weather in 24 hours
curl http://localhost:3000/api/weather/lagos/predict?hours=24
```
**Response:**
```json
{
  "success": true,
  "data": {
    "city": "Lagos",
    "prediction": {
      "temperature": 30,
      "humidity": 88,
      "windSpeed": 15,
      "pressure": 1011,
      "condition": "Thunderstorms",
      "confidence": 0.82,
      "trend": "falling"
    },
    "predictedFor": "2024-01-15T16:30:00.000Z",
    "method": "ml_prediction"
  }
}
```

#### 6. Weather Trend Analysis
```bash
# Analyze trends over 7 days (default)
curl http://localhost:3000/api/weather/lagos/trends

# Analyze trends over 14 days
curl http://localhost:3000/api/weather/lagos/trends?days=14
```
**Response:**
```json
{
  "success": true,
  "data": {
    "city": "Lagos",
    "trends": [
      {
        "day": "1/16/2024",
        "temperature": 29,
        "humidity": 82,
        "windSpeed": 10,
        "pressure": 1012,
        "condition": "Partly Cloudy",
        "confidence": 0.89,
        "trend": "rising"
      }
    ],
    "summary": {
      "avgTemperature": 28,
      "minTemperature": 25,
      "maxTemperature": 32,
      "avgHumidity": 85,
      "overallTrend": "warming",
      "weatherPattern": "mixed conditions"
    },
    "analyzedAt": "2024-01-15T10:30:00.000Z",
    "method": "ml_trend_analysis"
  }
}
```

#### 7. Multiple Cities Weather
```bash
curl -X POST http://localhost:3000/api/weather/multiple \
  -H "Content-Type: application/json" \
  -d '{"cities": ["lagos", "nairobi", "cape town"]}'
```
**Response:**
```json
{
  "success": true,
  "data": [
    {
      "city": "Lagos",
      "temp": 28,
      "humidity": 85,
      "condition": "Partly Cloudy",
      "windSpeed": 12,
      "pressure": 1013,
      "confidence": 0.87,
      "trend": "rising",
      "timestamp": "2024-01-15T10:30:00.000Z"
    },
    {
      "city": "Nairobi",
      "temp": 22,
      "humidity": 70,
      "condition": "Cloudy",
      "windSpeed": 15,
      "pressure": 1015,
      "confidence": 0.91,
      "trend": "stable",
      "timestamp": "2024-01-15T10:30:00.000Z"
    }
  ]
}
```

### Supported African Cities:
- **Nigeria**: Lagos, Abuja, Kano, Ibadan, Port Harcourt
- **Kenya**: Nairobi, Mombasa, Kisumu, Nakuru
- **South Africa**: Cape Town, Johannesburg, Durban, Pretoria
- **Ghana**: Accra, Kumasi, Tamale
- **Egypt**: Cairo, Alexandria
- **Morocco**: Casablanca, Rabat, Marrakech
- **Ethiopia**: Addis Ababa, Dire Dawa
- **Tanzania**: Dar es Salaam, Dodoma, Arusha
- **Uganda**: Kampala, Jinja
- **Rwanda**: Kigali
- **Senegal**: Dakar
- **Ivory Coast**: Abidjan, Yamoussoukro
- **Algeria**: Algiers, Oran
- **Tunisia**: Tunis, Sfax
- **Libya**: Tripoli, Benghazi
- **Sudan**: Khartoum, Port Sudan
- **Zimbabwe**: Harare, Bulawayo
- **Zambia**: Lusaka, Ndola
- **Botswana**: Gaborone, Francistown
- **Namibia**: Windhoek, Walvis Bay
- **Mozambique**: Maputo, Beira
- **Angola**: Luanda, Huambo
- **Malawi**: Lilongwe, Blantyre
- **Madagascar**: Antananarivo, Toamasina
- **Cameroon**: Yaoundé, Douala
- **DRC**: Kinshasa, Lubumbashi
- **Republic of Congo**: Brazzaville
- **Central African Republic**: Bangui
- **Chad**: N'Djamena
- **Niger**: Niamey
- **Mali**: Bamako, Timbuktu
- **Burkina Faso**: Ouagadougou
- **Guinea**: Conakry
- **Sierra Leone**: Freetown
- **Liberia**: Monrovia

---

## Enhanced Banking API Features

AfriHub now includes a comprehensive banking system with advanced querying and management capabilities for African financial institutions.

### Banking API Features:
- **100+ African Banks**: Comprehensive database of banks from 15+ African countries
- **Advanced Pagination**: Efficient data retrieval with customizable page sizes
- **Smart Filtering**: Filter banks by country, region, or specific criteria
- **Powerful Search**: Search across bank names, codes, SWIFT codes, and websites
- **Comprehensive Statistics**: Detailed analytics and breakdowns
- **Country-Specific Lists**: Get banks filtered by country code
- **Real-time Validation**: Account number validation against bank formats
- **Secure Session Management**: Banking sessions with PIN validation and expiry
- **PIN Security**: 4-6 digit PIN validation with attempt tracking
- **Session Expiry**: 30-minute session timeout with automatic cleanup
- **USSD Simulation**: Complete mobile banking session simulation

### Banking API Endpoints:

#### 1. List All Banks with Pagination
```bash
# Basic pagination (20 banks per page)
curl "http://localhost:3000/api/banking/banks"

# Custom pagination
curl "http://localhost:3000/api/banking/banks?page=2&limit=10"

# Filter by country
curl "http://localhost:3000/api/banking/banks?country=NG&page=1&limit=5"

# Search and paginate
curl "http://localhost:3000/api/banking/banks?search=gtb&page=1&limit=10"

# Sort and paginate
curl "http://localhost:3000/api/banking/banks?sortBy=name&sortOrder=desc&page=1&limit=15"
```
**Response:**
```json
{
  "success": true,
  "data": [
    {
      "name": "Guaranty Trust Bank Plc",
      "shortName": "gtb",
      "country": "Nigeria",
      "countryCode": "NG",
      "cbnCode": "058",
      "swiftCode": "GTBINGLA",
      "accountNumberFormat": {
        "length": 10,
        "type": "NUBAN",
        "checkDigitIncluded": true
      },
      "ussdCode": "*737#",
      "website": "https://www.gtbank.com",
      "founded": 1990
    }
  ],
  "pagination": {
    "currentPage": 1,
    "totalPages": 5,
    "totalBanks": 100,
    "banksPerPage": 20,
    "hasNextPage": true,
    "hasPrevPage": false
  },
  "statistics": {
    "totalBanks": 100,
    "countries": 12,
    "countryBreakdown": {
      "Nigeria": 25,
      "South Africa": 18,
      "Kenya": 15
    }
  }
}
```

#### 2. Bank Statistics
```bash
curl "http://localhost:3000/api/banking/banks/stats"
```
**Response:**
```json
{
  "success": true,
  "data": {
    "totalBanks": 100,
    "totalCountries": 12,
    "countryBreakdown": {
      "Nigeria": 25,
      "South Africa": 18,
      "Kenya": 15,
      "Ghana": 12
    },
    "accountFormatBreakdown": {
      "NUBAN": 45,
      "Universal": 30,
      "Mobile": 25
    },
    "foundingYearBreakdown": {
      "1990": 8,
      "2000": 12,
      "2010": 15
    },
    "oldestBank": {
      "name": "First Bank of Nigeria Plc",
      "founded": 1894
    },
    "newestBank": {
      "name": "Kuda Bank",
      "founded": 2019
    }
  }
}
```

#### 3. Banks by Country
```bash
# Get Nigerian banks
curl "http://localhost:3000/api/banking/banks/country/NG?page=1&limit=5"

# Get Kenyan banks
curl "http://localhost:3000/api/banking/banks/country/KE?page=1&limit=10"
```
**Response:**
```json
{
  "success": true,
  "data": [
    {
      "name": "Access Bank Nigeria Plc",
      "shortName": "access",
      "country": "Nigeria",
      "countryCode": "NG",
      "cbnCode": "044",
      "swiftCode": "ABNGNGLA",
      "ussdCode": "*901#",
      "website": "https://www.accessbankplc.com",
      "founded": 1989
    }
  ],
  "pagination": {
    "currentPage": 1,
    "totalPages": 5,
    "totalBanks": 25,
    "banksPerPage": 5,
    "hasNextPage": true,
    "hasPrevPage": false
  },
  "country": "NG"
}
```

#### 4. Search Banks
```bash
# Search for banks containing "access"
curl "http://localhost:3000/api/banking/banks/search?q=access&page=1&limit=5"

# Search by country
curl "http://localhost:3000/api/banking/banks/search?q=nigeria&page=1&limit=10"
```
**Response:**
```json
{
  "success": true,
  "data": [
    {
      "name": "Access Bank Nigeria Plc",
      "shortName": "access",
      "country": "Nigeria",
      "countryCode": "NG",
      "cbnCode": "044",
      "swiftCode": "ABNGNGLA",
      "ussdCode": "*901#",
      "website": "https://www.accessbankplc.com",
      "founded": 1989
    }
  ],
  "pagination": {
    "currentPage": 1,
    "totalPages": 2,
    "totalBanks": 8,
    "banksPerPage": 5,
    "hasNextPage": true,
    "hasPrevPage": false
  },
  "searchQuery": "access"
}
```

#### 5. Banking Session Management
```bash
# Create a new banking session
curl -X POST "http://localhost:3000/api/banking/gtb/session" \
  -H "Content-Type: application/json" \
  -d '{
    "phoneNumber": "+2348012345678",
    "accountNumber": "0123456789"
  }'
```
**Response:**
```json
{
  "success": true,
  "data": {
    "sessionId": "SES_1705312200000_GTB_abc123",
    "bank": "Guaranty Trust Bank Plc",
    "bankCode": "gtb",
    "expiresIn": 30,
    "createdAt": "2024-01-15T10:30:00.000Z",
    "message": "Banking session created for Guaranty Trust Bank Plc"
  }
}
```

#### 6. Secure Banking Operations with Session
```bash
# Check account balance with session and PIN
curl -X POST "http://localhost:3000/api/banking/gtb/balance" \
  -H "Content-Type: application/json" \
  -d '{
    "accountNumber": "0123456789",
    "sessionId": "SES_1705312200000_GTB_abc123",
    "pin": "1234"
  }'

# Transfer money with session and PIN
curl -X POST "http://localhost:3000/api/banking/gtb/transfer" \
  -H "Content-Type: application/json" \
  -d '{
    "amount": 1000,
    "recipient": "John Doe",
    "accountNumber": "0123456789",
    "sessionId": "SES_1705312200000_GTB_abc123",
    "pin": "1234"
  }'
```
**Response:**
```json
{
  "success": true,
  "data": {
    "accountNumber": "0123456789",
    "balance": "₦50,000.00",
    "accountName": "John Doe",
    "lastTransaction": "2024-01-15T10:30:00Z"
  },
  "security": {
    "requiresPin": true,
    "pinValidated": true
  }
}
```

#### 7. Traditional Banking Operations (No Session)
```bash
# Get bank information
curl "http://localhost:3000/api/banking/gtb"

# Check account balance without session (no PIN required)
curl -X POST "http://localhost:3000/api/banking/gtb/balance" \
  -H "Content-Type: application/json" \
  -d '{"accountNumber": "0123456789"}'

# Transfer money without session (no PIN required)
curl -X POST "http://localhost:3000/api/banking/gtb/transfer" \
  -H "Content-Type: application/json" \
  -d '{"amount": 1000, "recipient": "John Doe", "accountNumber": "0123456789"}'
```

## 🔐 Banking Security & Session Management

### **Complete Banking Flow:**

#### **Step 1: Create Banking Session**
```bash
curl -X POST "http://localhost:3000/api/banking/gtb/session" \
  -H "Content-Type: application/json" \
  -d '{
    "phoneNumber": "+2348012345678",
    "accountNumber": "0123456789"
  }'
```

#### **Step 2: Use Session for Secure Operations**
```bash
# Balance check with PIN
curl -X POST "http://localhost:3000/api/banking/gtb/balance" \
  -H "Content-Type: application/json" \
  -d '{
    "accountNumber": "0123456789",
    "sessionId": "SES_1705312200000_GTB_abc123",
    "pin": "1234"
  }'

# Transfer with PIN
curl -X POST "http://localhost:3000/api/banking/gtb/transfer" \
  -H "Content-Type: application/json" \
  -d '{
    "amount": 1000,
    "recipient": "John Doe",
    "accountNumber": "0123456789",
    "sessionId": "SES_1705312200000_GTB_abc123",
    "pin": "1234"
  }'
```

### **Test PINs for Development:**
- **`1234`** - Most common test PIN
- **`0000`** - Simple test PIN  
- **`1111`** - Another common test PIN
- **`9999`** - Alternative test PIN

### **Session Security Features:**
- ✅ **Session Expiry**: 30-minute timeout
- ✅ **PIN Attempt Tracking**: Max 3 attempts before lockout
- ✅ **Session Validation**: Bank-specific session matching
- ✅ **Automatic Cleanup**: Expired sessions removed automatically
- ✅ **Secure Format**: `SES_{timestamp}_{BANK}_{random}`

### **Error Handling:**
```json
// Invalid Session
{
  "success": false,
  "error": "Invalid session ID"
}

// Expired Session
{
  "success": false,
  "error": "Session has expired"
}

// Session Locked
{
  "success": false,
  "error": "Too many PIN attempts. Session locked"
}

// Invalid PIN
{
  "success": false,
  "error": "Invalid PIN",
  "attemptsRemaining": 2
}
```

### Supported Countries:
- **Nigeria (NG)**: 25+ banks including GTBank, Access, First Bank, UBA, Zenith
- **South Africa (ZA)**: Standard Bank, FNB, Nedbank, Absa, Capitec
- **Kenya (KE)**: KCB, Equity, Co-op Bank, NCBA, M-Pesa
- **Ghana (GH)**: GCB, Ecobank, Standard Chartered, MTN MoMo
- **Ethiopia (ET)**: CBE, Awash, Dashen, Bank of Abyssinia
- **Tanzania (TZ)**: CRDB, NMB, Equity, Vodacom M-Pesa
- **Uganda (UG)**: Centenary, Stanbic, Equity, MTN MoMo
- **Rwanda (RW)**: Bank of Kigali, Equity, MTN MoMo
- **Senegal (SN)**: Société Générale, Ecobank, Orange Money
- **Ivory Coast (CI)**: Ecobank, SGBCI, Orange Money, MTN MoMo
- **Egypt (EG)**: NBE, Banque Misr, CIB, Fawry
- **Morocco (MA)**: Attijariwafa, Banque Populaire, BMCE
- **And more African countries with mobile money integration**

---

## Currency Exchange System

**Advanced African currency exchange system with 40+ currencies and market simulation**

### Currency API Features:
- **40+ African and Global Currencies** - Complete coverage of African regions plus major world currencies
- **Real-time Exchange Rate Simulation** - Dynamic rates with realistic market volatility
- **Historical Rate Data** - Track currency trends and patterns over time
- **Market Volatility Modeling** - Weekend effects, currency stability factors
- **Bulk Currency Conversion** - Convert one currency to multiple others in a single request
- **Regional Currency Filtering** - Filter currencies by African regions
- **Cross-rate Calculations** - Automatic USD-based cross-rate calculations
- **Currency Analytics** - Statistics, volatility rankings, and market insights

### Supported Currencies:

**Major Global Currencies:**
- USD, EUR, GBP, JPY, CAD, AUD, CHF, CNY

**West African Currencies:**
- NGN (Nigerian Naira), GHS (Ghanaian Cedi), XOF (West African CFA Franc)
- GMD (Gambian Dalasi), SLL (Sierra Leonean Leone), LRD (Liberian Dollar)

**East African Currencies:**
- KES (Kenyan Shilling), UGX (Ugandan Shilling), TZS (Tanzanian Shilling)
- RWF (Rwandan Franc), ETB (Ethiopian Birr), SOS (Somali Shilling), DJF (Djiboutian Franc)

**Southern African Currencies:**
- ZAR (South African Rand), BWP (Botswana Pula), NAD (Namibian Dollar)
- SZL (Swazi Lilangeni), LSL (Lesotho Loti), ZMW (Zambian Kwacha)
- MWK (Malawian Kwacha), ZWL (Zimbabwean Dollar), MZN (Mozambican Metical), AOA (Angolan Kwanza)

**North African Currencies:**
- EGP (Egyptian Pound), MAD (Moroccan Dirham), TND (Tunisian Dinar)
- DZD (Algerian Dinar), LYD (Libyan Dinar), SDG (Sudanese Pound), ERN (Eritrean Nakfa)

**Indian Ocean:**
- KMF (Comorian Franc)

### Currency API Endpoints:

#### 1. Currency Conversion
```bash
# Convert USD to Nigerian Naira
curl "http://localhost:3000/api/currency/convert?from=USD&to=NGN&amount=100"
```

**Enhanced Response:**
```json
{
  "success": true,
  "data": {
    "from": "USD",
    "to": "NGN",
    "amount": 100,
    "convertedAmount": 46050.00,
    "rate": 460.500000,
    "timestamp": "2024-01-15T10:30:00.000Z",
    "source": "African Currency Exchange Simulator",
    "currencyInfo": {
      "from": {
        "code": "USD",
        "name": "US Dollar",
        "symbol": "$",
        "country": "United States",
        "region": "North America",
        "isMajor": true
      },
      "to": {
        "code": "NGN",
        "name": "Nigerian Naira",
        "symbol": "₦",
        "country": "Nigeria",
        "region": "West Africa",
        "isMajor": true
      }
    },
    "marketData": {
      "volatility": 0.025,
      "trend": 0.001,
      "volume": 856420.50
    }
  }
}
```

#### 2. List All Currencies
```bash
# Get all supported currencies
curl "http://localhost:3000/api/currency/currencies"

# Get major currencies only
curl "http://localhost:3000/api/currency/currencies/major"
```

#### 3. Regional Currency Filtering
```bash
# Get West African currencies
curl "http://localhost:3000/api/currency/currencies/region/west-africa"

# Get East African currencies
curl "http://localhost:3000/api/currency/currencies/region/east-africa"
```

#### 4. Currency Information
```bash
# Get detailed info about Nigerian Naira
curl "http://localhost:3000/api/currency/currencies/NGN"
```

#### 5. Exchange Rates
```bash
# Get all rates for USD
curl "http://localhost:3000/api/currency/rates/USD"

# Get all rates for EUR
curl "http://localhost:3000/api/currency/rates/EUR"
```

#### 6. Historical Rate Data
```bash
# Get 7-day history for USD to NGN
curl "http://localhost:3000/api/currency/history/USD/NGN?days=7"

# Get 30-day history for EUR to KES
curl "http://localhost:3000/api/currency/history/EUR/KES?days=30"
```

**Historical Data Response:**
```json
{
  "success": true,
  "data": {
    "pair": "USD-NGN",
    "history": [
      {
        "timestamp": "2024-01-14T00:00:00.000Z",
        "rate": 458.75,
        "volume": 1250000.00,
        "volatility": 0.023
      },
      {
        "timestamp": "2024-01-15T00:00:00.000Z",
        "rate": 460.50,
        "volume": 1380000.00,
        "volatility": 0.025
      }
    ],
    "days": 7,
    "count": 7
  }
}
```

#### 7. Bulk Currency Conversion
```bash
# Convert USD to multiple African currencies
curl -X POST "http://localhost:3000/api/currency/convert/bulk" \
  -H "Content-Type: application/json" \
  -d '{
    "from": "USD",
    "conversions": [
      { "to": "NGN", "amount": 100 },
      { "to": "KES", "amount": 50 },
      { "to": "ZAR", "amount": 75 },
      { "to": "GHS", "amount": 25 }
    ]
  }'
```

#### 8. Currency Statistics
```bash
# Get comprehensive currency system statistics
curl "http://localhost:3000/api/currency/stats"
```

**Statistics Response:**
```json
{
  "success": true,
  "data": {
    "totalCurrencies": 40,
    "majorCurrencies": 8,
    "regions": 6,
    "regionsList": [
      "North America",
      "Europe", 
      "Asia",
      "West Africa",
      "East Africa",
      "Southern Africa",
      "North Africa",
      "Indian Ocean"
    ],
    "mostVolatile": ["ZWL", "SOS", "SDG", "SLL", "LRD"],
    "leastVolatile": ["USD", "EUR", "GBP", "JPY", "CHF"],
    "lastUpdated": "2024-01-15T10:30:00.000Z"
  }
}
```

### Advanced Features:

**Market Volatility Modeling:**
- Major currencies have lower volatility (2-3%)
- Minor currencies have higher volatility (3-4%)
- Weekend effect increases volatility by 0.5%
- Time-based trend simulation

**Cross-Rate Calculations:**
- Automatic USD-based cross-rates for unsupported pairs
- Realistic fallback rate generation
- Currency characteristic-based rate estimation

**Historical Data Simulation:**
- 30+ days of historical data for major pairs
- Realistic market trends and patterns
- Volume and volatility tracking
- On-demand history generation

---

## Supported Countries & Languages

### Countries (20+)
- **West Africa**: Nigeria, Ghana, Senegal, Ivory Coast, Mali, Burkina Faso, Guinea, Sierra Leone, Liberia
- **East Africa**: Kenya, Tanzania, Uganda, Rwanda, Ethiopia
- **Southern Africa**: South Africa, Zimbabwe, Zambia, Botswana, Namibia, Mozambique, Angola, Malawi, Madagascar
- **North Africa**: Egypt, Morocco, Algeria, Tunisia, Libya, Sudan

### Currencies (40+)
**Major Global**: USD, EUR, GBP, JPY, CAD, AUD, CHF, CNY
**African Currencies**: NGN, KES, GHS, ZAR, ETB, UGX, TZS, RWF, MWK, ZMW, BWP, SLL, GMD, LRD, SZL, LSL, NAD, AOA, MZN, ZWL, XAF, XOF, DZD, EGP, MAD, TND, LYD, SDG, ERN, SOS, DJF, KMF

**NEW: Advanced Currency Exchange System**
Complete currency exchange simulation with:
- Real-time rate simulation with market volatility
- Historical rate data and trend analysis
- Bulk currency conversion capabilities
- Regional currency filtering
- Cross-rate calculations and market analytics

### Languages (20+)
- **Nigerian**: Yoruba (yo), Igbo (ig), Hausa (ha)
- **East African**: Swahili (sw), Amharic (am), Kinyarwanda (rw), Luganda (lg)
- **Southern African**: Zulu (zu), Afrikaans (af), Chichewa (ny)
- **West African**: Twi (tw), Wolof (wo), Bambara (bm)
- **Central African**: Lingala (ln)
- **North African**: Arabic (ar), French (fr), Portuguese (pt)
- **Other**: Somali (so)

**NEW: Full Sentence Translation Support**
All 20+ languages now support complete sentence translation with:
- Language-specific grammar models and sentence patterns
- Contextual translation rules and phonetic mappings
- Machine learning algorithms for unknown words
- Confidence scoring and complexity assessment

### Banking Systems
Over 100+ African banks across 15+ countries with advanced features including pagination, filtering, search, and comprehensive statistics. Realistic USSD codes, account formats, and banking operations simulation.

### AI Translation Features
- **Machine Learning Algorithm**: Local ML engine with word vectors, similarity matching, and contextual rules
- **Extensive Vocabulary**: 200+ words per language with comprehensive categories (family, food, technology, business, etc.)
- **Full Sentence Translation**: Complete sentence processing with intelligent word-by-word translation for ALL 20+ African languages
- **Multi-Language Grammar Models**: Language-specific grammar rules, sentence patterns, and phonetic mappings
- **Confidence Scoring**: Dynamic confidence levels based on known vs unknown words (60-95%)
- **Translation Methods**: Direct dictionary lookup, ML single-word, and ML sentence translation
- **Intelligent Suggestions**: Context-aware recommendations for better translations
- **Advanced Grammar Rules**: Suffix recognition, contextual translation, and phonetic mapping for unknown words
- **Complexity Assessment**: Automatic classification of translation difficulty (simple, basic, intermediate, complex)
- **Universal Language Support**: Sentence translation now works for all supported languages, not just Yoruba and Swahili

---

### `afrihub start` - Start the Local API Server

This command launches a local API server, providing endpoints for all simulated African APIs.

**Syntax:**
```bash
afrihub start [options]
```

**Options:**
*   `--port <number>`: Specify the port for the API server (default: 3000).

**Examples:**
*   Start the server on the default port:
    ```bash
    afrihub start
    ```
*   Start the server on port 5000:
    ```bash
    afrihub start --port 5000
    ```

Once the server is running, you can access the API endpoints (e.g., `http://localhost:3000/weather/lagos`).

---

### `afrihub generate` - Generate African Mock Data

This command allows you to generate various types of mock data.

**Syntax:**
```bash
afrihub generate [options]
```

**Options:**
*   `-t, --type <type>`: Type of data to generate (20+ types available). If not specified, an interactive prompt will appear.
*   `-c, --count <number>`: Number of items to generate (default: 10).
*   `-f, --format <format>`: Output format (`json`, `csv`, `table`) (default: `table`).
*   `-o, --output <file>`: Save output to a specified file.
*   `-r, --region <region>`: African region/country (`nigeria`, `kenya`, `ghana`, `southafrica`) (default: `nigeria`).

**Examples:**

*   **Interactive Data Generation:**
    ```bash
    afrihub generate
    ```
    (You will be prompted to select type, region, and count)

*   **Generate 50 Nigerian names as JSON:**
    ```bash
    afrihub generate --type name --count 50 --region nigeria --format json
    ```
*   **Generate 20 Kenyan phone numbers and save to a CSV file:**
    ```bash
    afrihub generate --type phone --count 20 --region kenya --format csv --output kenyan_phones.csv
    ```
*   **Generate bank details for South Africa:**
    ```bash
    afrihub generate --type bank --region southafrica
    ```
*   **Generate currency data (region is not applicable for this type):**
    ```bash
    afrihub generate --type currency --format json
    ```

### Available Mock Data Types (20+ Types)

**Identity Documents:**
- `passports` - Generate passport records with authentic African names
- `driver-licenses` - Generate driver license records with regional formats
- `national-ids` - Generate national ID records with country-specific formats

**Medical Data:**
- `patients` - Generate comprehensive patient medical records
- `prescriptions` - Generate prescription records with medications and dosages
- `lab-results` - Generate laboratory test results with normal ranges

**Educational Records:**
- `certificates` - Generate educational certificates from authentic African universities
- `transcripts` - Generate academic transcripts with course details and GPA
- `student-ids` - Generate student identification cards with program details

**Property Documents:**
- `property-deeds` - Generate property deed records with land size and values
- `rental-agreements` - Generate rental agreements with tenant and landlord details
- `property-values` - Generate property valuation records with appreciation rates

**Financial Records:**
- `credit-scores` - Generate credit score reports with ratings and payment history
- `loan-applications` - Generate loan application records with terms and calculations
- `insurance-claims` - Generate insurance claim records with incident details

**Traditional Data:**
- `names` - Generate authentic African names by region and ethnicity
- `phones` - Generate phone numbers with country-specific formats
- `addresses` - Generate realistic African addresses with cities and streets
- `banks` - Generate bank account information with regional banks
- `currencies` - Generate currency exchange data with rates and historical information

---

### `afrihub api` - Simulate API Calls

This command allows you to interact with the simulated African APIs directly from the command line.

**Syntax:**
```bash
afrihub api [options]
```

**Options:**
*   `--endpoint <endpoint>`: The API endpoint to simulate (`weather`, `bank`, `telco`, `currency`, `translation`).
*   `--params <json-string>`: JSON string of parameters for the API call (e.g., `'{"city": "Lagos"}'`).
*   `--format <format>`: Output format (`json`, `table`) (default: `table`).
*   Additional endpoint-specific options (e.g., `--city`, `--from`, `--to`, `--amount`, `--text`, `--phone`, `--code`).

**Examples:**

*   **Get weather for Nairobi:**
    ```bash
    afrihub api --endpoint weather --city Nairobi
    ```
    Or:
    ```bash
    afrihub api --endpoint weather --params '{"city": "Nairobi"}'
    ```

*   **Simulate currency conversion from USD to NGN:**
    ```bash
    afrihub api --endpoint currency --from USD --to NGN --amount 100
    ```
    Or:
    ```bash
    afrihub api --endpoint currency --params '{"from": "USD", "to": "NGN", "amount": 100}'
    ```

*   **Simulate USSD request for a Nigerian phone number:**
    To use the interactive USSD flow, you'll first start a session and then send inputs to it.

    **Step 1: Start a USSD Session (e.g., for GTBank)**

    *   **HTTP Method:** `POST`
    *   **Request URL:** `http://localhost:3000/api/banking/gtb/ussd/start` (Replace `gtb` with the bank's short name)

    **Postman Body (raw, JSON):**
    ```json
    {}
    ```
    (Optional: You can include `"code": "*737#"` and `"phoneNumber": "+2348031234567"` in the body to specify an initial USSD code or phone number.)

    *   **Postman Response:** Copy the `sessionId` from the response.
        ```json
        {
            "success": true,
            "data": {
                "sessionId": "SES1234567890", 
                "message": "Welcome to GTBank (*737#)\n1. Balance\n2. Transfer\n...",
                "isFinal": false,
                "status": "continue"
            }
        }
        ```

    **Step 2: Continue a USSD Session (e.g., Select '1' for Balance)**

    *   **HTTP Method:** `POST`
    *   **Request URL:** `http://localhost:3000/api/banking/gtb/ussd/YOUR_SESSION_ID_HERE` (Replace `YOUR_SESSION_ID_HERE` with the ID you copied)

    **Postman Body (raw, JSON):**
    ```json
    {
        "input": "1"
    }
    ```

    *   **Postman Response:** The server will respond with the next menu or prompt.
        ```json
        {
            "success": true,
            "data": {
                "sessionId": "SES1234567890",
                "message": "Enter 10-digit account number or type 1 for My Account:",
                "isFinal": false,
                "status": "continue"
            }
        }
        ```

    Continue sending `POST` requests to the same session URL (`/api/banking/:bank/ussd/:sessionId`) with subsequent `"input": "your_choice"` in the body, following the prompts until `"isFinal": true`.

---

## Recent Updates

### Enhanced Translation System (Latest)
- **Universal Sentence Translation**: Extended sentence translation capabilities to all 20+ African languages
- **Advanced Language Models**: Added comprehensive grammar rules, sentence patterns, and phonetic mappings for each language
- **Improved Machine Learning**: Enhanced ML algorithms with better contextual translation and confidence scoring
- **Multi-Language Grammar**: Language-specific grammar rules including articles, pronouns, verbs, adjectives, and prepositions
- **Contextual Translation**: Smart suffix recognition and phonetic mapping for unknown words
- **Better Accuracy**: Improved translation quality with confidence scores ranging from 60-95%

### Supported Sentence Translation Languages
All languages now support full sentence translation:
- **Nigerian Languages**: Yoruba, Igbo, Hausa
- **East African Languages**: Swahili, Amharic, Kinyarwanda, Luganda
- **Southern African Languages**: Zulu, Afrikaans, Chichewa
- **West African Languages**: Twi, Wolof, Bambara
- **Central African Languages**: Lingala
- **North African Languages**: Arabic, French, Portuguese
- **Other Languages**: Somali

## 🏦 Enhanced Bank USSD System

AfriHub now features a comprehensive Bank USSD system with **57 banks across 4 African countries**, each with unique USSD codes and interactive session management.

### Bank USSD Features:
- **57 African Banks**: Comprehensive database across Nigeria, Kenya, South Africa, and Ghana
- **Unique USSD Codes**: Each bank has its authentic USSD code for realistic simulation
- **Auto-Detection**: Bank automatically identified from USSD code (no need to specify bank in URL)
- **Interactive Sessions**: Full USSD flow simulation with state management
- **Session Management**: 5-minute session timeout with automatic cleanup
- **Real Banking Flows**: Authentic USSD menu structures and responses
- **Multi-Country Support**: Banks from Nigeria, Kenya, South Africa, and Ghana

### Bank USSD API Endpoints:

#### 1. Start Bank USSD Session
```bash
# Bank is auto-detected from USSD code
curl -X POST "http://localhost:3000/api/banking/ussd/start" \
  -H "Content-Type: application/json" \
  -d '{
    "code": "*737#",
    "phoneNumber": "+2348031234567"
  }'
```

**Response:**
```json
{
  "success": true,
  "data": {
    "sessionId": "USS_1703123456789_GTB_ABC123",
    "message": "Welcome to GTBank *737#\n1. Balance\n2. Transfer\n3. Airtime\n4. Bills",
    "isFinal": false,
    "bank": "Guaranty Trust Bank Plc",
    "ussdCode": "*737#"
  }
}
```

#### 2. Continue Bank USSD Session
```bash
# Continue the USSD session with user input
curl -X POST "http://localhost:3000/api/banking/ussd/{sessionId}" \
  -H "Content-Type: application/json" \
  -d '{"input": "1"}'
```

**Response:**
```json
{
  "success": true,
  "data": {
    "sessionId": "USS_1703123456789_GTB_ABC123",
    "message": "Enter your account number:",
    "isFinal": false
  }
}
```

### Supported Banks & USSD Codes:

#### 🇳🇬 Nigerian Banks (32 banks):
| Bank | USSD Code | Short Name |
|------|-----------|------------|
| **Access Bank** | `*901#` | `access` |
| **First Bank** | `*894#` | `fbn` |
| **GTBank** | `*737#` | `gtb` |
| **Zenith Bank** | `*966#` | `zenith` |
| **UBA** | `*919#` | `uba` |
| **Fidelity Bank** | `*770#` | `fidelity` |
| **Union Bank** | `*826#` | `union` |
| **Ecobank Nigeria** | `*326#` | `ecobank` |
| **FCMB** | `*214#` | `fcmb` |
| **Wema Bank** | `*945#` | `wema` |
| **Polaris Bank** | `*833#` | `polaris` |
| **Stanbic IBTC** | `*909#` | `stanbic` |
| *...and 20 more Nigerian banks* | | |

#### 🇰🇪 Kenyan Banks (12 banks):
| Bank | USSD Code | Short Name |
|------|-----------|------------|
| **Equity Bank** | `*247#` | `equity_ke` |
| **KCB Bank** | `*522#` | `kcb` |
| **Cooperative Bank** | `*667#` | `coop_bank` |
| **Standard Chartered** | `*200#` | `sc_ke` |
| **Absa Bank** | `*130#` | `absa_ke` |
| **NCBA Bank** | `*488#` | `ncba` |
| *...and 6 more Kenyan banks* | | |

#### 🇿🇦 South African Banks (8 banks):
| Bank | USSD Code | Short Name |
|------|-----------|------------|
| **Standard Bank** | `*120*001#` | `standard_sa` |
| **FirstRand Bank** | `*120*321#` | `firstrand` |
| **Absa Bank** | `*120*227#` | `absa_sa` |
| **Capitec Bank** | `*120*3279#` | `capitec` |
| *...and 4 more South African banks* | | |

#### 🇬🇭 Ghanaian Banks (10 banks):
| Bank | USSD Code | Short Name |
|------|-----------|------------|
| **Ghana Commercial Bank** | `*422#` | `gcb` |
| **Ecobank Ghana** | `*326#` | `ecobank_gh` |
| **Zenith Bank Ghana** | `*966#` | `zenith_gh` |
| **Access Bank Ghana** | `*901#` | `access_gh` |
| *...and 6 more Ghanaian banks* | | |

### Complete Bank USSD Flow Example:

#### Step 1: Start USSD Session
```bash
curl -X POST "http://localhost:3000/api/banking/ussd/start" \
  -H "Content-Type: application/json" \
  -d '{"code": "*737#", "phoneNumber": "+2348031234567"}'
```

#### Step 2: Select Balance Check
```bash
curl -X POST "http://localhost:3000/api/banking/ussd/USS_1703123456789_GTB_ABC123" \
  -H "Content-Type: application/json" \
  -d '{"input": "1"}'
```

#### Step 3: Enter Account Number
```bash
curl -X POST "http://localhost:3000/api/banking/ussd/USS_1703123456789_GTB_ABC123" \
  -H "Content-Type: application/json" \
  -d '{"input": "1234567890"}'
```

#### Final Response:
```json
{
  "success": true,
  "data": {
    "sessionId": "USS_1703123456789_GTB_ABC123",
    "message": "Your account balance is NGN 45,250.00\n\nLast transaction: NGN 5,000.00\nDate: 21/12/2023\n\nThank you for banking with GTBank!",
    "isFinal": true
  }
}
```

---

## 📱 Advanced Telecom System

AfriHub features a comprehensive telecom system with **15+ African telecom providers** across 6 countries, advanced USSD session management, and mobile money integration.

### Telco System Features:
- **15+ African Telecom Providers**: Coverage across Nigeria, Kenya, South Africa, Ghana, Tanzania, and Uganda
- **Advanced USSD Session Management**: Interactive USSD flows with state management and analytics
- **Mobile Money Integration**: Complete mobile money services simulation for supported providers
- **Provider Identification**: Automatic provider detection by phone number prefix
- **Session Analytics**: Comprehensive tracking of menu navigations and service usage
- **Multi-Country Support**: Realistic USSD flows for different African markets
- **Structured Response Format**: Clean JSON responses with actionable options

### Telco API Endpoints:

#### 1. List All Telecom Providers
```bash
curl "http://localhost:3000/api/telco/providers"
```

#### 2. Get Providers by Country
```bash
curl "http://localhost:3000/api/telco/providers/country/NG"
```

#### 3. Get Provider Information
```bash
curl "http://localhost:3000/api/telco/providers/mtn-ng"
```

#### 4. Identify Provider by Phone Number
```bash
curl -X POST "http://localhost:3000/api/telco/identify" \
  -H "Content-Type: application/json" \
  -d '{"phoneNumber": "+2348031234567"}'
```

#### 5. Start USSD Session
```bash
curl -X POST "http://localhost:3000/api/telco/ussd" \
  -H "Content-Type: application/json" \
  -d '{
    "phoneNumber": "+2348031234567",
    "code": "*131#"
  }'
```

**Response:**
```json
{
  "success": true,
  "data": {
    "sessionId": "5ca27577-3574-45f2-8055-a48294413fdb",
    "message": "Welcome to MTN Nigeria. Please select an option:",
    "actions": [
      { "id": "1", "label": "Check Balance" },
      { "id": "2", "label": "Buy Airtime" },
      { "id": "3", "label": "Data Bundles" },
      { "id": "4", "label": "Mobile Money" },
      { "id": "5", "label": "Other Services" },
      { "id": "0", "label": "Exit" }
    ],
    "isFinal": false
  }
}
```

#### 6. Continue USSD Session
```bash
curl -X POST "http://localhost:3000/api/telco/ussd/{sessionId}" \
  -H "Content-Type: application/json" \
  -d '{"input": "1"}'
```

#### 7. Get Telco Statistics
```bash
curl "http://localhost:3000/api/telco/stats"
```

### Supported Telecom Providers:

#### 🇳🇬 Nigeria (4 providers):
- **MTN Nigeria**: `*131#`, `*144#`, `*461#`, `*606#`, `*123#`
- **Airtel Nigeria**: `*123#`, `*432#`, `*141#`
- **Glo Nigeria**: `*123#`, `*777#`, `*141#`
- **9mobile**: `*200#`, `*232#`, `*141#`

#### 🇰🇪 Kenya (3 providers):
- **Safaricom**: `*234#`, `*544#`, `*544*1#`, `*544*2#`, `*544*3#`
- **Airtel Kenya**: `*100#`, `*544#`, `*544*1#`
- **Telkom Kenya**: `*100#`, `*544#`, `*544*1#`

#### 🇿🇦 South Africa (2 providers):
- **Vodacom**: `*111#`, `*135#`, `*135*1#`, `*135*2#`
- **MTN South Africa**: `*123#`, `*135#`, `*135*1#`, `*135*2#`

#### 🇬🇭 Ghana (2 providers):
- **MTN Ghana**: `*138#`, `*170#`, `*170*1#`, `*170*2#`
- **Vodafone Ghana**: `*110#`, `*170#`, `*170*1#`

#### 🇹🇿 Tanzania (2 providers):
- **Vodacom Tanzania**: `*150#`, `*150*1#`, `*150*2#`
- **Airtel Tanzania**: `*150#`, `*150*1#`, `*150*2#`

#### 🇺🇬 Uganda (2 providers):
- **MTN Uganda**: `*165#`, `*165*1#`, `*165*2#`
- **Airtel Uganda**: `*165#`, `*165*1#`, `*165*2#`

### Complete Telco USSD Flow Example:

#### Step 1: Start USSD Session
```bash
curl -X POST "http://localhost:3000/api/telco/ussd" \
  -H "Content-Type: application/json" \
  -d '{"phoneNumber": "+2348031234567", "code": "*131#"}'
```

#### Step 2: Select Airtime Purchase
```bash
curl -X POST "http://localhost:3000/api/telco/ussd/5ca27577-3574-45f2-8055-a48294413fdb" \
  -H "Content-Type: application/json" \
  -d '{"input": "2"}'
```

#### Step 3: Choose Self or Others
```bash
curl -X POST "http://localhost:3000/api/telco/ussd/5ca27577-3574-45f2-8055-a48294413fdb" \
  -H "Content-Type: application/json" \
  -d '{"input": "1"}'
```

#### Step 4: Enter Amount
```bash
curl -X POST "http://localhost:3000/api/telco/ussd/5ca27577-3574-45f2-8055-a48294413fdb" \
  -H "Content-Type: application/json" \
  -d '{"input": "500"}'
```

#### Final Response:
```json
{
  "success": true,
  "data": {
    "sessionId": "5ca27577-3574-45f2-8055-a48294413fdb",
    "message": "✅ Airtime purchase successful!\n\nAmount: NGN 500\nRecipient: your number\nTransaction ID: ABC123DEF456",
    "isFinal": true
  }
}
```

### Telco System Features:
- **Advanced Session Management**: 5-minute session timeout with automatic cleanup
- **Mobile Money Integration**: Complete mobile money services for supported providers
- **Provider Analytics**: Track menu navigations, service usage, and session duration
- **Back Navigation**: Full back navigation support throughout USSD flows
- **Error Handling**: Comprehensive error messages with retry options
- **Realistic Responses**: Authentic USSD menu structures and service flows

## Development:

*   To build the TypeScript project:
    ```bash
    npm run build
    ```
*   To start the development server:
    ```bash
    npm start
    ``` 
