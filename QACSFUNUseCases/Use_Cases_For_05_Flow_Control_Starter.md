# Agile User Stories for Zoo Tycoon Animal Management System

## 05 Flow Control – Starter

### Menu Driven Enhanced Version

------------------------------------------------------------------------

## User Story 11: Interactive Menu System

**As a** zoo administrator
**I want a** menu-driven interface with multiple options
**So that** I can perform different operations without restarting the
application

### Acceptance Criteria:

- Menu displays with clear numbered options

- Menu includes: List animals, Add animal, Exit

- Menu re-displays after each operation completes

- Menu remains active until user chooses to exit

- Menu has clear title "Animals App - Menu"

**Priority:** High  
**Story Points:** 5

------------------------------------------------------------------------

## User Story 12: Persistent Application Session

**As a** zoo administrator  
**I want** the application to stay running until I choose to exit  
**So that** I can perform multiple operations in one session

### Acceptance Criteria:

- Application runs in continuous loop

- Each operation returns user to main menu

- Only "Exit" option terminates the application

- All previous additions persist within the session

- User can list animals multiple times to see cumulative changes

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 13: Menu-Based Navigation

**As a** zoo administrator  
**I want to** select operations by entering numbers  
**So that** I have a simple and intuitive interface

### Acceptance Criteria:

- User enters "1" to list animals

- User enters "2" to add an animal

- User enters "3" to exit application

- Invalid entries show "Unknown option. Please try again."

- Invalid entries return user to menu without crashing

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 14: Reusable Input Helper Function

**As a** developer  
**I want** a centralized input method with consistent prompting  
**So that** all user inputs follow the same pattern and validation

### Acceptance Criteria:

- InputDetail method accepts custom prompt text

- Method displays prompt with colon separator

- Method trims whitespace from input

- Method returns empty string for null input (safe default)

- Method is reused throughout application

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 15: Graceful Application Exit

**As a** zoo administrator  
**I want** a clear exit option with confirmation message  
**So that** I know my session is ending intentionally

### Acceptance Criteria:

- Selecting "3" exits the application

- Exit displays "Goodbye — saving and exiting." message

- Application terminates cleanly (no errors)

- Message suggests data persistence (even if not yet implemented)

- Control returns to operating system

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 16: Invalid Input Handling with Recovery

**As a** zoo administrator  
**I want** helpful error messages when I enter invalid menu choices  
**So that** I understand what went wrong and can try again

### Acceptance Criteria:

- Any non-1/2/3 input triggers error message

- Error message reads "Unknown option. Please try again."

- Application continues running after error

- User is returned to menu for another attempt

- No application crash or unexpected termination

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 17: Simplified Method Naming Convention

**As a** developer  
**I want** concise, action-oriented method names  
**So that** code is more readable and maintainable

### Acceptance Criteria:

- CreateAnimalCollection renamed to LoadAnimals

- PrintDetails renamed to ListAnimals

- AddNewAnimal renamed to AddAnimal

- All methods follow verb-noun naming pattern

- Method names clearly indicate their purpose

**Priority:** Low  
**Story Points:** 1

------------------------------------------------------------------------

## User Story 18: Separation of Concerns - Menu Logic

**As a** developer  
**I want** menu logic separated from application entry point  
**So that** the code is better organized and testable

### Acceptance Criteria:

- MainMenu method contains all menu loop logic

- Main method only calls MainMenu

- Each menu option maps to a dedicated method

- Business logic separated from UI flow control

- Switch statement handles menu routing cleanly

**Priority:** Medium  
**Story Points:** 3

------------------------------------------------------------------------

## Technical Notes

### Key Architectural Improvements:

- Event-driven menu loop architecture

- Separation of UI flow (MainMenu) from entry point (Main)

- Centralized input handling with InputDetail

- Stateful session management (animals list persists in loop)

- Graceful error recovery for invalid inputs

- Improved method naming clarity

- Removal of debugging count variable (cleaner code)

### User Experience Enhancements:

- Non-linear workflow (user chooses operations)

- Multiple operations per session

- Immediate feedback for all actions

- Clear navigation paths

- Professional exit messaging
