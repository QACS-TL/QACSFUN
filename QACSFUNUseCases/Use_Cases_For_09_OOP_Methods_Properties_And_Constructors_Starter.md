# Agile User Stories for Zoo Tycoon Animal Management System

## 09 OOP Methods Properties and Constructors – Starter

### Object-Oriented Programming Enhanced Version

------------------------------------------------------------------------

## User Story 60: Animal Class with Encapsulation

**As a** developer  
**I want** animals represented as objects with private fields and public
properties  
**So that** data is properly encapsulated and validated at the class
level

### Acceptance Criteria:

- Animal class with private fields: \_name, \_colour, \_type,
  \_limbCount, \_id

- Public properties: Name, Colour, Type, LimbCount, Id

- Properties enforce validation rules in setters

- Invalid values default to safe values (e.g., "Anonymous", "BROWN",
  "ANIMAL", 0)

- Static allowed lists defined within Animal class

**Priority:** High  
**Story Points:** 8

------------------------------------------------------------------------

## User Story 61: Auto-Incrementing Animal IDs

**As a** zoo administrator  
**I want** each animal to receive a unique sequential ID automatically  
**So that** I can track and reference individual animals consistently

### Acceptance Criteria:

- Static id property tracks next available ID

- GenerateNewId() method increments and returns new ID

- Constructor accepts optional id parameter for data loading

- If no id provided, automatically generates new one

- IDs formatted with 3 digits in ToString() (e.g., "005")

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 62: Animal Constructor with Named Parameters

**As a** developer  
**I want** to create animals using named parameters with defaults  
**So that** object creation is flexible and self-documenting

### Acceptance Criteria:

- Constructor signature: Animal(int? id = null, string name =
  "Anonymous", string colour = "Brown", int limbCount = 4, string type =
  "Animal")

- All parameters optional with sensible defaults

- Named parameter syntax supported: new Animal(name: "Fido", type:
  "DOG")

- Parameters in logical order

- Nullable id for optional explicit ID assignment

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 63: Property-Level Validation in Setters

**As a** developer  
**I want** validation logic embedded in property setters  
**So that** invalid data is automatically corrected when assigned

### Acceptance Criteria:

- Name setter: names \< 2 chars default to "Anonymous"

- Colour setter: invalid colours default to "BROWN"

- Type setter: invalid types default to "ANIMAL"

- LimbCount setter: negative values default to 0

- Validation uses expression-bodied members where appropriate

**Priority:** High  
**Story Points:** 5

------------------------------------------------------------------------

## User Story 64: Static Validation Collections in Animal Class

**As a** developer  
**I want** allowed species and colours defined in the Animal class  
**So that** validation rules are co-located with the data model

### Acceptance Criteria:

- AllowedColours: static readonly HashSet in Animal class

- AllowedSpecies: static HashSet in Animal class

- Same values as Program class versions

- Property setters reference these collections

- Centralized source of truth for valid values

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 65: Animal Behaviour Methods

**As a** developer  
**I want** animals to have Behaviour methods (Eat, Move)  
**So that** animals can perform actions appropriate to their type

### Acceptance Criteria:

- Eat(string food) returns formatted message

- Move(string direction, int distance) returns formatted message

- Methods use animal's own properties (Name, Type, LimbCount)

- Return values are strings for display flexibility

- Methods demonstrate encapsulation of Behaviour with data

**Priority:** Medium  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 66: ToString Override for Formatted Display

**As a** developer  
**I want** Animal.ToString() to provide formatted output  
**So that** animals can be easily displayed in consistent format

### Acceptance Criteria:

- Override ToString() method

- Format: "Id: {Id:D3}, Name: {Name}, Species: {Type}, Colour: {Colour},
  Limb Count: {LimbCount}"

- ID formatted with 3 digits (D3 format specifier)

- Uses "Species" label for Type field

- Returns complete animal state in one string

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 67: Type Migration from Dictionary to Animal Objects

**As a** developer  
**I want** to replace Dictionary\<string,string\> with Animal objects  
**So that** the codebase benefits from type safety and IntelliSense

### Acceptance Criteria:

- LoadAnimals returns List\<Animal\> instead of
  List\<Dictionary\<string,string\>\>

- All method signatures updated to accept List\<Animal\>

