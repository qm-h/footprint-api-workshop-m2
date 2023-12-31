# api-workshop-m2

API dédié au projet workshop du M2

# Installation

## Dépendances

```bash
$ pnpm install
```

## Prérequis

- Node.js
- pnpm

# Utilisation

## Lancement

```bash
$ pnpm start:dev
```

## Tests

```bash
$ pnpm test
```

# Documentation

## API

## FootPrint

### GET /api/footprint/getfootprintcartravel

#### Paramètres

| distance | vehicule

#### Réponse

```json
{
  "footprint": "number"
}
```

### GET /api/footprint/getfootprintpublictransport

#### Paramètres

| distance | publicTansitType

#### Réponse

```json
{
  "footprint": "number"
}
```

### GET /api/footprint/getfootprintflight

#### Paramètres

| distance | flightType

#### Réponse

```json
{
  "footprint": "number"
}
```

### POST /api/footprint/createfootprintcartravel

#### Paramètres

| userId | categoryName | emissionCo2 | description | nameActivity | tauxEmission | distanceParcourue

#### Réponse

```json
{
  "footPrint": {
    "id_carbon": 1,
    "id_activity": 1,
    "taux_emission": 0.2
  },
  "categoryActivity": {
    "id_category": 1,
    "name_category": "Car travel",
    "id_activity": null
  },
  "activity": {
    "id_activity": 1,
    "name_activity": "Car travel Activity",
    "emission_co2": 0.2,
    "description": "Car travel Description",
    "id_category": 1
  },
  "activityLog": {
    "id_log": 1,
    "id_user": "1",
    "id_activity": 1,
    "date": "2023-10-26T00:00:00.000Z",
    "distance_parcourue": 100,
    "duree_active": "1970-01-01T09:09:33.992Z",
    "id_recommendation": null,
    "id_carbon": 1
  }
}
```

### GET /api/footprint/findFootPrintByUser/:id

#### Paramètres

| id

### Réponse

### On retourne un tableau d'empreinte carbone

```json
[
  {
    "footPrint": {
      "id_carbon": 1,
      "id_activity": 1,
      "taux_emission": 0.2
    },
    "categoryActivity": {
      "id_category": 1,
      "name_category": "Car travel",
      "id_activity": null
    },
    "activity": {
      "id_activity": 1,
      "name_activity": "Car travel Activity",
      "emission_co2": 0.2,
      "description": "Car travel Description",
      "id_category": 1
    },
    "activityLog": {
      "id_log": 1,
      "id_user": "1",
      "id_activity": 1,
      "date": "2023-10-26T00:00:00.000Z",
      "distance_parcourue": 100,
      "duree_active": "1970-01-01T09:09:33.992Z",
      "id_recommendation": null,
      "id_carbon": 1
    }
  },
  {
    "footPrint": {
      "id_carbon": 2,
      "id_activity": 2,
      "taux_emission": 0.5
    },
    "categoryActivity": {
      "id_category": 3,
      "name_category": "Random category",
      "id_activity": null
    },
    "activity": {
      "id_activity": 2,
      "name_activity": "activity name",
      "emission_co2": 0.4,
      "description": "Description Random",
      "id_category": 3
    },
    "activityLog": {
      "id_log": 2,
      "id_user": "1",
      "id_activity": 2,
      "date": "2023-10-26T00:00:00.000Z",
      "distance_parcourue": 200,
      "duree_active": "1970-01-01T09:40:32.182Z",
      "id_recommendation": null,
      "id_carbon": 2
    }
  }
]
```

## FoodPrint

### GET /api/foodprint/getfoodprint

#### Paramètres

| frenchName

#### Réponse

```json
{
  "group": "string",
  "category": "string",
  "french_name": "string",
  "name": "string",
  "rating_quality": "string",
  "footprint": "string"
}
```

### GET /api/foodprint/getfoodprintbycategory

#### Paramètres

| category

#### Réponse

