<!-- repo-header:start -->
<h3 align="center">Cooky Recipe Library</h3>

<p align="center"><strong>Shared recipe library for the Cooky iOS app: a single <code>recipes.json</code> whose schema matches the app's Swift model exactly.</strong></p>

<p align="center">
  <a href=".bestpractices.json"><img src="https://img.shields.io/badge/best%20practices-evidence%20reviewed-6a4c93?style=flat-square&labelColor=20232a" alt="Best Practices Evidence"></a>
  <a href="https://github.com/sponsors/dcondrey"><img src="https://img.shields.io/badge/GitHub%20Sponsors-Sponsor-EA4AAA?style=flat-square&labelColor=20232a" alt="GitHub Sponsors"></a>
</p>
<!-- repo-header:end -->

---

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