- Constructor calls replace dictionary initialization

- Property access replaces dictionary key access

- Compile-time type checking for all animal operations

**Priority:** High  
**Story Points:** 8

------------------------------------------------------------------------

## User Story 68: Property Access Replacing Dictionary Lookups

**As a** developer  
**I want** to access animal attributes via properties instead of
dictionary keys  
**So that** code is clearer and errors are caught at compile time

### Acceptance Criteria:

- animals\[i\]\["Name"\] becomes animals\[i\].Name

- animals\[i\]\["Type"\] becomes animals\[i\].Type

- ani\["Colour"\] becomes ani.Colour

- ani\["LimbCount"\] becomes ani.LimbCount

- IntelliSense provides property suggestions

**Priority:** High  
**Story Points:** 5

------------------------------------------------------------------------

## User Story 69: Comprehensive Unit Test Suite

**As a** developer  
**I want** automated tests for all critical functionality  
**So that** I can verify code correctness and prevent regressions

### Acceptance Criteria:

- Separate test project (ZooTycoonTests) using xUnit

- ProgramTests.cs tests Program class methods

- AnimalTests.cs tests Animal class Behaviour

- Tests cover: object creation, validation, LoadAnimals, IsNumeric

- Tests use Arrange-Act-Assert pattern

**Priority:** High  
**Story Points:** 8

------------------------------------------------------------------------

## User Story 70: Animal Creation and Validation Tests

**As a** developer  
**I want** tests verifying Animal object creation and validation  
**So that** I ensure objects are constructed correctly

### Acceptance Criteria:

- TestCreateAnimal: verifies single animal creation

- TestCreateTwoAnimals: verifies multiple animals with unique IDs

- TestCreateAnimalWithBadValues: verifies default fallback values

- Tests reset static id counter for consistency

- Tests verify ToString() output format

**Priority:** High  
**Story Points:** 5

------------------------------------------------------------------------

## User Story 71: Animal Behaviour Tests

**As a** developer  
**I want** tests for Eat() and Move() methods  
**So that** I verify animal Behaviours produce correct output

### Acceptance Criteria:

- TestEat: verifies Eat() message format

- TestMove: verifies Move() message format with direction/distance

- Tests verify methods use animal's own properties

- Tests check exact string formatting

- Tests demonstrate method contracts

**Priority:** Medium  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 72: Program Method Unit Tests

**As a** developer  
**I want** tests for Program helper methods  
**So that** I verify validation and data loading logic

### Acceptance Criteria:

- TestLoadAnimals: verifies all 4 animals loaded correctly

- TestIsNumeric: tests valid numbers, invalid strings, null, empty

- TestGetAndValidateAttributeForAdding: tests valid input

- Tests use StringReader/StringWriter for console I/O mocking

- Theory-based tests for multiple input scenarios

**Priority:** High  
**Story Points:** 5

------------------------------------------------------------------------

## User Story 73: Theory-Based Parameterized Tests

**As a** developer  
**I want** parameterized tests using xUnit Theory attribute  
**So that** I can test multiple scenarios efficiently

### Acceptance Criteria:

- \[Theory\] attribute for parameterized tests

- \[InlineData\] for test case parameters

- TestGetAndValidateAnimalAttributeWithValidTypes tests multiple inputs

- First parameter is input string, second is expected result

- Tests validation retry logic (e.g., "Dragon\nGoat\nBird" → "Bird")

**Priority:** Medium  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 74: Console I/O Test Mocking

**As a** developer  
**I want** to mock console input/output in tests  
**So that** I can test interactive methods without user interaction

### Acceptance Criteria:

- StringReader mocks Console.ReadLine() input

- StringWriter captures Console.WriteLine() output

- Console.SetIn(input) redirects standard input

- Console.SetOut(output) redirects standard output

- Tests verify input validation loops

**Priority:** Medium  
**Story Points:** 4

------------------------------------------------------------------------

## User Story 75: Static ID Reset for Test Isolation

**As a** developer  
**I want** tests to reset Animal.id counter  
**So that** tests produce consistent, predictable IDs

### Acceptance Criteria:

- Each test sets Animal.id = 4 before creating animals

- First animal created gets ID "005"

- Second animal gets ID "006"

- Tests don't interfere with each other

- Predictable test assertions for ID values