```json
{
  "group": "string",
  "category": "string",
  "french_name": "string",
  "name": "string",
  "rating_quality": "string",
  "footprint": "string"
}
```

### GET /api/foodprint/getCategories

#### Paramètres

| none

#### Réponse

```json
{
  "categories": [
    "string"
  ]
}
```

## Open AI

### POST /api/openAI/chatgptHelper

#### Paramètres Body

| Message | Model | Max_Tokens

#### Réponse

```json
{
  "chatGPTId": "string",
  "chatGPTMessage": "string",
  "chatGPTFinishReason": "string",
  "chatGPTUsage": {
    "prompt_tokens": "number",
    "completion_tokens": "number",
    "total_tokens": "number"
  }
}
```

## User

### POST /api/user/createUser

#### Paramètres

| password | mail

#### Réponse

```json
{
  "user": {
    "id": "string",
    "mail": "string",
    "password": "string"
  }
}
```

### POST /api/user/login

#### Paramètres

| password | mail

#### Réponse

```json
{
  "user": {
    "id": "string",
    "mail": "string",
  }
}
```

### GET /api/user/findUserById/:id

#### Paramètres

| id

#### Réponse

```json
{
  "user": {
    "id": "string",
    "mail": "string",
    "password": "string"
  }
}
```

### Using Model

The model used is the GPT-3-turbo model, but it is possible to change it using the "model" parameter in the request.

### Using Max_Tokens

The max_tokens parameter is used to limit the number of tokens generated by the model. The default value is 300.



# Documentation Typages

## Types FootPrint

```typescript 
export enum FootPrintCategory {
  CARBON_FOOTPRINT_FROM_CAR_TRAVEL = 'CarbonFootprintFromCarTravel',
  CARBON_FOOTPRINT_FROM_FLIGHT = 'CarbonFootprintFromFlight',
  CARBON_FOOTPRINT_FROM_PUBLIC_TRANSIT = 'CarbonFootprintFromPublicTransit',
  CARBON_FOOTPRINT_FROM_MOTOR_BIKE = 'CarbonFootprintFromMotorBike',
  FUEL_TO_CO2E = 'FuelToCO2e',
  CLEAN_HYDRO_TO_CARBON_FOOTPRINT = 'CleanHydroToCarbonFootprint',
  TRADITIONAL_HYDRO_TO_CARBON_FOOTPRINT = 'TraditionalHydroToCarbonFootprint',
  AIR_QUALITY_HEALTH_INDEX = 'AirQualityHealthIndex',
}

export interface FootPrintCarTravelParams {
  distance: string // in km
  vehicle: FootPrintCarTravelVehicleType
}

export interface FootPrintGenericParams {
  distance: string // in km
  type: FootPrintFlightType | FootPrintPublicTransitType
}

export type FootPrintParams = FootPrintCarTravelParams | FootPrintGenericParams

export enum FootPrintFlightType {
  DOMESTIC_FLIGHT = 'DomesticFlight',
  SHORT_ECONOMY_CLASS_FLIGHT = 'ShortEconomyClassFlight',
  SHORT_BUSINESS_CLASS_FLIGHT = 'ShortBusinessClassFlight',
  LONG_ECONOMY_CLASS_FLIGHT = 'LongEconomyClassFlight',
  LONG_PREMIUM_CLASS_FLIGHT = 'LongPremiumClassFlight',
  LONG_BUSINESS_CLASS_FLIGHT = 'LongBusinessClassFlight',
  LONG_FIRST_CLASS_FLIGHT = 'LongFirstClassFlight',
}

export enum FootPrintCarTravelVehicleType {
  SMALL_DIESEL_CAR = 'SmallDieselCar',
  MEDIUM_DIESEL_CAR = 'MediumDieselCar',
  LARGE_DIESEL_CAR = 'LargeDieselCar',
  SMALL_PETROL_CAR = 'SmallPetrolCar',
  MEDIUM_PETROL_CAR = 'MediumPetrolCar',
  LARGE_PETROL_CAR = 'LargePetrolCar',
  SMALL_PLUGIN_HYBRID_CAR = 'SmallPluginHybridCar',
  MEDIUM_PLUGIN_HYBRID_CAR = 'MediumPluginHybridCar',
  LARGE_PLUGIN_HYBRID_CAR = 'LargePluginHybridCar',
}

export enum FootPrintPublicTransitType {
  TAXI = 'Taxi',
  BUS = 'Bus',
  TRAIN = 'Train',
  SUBWAY = 'Subway',
}

```

