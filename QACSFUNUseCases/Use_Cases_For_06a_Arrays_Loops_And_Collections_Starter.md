# Agile User Stories for Zoo Tycoon Animal Management System

## 06a Arrays, Loops and Collections – Starter

### Structured Animal Data Model Enhanced Version

------------------------------------------------------------------------

## User Story 19: Structured Animal Data Model

**As a** developer  
**I want** animals stored as dictionaries with named properties  
**So that** I can access animal attributes by key rather than parsing
CSV strings

### Acceptance Criteria:

- Each animal is a Dictionary\<string, string\> with keys: Name, Type,
  Colour, LimbCount

- Animals collection is List\<Dictionary\<string, string\>\>

- All animal data uses key-value access pattern

- No CSV parsing required to retrieve individual attributes

- Data structure supports easy attribute lookup

**Priority:** High  
**Story Points:** 5

------------------------------------------------------------------------

## User Story 20: Field-by-Field Animal Input

**As a** zoo administrator  
**I want to** enter each animal attribute separately with individual
prompts  
**So that** the input process is clearer and less error-prone

### Acceptance Criteria:

- Separate prompts for: Name, Type, Colour, Limb Count

- Each field prompts independently (no single CSV input line)

- User sees clear label for each field being entered

- Fields are entered in logical order

- Each field can be validated independently

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 21: Name Validation with Minimum Length

**As a** zoo administrator  
**I want** animal names to have at least 2 characters  
**So that** all animals have meaningful, identifiable names

### Acceptance Criteria:

- Names with fewer than 2 characters are rejected

- User sees "Invalid name, please try again." error message

- User is re-prompted until valid name is entered

- Validation loop prevents empty or single-character names

- Whitespace is trimmed before validation

**Priority:** Medium  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 22: Species Type Validation with Allowed List

**As a** zoo administrator  
**I want** animal types restricted to predefined valid species  
**So that** data remains consistent and prevents typos

### Acceptance Criteria:

- Only accepts: CAT, DOG, BIRD, APE, UNKNOWN

- Input is case-insensitive (converted to uppercase)

- Invalid types show "Invalid Type, please try again."

- User is re-prompted until valid type is entered

- Validation uses HashSet for efficient lookup

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 23: Colour Validation with Allowed Palette

**As a** zoo administrator  
**I want** animal colours restricted to predefined valid options  
**So that** colour data is standardized across the system

### Acceptance Criteria:

- Only accepts: BROWN, BLACK, WHITE, ORANGE, PURPLE, PINK

- Input is case-insensitive (converted to uppercase)

- Invalid colours show "Invalid colour, please try again."

- User is re-prompted until valid colour is entered

- Validation uses HashSet for efficient lookup

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 24: Numeric Limb Count Validation

**As a** zoo administrator  
**I want** limb count to accept only non-negative integers  
**So that** limb data is numerically valid and realistic

### Acceptance Criteria:

- Only numeric integer values are accepted

- Negative numbers are rejected

- Non-numeric input (letters, symbols) is rejected

- Error message: "Invalid limb count, please try again."

- Uses int.TryParse for safe type conversion

- User is re-prompted until valid number is entered

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 25: Validation Loop Pattern

**As a** developer  
**I want** consistent validation loops for all input fields  
**So that** invalid data never enters the system

### Acceptance Criteria:

- Each field has while loop for validation

- Loops continue until valid input is provided

- Clear error messages for each validation type

- User cannot bypass validation

- Application never crashes from invalid input

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 26: Formatted Animal Display List

**As a** zoo administrator  
**I want** animals displayed in numbered, structured format  
**So that** I can easily read and reference each animal's details

### Acceptance Criteria:

- Each animal displayed on separate line

- Numbered list (1, 2, 3...) based on position

- Format: "N) Name: X, Colour: Y, LimbCount: Z, Type: W"

- All attributes clearly labeled

- Uses dictionary key access for attribute retrieval

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 27: Case-Insensitive Input Normalization

**As a** zoo administrator  
**I want** Type and Colour inputs to accept any case  
**So that** I don't have to remember exact capitalization

### Acceptance Criteria:

- "dog", "DOG", "Dog" all accepted for Type

- "black", "BLACK", "Black" all accepted for Colour

- Input automatically converted to uppercase

- Stored values are consistently uppercase

- Case normalization happens before validation

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 28: HashSet-Based Validation Rules

**As a** developer  
**I want** validation rules defined as HashSet collections  
**So that** allowed values are easy to maintain and lookup is efficient

### Acceptance Criteria:

- allowedSpecies defined as static HashSet

- allowedColours defined as static HashSet

- HashSets initialized with collection initializer syntax

- Validation uses Contains() method for O(1) lookup

- Easy to add/remove allowed values by editing HashSet

**Priority:** Low  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 29: Safe Type Conversion for Numeric Input

**As a** developer  
**I want** to use TryParse for numeric conversions  
**So that** invalid numeric input doesn't crash the application

### Acceptance Criteria:

- int.TryParse used for limb count input

- Method returns bool indicating success/failure

- Out parameter receives parsed value

- No exceptions thrown for invalid input

- Validation checks both parse success and value range

**Priority:** High  
**Story Points:** 2

## User Story 30: Data Integrity Through Validation

**As a** zoo administrator  
**I want** all animal data validated before being stored  
**So that** the collection contains only clean, consistent data

### Acceptance Criteria:

- No animal added without passing all validations

- All stored names have 2+ characters

- All stored types are from allowed list

- All stored colours are from allowed list

- All stored limb counts are non-negative integers

- Dictionary structure ensures all required fields present

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## Technical Notes

### Key Architectural Changes:

- Migration from CSV strings to structured dictionaries

- Implementation of comprehensive input validation

- Field-level validation with retry loops

- Type safety with numeric parsing

- Centralized validation rules in HashSets

- Elimination of malformed data risk

### Data Quality Improvements:

- Enforced data consistency

- Type safety for numeric fields

- Case normalization for categorical fields

- Length validation for names

- Whitelist-based validation for enums

- No possibility of CSV parsing errors

### User Experience Enhancements:

- Step-by-step guided input process

- Clear, specific error messages

- Immediate validation feedback

- Persistent re-prompting until valid

- Case-insensitive input acceptance

- Professional numbered list display