**Priority:** Medium  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 76: Expression-Bodied Property Members

**As a** developer  
**I want** to use expression-bodied members for simple properties  
**So that** code is concise and modern

### Acceptance Criteria:

- LimbCount getter: get =\> \_limbCount;

- LimbCount setter: set =\> \_limbCount = value \< 0 ? 0 : value;

- Type getter: get =\> \_type;

- Applies C# 6.0+ syntax for getters and C# 7.0+ for setters

- Reduces boilerplate code

**Priority:** Low  
**Story Points:** 2

------------------------------------------------------------------------

## User Story 77: Convert.ToInt32 for Type Conversion

**As a** developer  
**I want** to use Convert.ToInt32 instead of int.Parse  
**So that** type conversions are more robust

### Acceptance Criteria:

- AddAnimal uses Convert.ToInt32(limbCount)

- EditAnimal uses Convert.ToInt32(limbCount)

- Handles null values more gracefully than Parse

- Consistent with best practices

- Works with validated numeric strings

**Priority:** Low  
**Story Points:** 1

------------------------------------------------------------------------

## User Story 78: Separated Test Project Structure

**As a** developer  
**I want** tests in a separate project from production code  
**So that** I maintain clean architecture and deployment separation

### Acceptance Criteria:

- Solution contains two projects: CSharpZooTycoon and ZooTycoonTests

- ZooTycoonTests references CSharpZooTycoon project

- xUnit framework installed in test project

- Test project contains only test files

- Production project contains only application code

**Priority:** High  
**Story Points:** 3

------------------------------------------------------------------------

## User Story 79: Fact vs Theory Test Attributes

**As a** developer  
**I want** to use appropriate test attributes for different test types  
**So that** tests are properly categorized and executed

### Acceptance Criteria:

- \[Fact\] for single-scenario tests

- \[Theory\] with \[InlineData\] for multi-scenario tests

- Each Fact test runs once

- Each Theory test runs once per InlineData row

- Clear distinction between test types

**Priority:** Low  
**Story Points:** 1

## User Story 70: Readonly Static Collections

**As a** developer  
**I want** AllowedColours to be readonly static  
**So that** the collection cannot be modified after initialization

### Acceptance Criteria:

- AllowedColours declared as static readonly HashSet\<string\>

- AllowedSpecies declared as static HashSet\<string\> (mutable for
  testing)

- Readonly prevents accidental modification

- Initialized with collection initializer

- Enforces immutability where appropriate

**Priority:** Low  
**Story Points:** 1

------------------------------------------------------------------------

## Technical Notes

### Major Architectural Changes:

- **Paradigm Shift**: Dictionary-based → Object-Oriented Programming

- **Type Safety**: Compile-time checking via strongly-typed Animal class

- **Encapsulation**: Private fields with validated public properties

- **Behaviour**: Methods encapsulate animal-specific actions

- **Testing**: Comprehensive automated test coverage

- **Project Structure**: Multi-project solution with test isolation

### OOP Principles Demonstrated:

- **Encapsulation**: Private fields, public properties, validation in
  setters

- **Abstraction**: Animal class abstracts data and Behaviour

- **Data Hiding**: Internal validation logic hidden from consumers

- **Single Responsibility**: Animal manages its own validation

### Testing Strategy:

- **Unit Tests**: Individual method/property testing

- **Integration Tests**: LoadAnimals tests full object creation

- **Parameterized Tests**: Theory-based tests for multiple scenarios

- **I/O Mocking**: Console redirection for testable interactive code

- **AAA Pattern**: Arrange-Act-Assert structure throughout

### Code Quality Improvements:

- **IntelliSense Support**: Property access provides autocomplete

- **Compile-Time Safety**: Invalid property names caught before runtime

- **Self-Documenting**: Property names clearer than dictionary keys

- **Refactoring Support**: Rename refactoring works across codebase

- **Debugger Friendly**: Object properties visible in debugger

### Migration Impact:

- All CRUD operations updated for Animal objects

- Property access replaces dictionary key lookups throughout

- ToString() provides consistent formatting

- Validation now happens at two levels (UI + Model)

- Tests verify both layers work correctly

This represents a **significant architectural milestone** -
transitioning from procedural string manipulation to proper
object-oriented design with automated testing.
