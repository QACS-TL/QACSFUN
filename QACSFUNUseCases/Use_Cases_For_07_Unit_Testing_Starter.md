# Agile User Stories for Zoo Tycoon Animal Management System

## 07 Unit Testing – Starter

### Unit Testing Version

------------------------------------------------------------------------

## User Story 48: Unit Test Project Integration

**As a** developer  
**I want** a separate xUnit test project for the zoo application  
**So that** I can verify code correctness through automated testing

### Acceptance Criteria:

- Separate test project named "ZooTycoonTests"

- xUnit testing framework integrated

- Test project references main CSharpZooTycoon project

- Tests can access public methods from Program class

- Test namespace follows convention: namespace ZooTycoonTests

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 49: LoadAnimals Method Test Coverage

**As a** developer  
**I want** comprehensive tests for LoadAnimals functionality  
**So that** I can verify initial animal data is loaded correctly

### Acceptance Criteria:

- Test verifies collection contains exactly 4 animals

- Test validates first animal (Fido) attributes:

  - Name: "Fido"

  - Type: "DOG"

  - Colour: "BLACK"

  - LimbCount: 4

- Test validates second animal (Fifi) attributes:

  - Name: "Fifi"

  - Type: "CAT"

  - Colour: "WHITE"

  - LimbCount: 5

- Uses Arrange-Act-Assert pattern

- Parses LimbCount string to int for numerical assertion

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 50: IsNumeric Helper Method Test Coverage

**As a** developer  
**I want** comprehensive tests for numeric validation logic  
**So that** I can ensure numeric strings are correctly identified

### Acceptance Criteria:

- Test with valid numeric string "12345" returns true

- Test with alphanumeric string "12a45" returns false

- Test with empty string "" returns false

- Test with null string returns false

- All edge cases covered for guard clause validation

- Uses Arrange-Act-Assert pattern

**Priority:** High  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 51: Console Input/Output Redirection for Testing

**As a** developer  
**I want** to redirect console I/O during tests  
**So that** I can test interactive console methods programmatically

### Acceptance Criteria:

- Uses StringReader to simulate user input

- Uses StringWriter to capture console output

- Console.SetIn() redirects standard input

- Console.SetOut() redirects standard output

- Tests can verify prompts and responses

- Pattern reusable across multiple tests

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 52: Valid Input Validation Test

**As a** developer  
**I want** to test GetAndValidateAttributeForAdding with valid input  
**So that** I can verify correct values pass validation on first attempt

### Acceptance Criteria:

- TestGetAndValidateAttributeForAddingWithValidName:

  - Simulates input "Bob\n"

  - Verifies returned value is "Bob"

- TestGetAndValidateAttributeForAddingWithValidType:

  - Simulates input "Dog\n"

  - Verifies returned value is "Dog"

- No validation loops triggered

- Uses Arrange-Act-Assert pattern

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 53: Invalid-Then-Valid Input Validation Test

**As a** developer  
**I want** to test validation retry logic with sequential inputs  
**So that** I can verify the validation loop works correctly

### Acceptance Criteria:

- Test simulates invalid input "Bear" followed by valid "Bird"

- Input string: "Bear\nBird\n"

- Method loops once for invalid "Bear"

- Method accepts and returns "Bird"

- Verifies retry mechanism works as expected

- Uses Arrange-Act-Assert pattern

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 54: Theory-Based Parameterized Testing

**As a** developer  
**I want** to use xUnit Theory tests with InlineData  
**So that** I can test multiple input scenarios with a single test
method

### Acceptance Criteria:

- \[Theory\] attribute enables parameterized testing

- \[InlineData\] provides test case parameters

- Test cases include:

  - "Dog" → expects "Dog" (valid on first try)

  - "Dragon\nGoat\nBird" → expects "Bird" (multiple retries)

- Commented-out test cases preserved for future expansion

- Reduces code duplication across similar test scenarios

**Priority:** Medium  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 55: Validation Logic Edge Case Testing

