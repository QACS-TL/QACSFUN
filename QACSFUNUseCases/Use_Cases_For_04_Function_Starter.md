# Agile User Stories for Zoo Tycoon Animal Management System

## 04 Functions – Starter

------------------------------------------------------------------------

## User Story 6: Interactive Animal Addition

**As a** developer  
**I want to** refactor the code that adds new animals through console input by placing it in a function  
**So that** I can add additional animals to the collection without duplicating my code

### Acceptance Criteria:

- Code contains a new function called AddNewAnimal where:

  - System prompts user with clear format instructions

  - User can enter animal details as comma-separated values

  - Input follows format: Name,Type,Colour,LimbCount

  - Invalid/empty input is handled gracefully (not added to collection)

  - Newly added animal appears in subsequent collection printouts

### Technical Notes:

- AddNewAnimal takes List<Animal> as a parameter

- Appropriate code is moved from Main to AddNewAnimal

**Priority:** High  
**Story Points:** 3


------------------------------------------------------------------------

## User Story 7: Input Validation and Sanitization

**As a** system user  
**I want** my input to be trimmed and validated  
**So that** accidental whitespace doesn't corrupt animal data

### Acceptance Criteria:

- Leading and trailing whitespace is removed from input

- Null or empty strings are rejected

- Only valid entries are added to the collection

- No error messages are displayed for empty input (silent rejection)

### Technical Notes:

- Done in AddNewAnimal method

- Null or empty test done with:
    if (!string.IsNullOrEmpty(animal))

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 8: Reusable Collection Display

**As a** developer  
**I want** a reusable method to print animal details  
**So that** I can display the collection at multiple points in the
program flow

### Acceptance Criteria:

- PrintDetails method can be called multiple times

- Each call shows current state of the collection

- Output includes formatted header and animal count

- Method accepts List\<string\> parameter for flexibility

### Technical Notes:

- Move relevant code into new PrintDetails function

- PrintDetails Function takes animals collection as a parameter.

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 9: Enhanced Collection Creation

**As a** developer 
**I want** the code that creates the initial collection of animals to be relocated into a function called CreateAnimalCollection   
**So that** I keep it separate from the rest of my code

### Acceptance Criteria:

- Code contains a new function called CreateAnimalCollection where:

  - Collection includes animals with non-standard limb counts (3, 5 limbs)

  - Collection includes unusual colors (PURPLE, ORANGE)

  - Collection includes generic "Animal" type

  - System handles this variety without errors

  - Size of collection is written to the console

  - Function returns the collection

### Technical Notes:

- Function's content is moved from Main

**Priority:** Low  
**Story Points:** 1

------------------------------------------------------------------------

## User Story 10: Before-and-After Collection Comparison

**As a** zoo administrator  
**I want to** see the collection before and after adding animals  
**So that** I can verify my additions were successful

### Acceptance Criteria:

- Initial collection is displayed after creation

- Collection is displayed again after interactive addition

- Count increases reflect successful additions

- User can visually confirm the new animal appears in the list

### Technical Notes:

- Code in Main calls the appropriate functions to achieve requirement

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## Technical Notes

### Key Differences from Previous Version:

- Interactive input capability (AddNewAnimal method)

- Reusable display logic (PrintDetails method)

- Main method now orchestrates workflow

- Input validation with null-checking and trimming

- Multiple display points for verification

- More diverse test data
