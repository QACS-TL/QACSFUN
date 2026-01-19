# Agile User Stories for Zoo Tycoon Animal Management System

## 03 Variables - Starter

### Epic: Animal Collection Management

As a zoo manager, I want to manage a collection of animals so that I can
track the animals in my zoo.

------------------------------------------------------------------------

## User Story 1: Initialize Animal Collection

**As a** developer  
**I want to** create a list to store animal data  
**So that** I can maintain a collection of animals in the system

### Acceptance Criteria:

- A List\<string\> collection is initialized to store animal records

- The collection can accept string values in CSV format

- An integer counter variable is initialized to track manual count

### Technical Notes:

- Use List\<string\> for the animal collection

- Initialize counter at 0

- Each animal stored as: "Name,Type,Colour,LimbCount"

------------------------------------------------------------------------

## User Story 2: Pre-populate Animal Data

**As a** zoo manager  
**I want to** have sample animals in the system at startup  
**So that** I can see example data and test the system

## Acceptance Criteria:

- Four animals are added to the collection on initialization:

  - Fido (Dog, Black, 4 limbs)

  - Fifi (Cat, White, 5 limbs)

  - Oscar (Bird, Orange, 3 limbs)

  - Boris (Animal, Purple, 3 limbs)

- Each animal addition increments the manual counter

- Animal data follows CSV format: Name,Type,Colour,LimbCount

------------------------------------------------------------------------

### User Story 3: Display Animal Collection

**As a** zoo manager  
**I want to** view the current list of animals  
**So that** I can see what animals are in my zoo

## Acceptance Criteria:

- Animals are displayed in two formats:

  1.  One animal per line with comma separation

  2.  All animals in a single bracketed line

- Both the manual count and collection count are displayed

- Output clearly shows total number of animals

## Technical Notes:

- Use string.Join(",\n", animals) for multi-line display

- Use "\[" + string.Join(", ", animals) + "\]" for single-line display

- Display both count variable and animals.Count property

------------------------------------------------------------------------

### User Story 4: Add New Animal Interactively

**As a** zoo manager  
**I want to** add a new animal through console input  
**So that** I can expand my animal collection

## Acceptance Criteria:

- System prompts user with clear instruction: "Enter Animal Details (in
  form '{Name},{Type},{Colour},{LimbCount}'"

- User can input animal data in CSV format

- Input is trimmed of whitespace

- Non-empty input is added to the collection

- Manual counter is incremented after successful addition

- Null or empty input is handled gracefully (not added)

## Technical Notes:

- Use Console.ReadLine()?.Trim() to capture input

- Validate input is not null or empty before adding

- Use null-conditional operator for safe string handling

------------------------------------------------------------------------

### User Story 5: Display Updated Animal Collection

**As a** zoo manager  
**I want to** see the updated animal list after adding a new animal  
**So that** I can confirm my addition was successful

## Acceptance Criteria:

- After adding new animal, display updated collection in bracketed
  format

- Show both manual count and collection count

- Counts should reflect the newly added animal

## Technical Notes:

- Reuse display logic from User Story 3

- Ensure both counters are synchronized

------------------------------------------------------------------------

### Non-Functional Requirements

**Data Format**

- Animal data must follow CSV structure: Name,Type,Colour,LimbCount

- All fields are strings (including LimbCount)

**Error Handling**

- Handle null input from Console.ReadLine()

- Handle empty or whitespace-only input

- Use null-conditional operators where appropriate

**Code Quality**

- Follow naming conventions (PascalCase for public members)

- Use string interpolation for output messages