## Types FoodPrint

```typescript
export enum FoodPrintEndpoints {
  FRENCH_NAME = 'frenchname',
  CATEGORY = 'category',
  GET_CATEGORIES = 'getCategories'
}

export interface FoodPrintParams {
  frenchName?: string
  category?: string
}

export interface FoodPrintApiResponse {
  group: string
  category: string
  french_name: string
  name: string
  rating_quality: string
  footprint: string
}

export interface FoodPrintCategory {
  category: string[]
}

```

## Types OpenAI

```typescript
export interface Choice {
  index: number
  message: {
    role: string
    content: string | null
  }
  finish_reason: string
}

export interface Usage {
  prompt_tokens: number
  completion_tokens: number
  total_tokens: number
}

export interface ChatCompletionResponse {
  id: string
  object: string
  created: number
  model: string
  choices: Choice[]
  usage?: Usage
}

export interface ChatGPTData {
  chatGPTId: string
  chatGPTMessage: string | null
  chatGPTFinishReason: string
  chatGPTUsage?: Usage
}

```


## Types Prisma 

```typescript
// Model Activity
export interface Activity {
  id_activity: number
  name_activity: string
  emission_co2: number
  description: string | null
  id_category: number | null
  category_activity?: CategoryActivity
  activitylog: ActivityLog[]
  carbon_emissions: CarbonEmission[]
}

// Model ActivityLog
export interface ActivityLog {
  id_log: number
  id_user: number | null
  id_activity: number | null
  date: Date
  distance_parcourue: number | null
  duree_active: Date | null
  id_recommendation: number | null
  id_carbon: number | null
  activity: Activity | null
  carbon_emissions: CarbonEmission | null
  recommendations: Recommendation | null
  user: User | null
}

// Model CarbonEmission
export interface CarbonEmission {
  id_carbon: number
  id_activity: number | null
  taux_emission: number | null
  activitylog: ActivityLog[]
  activity: Activity | null
}

// Model CategoryActivity
export interface CategoryActivity {
  id_category: number
  name_category: string
  id_activity: number | null
  activity: Activity[]
  activity_category_activity_id_activityToactivity: Activity | null
}

// Model Recommendation
export interface Recommendation {
  id_recommendation: number
  description: string | null
  id_log: number | null
  activitylog_activitylog_id_recommendationTorecommendations: ActivityLog[]
  activitylog_recommendations_id_logToactivitylog: ActivityLog | null
}

// Model User
export interface User {
  id_user: number
  password: string
  mail: string
  activitylog: ActivityLog[]
}

export type CarbonEmissionsPrisma = Omit<CarbonEmission, 'activity' | 'activitylog'>
export type ActivityPrisma = Omit<Activity, 'carbon_emissions' | 'activitylog' | 'category_activity'>
export type ActivityLogPrisma = Omit<ActivityLog, 'activity' | 'carbon_emissions' | 'recommendations' | 'user'>
export type CategoryActivityPrisma = Omit<CategoryActivity, 'activity' | 'activity_category_activity_id_activityToactivity'>
export type RecommendationPrisma = Omit<Recommendation, 'activitylog_activitylog_id_recommendationTorecommendations' | 'activitylog_recommendations_id_logToactivitylog'>
export type UserPrisma = Omit<User, 'activitylog'>

export interface FootPrintPrisma {
  footPrint: CarbonEmissionsPrisma
  categoryActivity: CategoryActivityPrisma
  activity: ActivityPrisma
  activityLog: ActivityLogPrisma
}

```
