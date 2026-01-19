# Agile User Stories for Zoo Tycoon Animal Management System

## 06b Loops and Collections Extended – Starter

### Structured Animal Data Model Refactored With CRUD Operations Version

------------------------------------------------------------------------

## User Story 31: Centralized Validation Logic

**As a** developer  
**I want** a single validation function for all attribute types  
**So that** validation rules are consistent and maintainable in one
location

### Acceptance Criteria:

- AttributeChecker method handles all attribute validation

- Switch statement routes validation by attribute name

- Returns boolean indicating validation failure (true = invalid)

- Supports: Name, Type, Colour, LimbCount validation

- Default case returns true for unknown attributes

**Priority:** High  
**Story Points:** 5

------------------------------------------------------------------------

## User Story 32: Reusable Input and Validation Flow

**As a** developer  
**I want** a generic method for getting and validating any attribute  
**So that** I can eliminate duplicate validation code

## Acceptance Criteria:

- GetAndValidateAttributeForAdding accepts attribute name parameter

- Prompts user with attribute-specific label

- Loops until valid input received

- Uses AttributeChecker for validation

- Returns validated string value

- Error messages include specific attribute name

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 33: Custom Numeric Validation Function

**As a** developer  
**I want** a dedicated IsNumeric helper function  
**So that** numeric validation is explicit and reusable

## Acceptance Criteria:

- IsNumeric checks if string contains only digits

- Returns false for null or empty strings (guard clause)

- Uses LINQ All() with char.IsNumber

- Handles Unicode numeric digits

- Used by LimbCount validation logic

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 34: Edit Existing Animals

**As a** zoo administrator  
**I want to** modify existing animal attributes  
**So that** I can correct mistakes or update animal information

### Acceptance Criteria:

- User selects animal by number from list

- Current values shown in square brackets for each field

- User can press Enter to keep existing value

- Only modified fields are updated

- Validation applies to new values only

- Confirmation message: "Saved changes."

**Priority:** High  
**Story Points:** 5

## User Story 35: Edit with Blank-to-Keep Pattern

**As a** zoo administrator  
**I want to** leave fields blank during editing to keep current values  
**So that** I only need to type values I want to change

### Acceptance Criteria:

- GetAndValidateAttributeWhileEditing displays current value

- Blank/empty input preserves existing value

- Non-blank input must pass validation

- Prompt format: "attribute \[current_value\]: "

- User can cancel individual field changes

**Priority:** Medium  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 36: Remove Animals from Collection

**As a** zoo administrator  
**I want to** delete animals from the collection  
**So that** I can remove animals no longer in the zoo

### Acceptance Criteria:

- User selects animal by number from list

- Selected animal is removed from collection

- Confirmation message shows removed animal's name

- Format: "Removed {Name}"

- Animal no longer appears in subsequent listings

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 37: Interactive Animal Feeding

**As a** zoo administrator  
**I want to** feed animals with type-appropriate food  
**So that** I can simulate animal care activities

### Acceptance Criteria:

- User selects animal by number to feed

- Food type determined by animal species:

  - CAT → fish

  - DOG → biscuits

  - BIRD → seeds

  - Others → sandwiches

- Message describes animal eating with its limbs

- Species-specific response after feeding

**Priority:** Medium  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 38: Species-Specific Feeding Responses

**As a** zoo administrator  
**I want** different feedback based on animal type when feeding  
**So that** the interaction feels realistic and engaging

### Acceptance Criteria:

- DOG: "It's wagging its tail happily!"

- CAT: "It purrs contentedly."

- BIRD: "It chirps sweetly."

- Others: "It seems satisfied."

- Message includes animal name, type, limb count, and food

- Case-insensitive type comparison

**Priority:** Low  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 39: Reusable Animal Selection Pattern

**As a** developer  
**I want** a centralized animal selection method  
**So that** Edit, Remove, and Feed operations share the same selection
logic

### Acceptance Criteria:

- AnimalSelector method accepts mode parameter (edit/remove/feed)

- Displays title-cased operation name

- Shows numbered list of animals

- Returns selected animal dictionary and quit flag

- Handles empty collections gracefully

- User can cancel selection by entering blank

**Priority:** High  
**Story Points:** 5

------------------------------------------------------------------------

## User Story 40: Indexed Animal Selection

**As a** zoo administrator  
**I want to** select animals by entering their list number  
**So that** I can quickly choose specific animals for operations