**As a** developer  
**I want** tests that verify validation with multiple invalid attempts  
**So that** I can ensure validation persists until valid input received

### Acceptance Criteria:

- Test handles multi-line input: "Dragon\nGoat\nBird"

- Simulates two invalid attempts before valid input

- Verifies method continues looping through invalid inputs

- Only accepts input when validation passes

- Validates against allowedSpecies HashSet

- Tests real-world user error scenarios

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 56: Arrange-Act-Assert Test Pattern

**As a** developer  
**I want** all tests to follow AAA pattern  
**So that** tests are consistent, readable, and maintainable

### Acceptance Criteria:

- **Arrange** section: Set up test data, mock inputs, configure state

- **Act** section: Execute the method under test

- **Assert** section: Verify expected outcomes

- Comments mark each section clearly

- Pattern applied consistently across all tests

- Improves test readability and debugging

**Priority:** Low  
**Story Points:** 1

------------------------------------------------------------------------

## User Story 57: Test Isolation with Console Redirection

**As a** developer  
**I want** each test to have isolated console I/O  
**So that** tests don't interfere with each other or pollute output

### Acceptance Criteria:

- Each test creates new StringReader instance

- Each test creates new StringWriter instance

- Console redirection scoped to individual test

- No shared state between tests

- Tests can run in parallel safely

- Console state doesn't affect subsequent tests

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 58: Commented Test Cases for Future Expansion

**As a** developer  
**I want** placeholder commented test cases in Theory tests  
**So that** I can easily identify areas for future test expansion

### Acceptance Criteria:

- Commented InlineData cases indicate planned tests:

  - //\[InlineData("Dragon", "")\] - expects empty on timeout/failure

  - //\[InlineData("Dragon\nGoat\nFish", "")\] - all invalid inputs

- Comments serve as test backlog/TODO

- Indicates awareness of edge cases not yet handled

- Easy to uncomment and implement later

- Documents test coverage gaps

**Priority:** Low  
**Story Points:** 1

------------------------------------------------------------------------

## User Story 59: Type Conversion Testing

**As a** developer  
**I want** tests that verify string-to-int parsing of LimbCount  
**So that** I can ensure numeric data is correctly stored and retrieved

### Acceptance Criteria:

- TestLoadAnimals parses LimbCount strings to integers

- Uses int.Parse(animals\[0\]\["LimbCount"\])

- Verifies Fido has 4 limbs (integer comparison)

- Verifies Fifi has 5 limbs (integer comparison)

- Validates dictionary stores numeric data as strings

- Confirms conversion logic works correctly

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## Technical Notes

### Testing Architecture:

- **Framework**: xUnit (industry-standard .NET testing framework)

- **Pattern**: Arrange-Act-Assert for test structure

- **Isolation**: Console I/O redirection for interactive method testing

- **Parameterization**: Theory tests for multiple scenarios

- **Coverage**: Core business logic and validation methods

### Test Categories:

1.  **Data Loading Tests**: Verify initial state

2.  **Validation Tests**: Ensure business rules enforced

3.  **Input Handling Tests**: Test interactive console methods

4.  **Edge Case Tests**: Null, empty, invalid inputs

### Quality Improvements:

- Automated regression detection

- Documentation through tests (test names describe behavior)

- Confidence in refactoring (tests verify behavior preservation)

- Executable specifications for business rules

- Foundation for Test-Driven Development (TDD)

### Test Coverage Analysis:

- LoadAnimals: Fully tested

- IsNumeric: Comprehensive edge cases

- GetAndValidateAttributeForAdding: Valid and invalid flows

- Not yet tested: AddAnimal, EditAnimal, RemoveAnimal, FeedAnimal,
  AnimalSelector

- 📝 Future work: Expand test coverage to untested methods

### Best Practices Demonstrated:

- Consistent naming convention (Test{MethodName}With{Scenario})

- Comprehensive edge case coverage

- Use of modern xUnit features (Theory, InlineData)

- Clear test documentation through comments

- Isolated test execution

- Placeholder comments for future expansion
