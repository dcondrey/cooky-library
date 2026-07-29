# Cooky Recipe Library

Community recipe library for the [Cooky](https://github.com/dcondrey/cooky) iOS kitchen app.

## Format

`recipes.json` — a JSON array of `Recipe` objects. The schema matches the Swift `Recipe` model in the iOS app exactly, so recipes load without transformation.

### Required fields

| Field | Type | Notes |
|---|---|---|
| `id` | UUID string | Unique per recipe |
| `name` | string | |
| `description` | string | |
| `cuisine` | string | e.g. "Italian", "Mexican" |
| `difficulty` | "Easy" \| "Medium" \| "Hard" | |
| `estimatedMinutes` | Int | Total cook + prep time |
| `servings` | Int | |
| `tags` | [string] | e.g. ["Dinner", "Vegetarian"] |
| `imageQuery` | string | Used to fetch a representative image |
| `estimatedCostUSD` | Double | Per-recipe ingredient cost estimate |
| `ingredients` | [Ingredient] | See below |
| `steps` | [RecipeStep] | See below |
| `nutrition` | Nutrition | See below |
| `missingIngredients` | [string] | Leave `[]` in library recipes |

### Ingredient fields

`id`, `name`, `quantity` (Double), `unit`, `isOptional` (Bool), `substitutions` ([string]), `notes` (string?), `isDisabled` (Bool, default `false`)

### RecipeStep fields

`id`, `stepNumber` (Int), `instruction`, `timeMinutes` (Int?), `tip` (string?), `measurementAlternatives` ([string]), `imageQuery` (string?)

### Nutrition fields

`caloriesPerServing`, `proteinGrams`, `carbsGrams`, `fatGrams`, `fiberGrams` (all Double), `vitamins` ([string]), `minerals` ([string]), `antioxidants` ([string]), `isKeto`, `isVegetarian`, `isVegan`, `isGlutenFree`, `isKosher`, `isDairyFree`, `isAntiInflammatory` (all Bool), `healthScore` (Int, 1-10)

## Contributing

Open a PR with additional recipes in `recipes.json`. Keep `id` fields as valid UUIDs. All fields are required unless marked optional.