### Acceptance Criteria:

- ChooseIndex method accepts maximum valid number

- User can enter blank to cancel

- Validates numeric input

- Validates number is within range (1 to maxN)

- Returns zero-based index (nullable int)

- Returns null for invalid/cancelled selections

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 41: Cancellable Animal Selection

**As a** zoo administrator  
**I want to** cancel animal selection by leaving input blank  
**So that** I can back out of operations without making changes

### Acceptance Criteria:

- Blank input during selection shows "Cancelled."

- Operation aborts without modifications

- User returns to main menu

- Works for Edit, Remove, and Feed operations

- No error messages for intentional cancellation

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 42: Empty Collection Handling

**As a** zoo administrator  
**I want** helpful messages when no animals exist  
**So that** I understand why operations cannot proceed

### Acceptance Criteria:

- AnimalSelector detects null or empty collections

- Message format: "No animals to {operation}."

- Operation automatically aborted (quit flag set)

- User returned to menu without error

- Applies to Edit, Remove, and Feed operations

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 43: Expanded Menu Options

**As a** zoo administrator  
**I want** access to all CRUD operations plus feeding  
**So that** I have complete control over the animal collection

### Acceptance Criteria:

- Menu includes: List, Add, Edit, Remove, Feed, Exit

- Menu options numbered 1-6

- Each option routes to appropriate method

- Exit option updated to "6"

- All operations accessible from main menu

**Priority:** High  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 44: Title Case Operation Labelling

**As a** zoo administrator  
**I want** operation names displayed in proper title case  
**So that** the interface appears professional

### Acceptance Criteria:

- CultureInfo.CurrentCulture.TextInfo.ToTitleCase used

- "edit" becomes "Edit animals"

- "remove" becomes "Remove animals"

- "feed" becomes "Feed animals"

- Culture-aware capitalization

**Priority:** Low  
**Story Points:** 1

------------------------------------------------------------------------

## User Story 45: Switch Expression for Food Assignment

**As a** developer  
**I want** to use modern C# switch expressions for food type mapping  
**So that** code is concise and readable

### Acceptance Criteria:

- Switch expression maps Type to food string

- Pattern: ani\["Type"\].ToUpperInvariant() switch { ... }

- Returns appropriate food for each species

- Default case handles unknown types

- Single expression assignment (no intermediate variables)

**Priority:** Low  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 46: Tuple Return Pattern for Complex Results

**As a** developer  
**I want** AnimalSelector to return tuple with animal and quit status  
**So that** callers receive both selection result and cancellation state

### Acceptance Criteria:

- Return type: (Dictionary\<string, string\>? selected, bool Quit)

- Named tuple elements for clarity

- Nullable animal dictionary for no selection

- Boolean indicates operation should quit

- Destructuring syntax supported: var (ani, qf) = ...

**Priority:** Medium  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 47: Prepared for Persistence Layer

**As a** developer  
**I want** commented SaveAnimals calls in Edit and Remove  
**So that** persistence can be added without refactoring

### Acceptance Criteria:

- //SaveAnimals(animals); present after Edit

- //SaveAnimals(animals); present after Remove

- Comments indicate future functionality

- Code structure supports easy activation

- No actual file I/O implemented yet

**Priority:** Low  
**Story Points:** 1

------------------------------------------------------------------------

## Technical Notes

### Key Architectural Improvements:

- DRY principle: centralized validation via AttributeChecker

- Reusable patterns: GetAndValidateAttribute methods

- Tuple returns for complex method results

- Switch expressions for concise mapping logic

- Nullable return types for optional values

- Culture-aware string manipulation

### CRUD Completeness:

- **Create**: AddAnimal (existing, now refactored)

- **Read**: ListAnimals (existing)

- **Update**: EditAnimal (NEW)

- **Delete**: RemoveAnimal (NEW)

- **Bonus**: FeedAnimal interaction (NEW)

### Code Quality Enhancements:

- Eliminated duplicate validation code (80+ lines → reusable methods)

- Consistent user experience across operations

- Guard clauses for null/empty checks

- Meaningful variable names and error messages

- Modern C# features (switch expressions, tuples, nullable types)

### User Experience Improvements:

- Cancellable operations at selection stage

- Current values shown during editing

- Clear confirmation messages

- Species-appropriate interactive responses

- Professional title-cased labels

- Helpful messages for edge cases (empty collections)
