# Flyweight Design Pattern

The Flyweight design pattern is a structural design pattern that provides a way to use objects in large numbers when a simple repeated representation would use an unacceptable amount of memory. It's particularly useful when you need to spawn a large number of similar objects.

In the provided Go code, the Flyweight pattern is used to manage `Team` objects.

## Code Explanation
### Constants

```go
const (
    TEAM_A = iota
    TEAM_B
)
```

These constants represent the two types of teams that can be created.

### Structs

Several structs are defined: `Player`, `HistoricalData`, `Team`, and `Match`. These represent different entities in a football league.

### Flyweight Factory

The `teamFlyweightFactory` struct is the Flyweight Factory. It maintains a map of already created teams.

```go
type teamFlyweightFactory struct {
    createdTeams map[int]*Team
}
```

### Factory Methods

The `getTeamFactory` function is a simple factory method that creates a new `Team` based on the input.

```go
func getTeamFactory(team int) Team {
    //...
}
```

The `NewTeamFactory` function creates a new instance of `teamFlyweightFactory`.

```go
func NewTeamFactory() teamFlyweightFactory {
    //...
}
```

### Flyweight Methods

The `GetTeam` method in `teamFlyweightFactory` checks if a team already exists in the `createdTeams` map. If it does, it returns the existing team. If not, it creates a new team, adds it to the map, and then returns it. This is where the Flyweight pattern is implemented.

```go
func (t *teamFlyweightFactory) GetTeam(teamName int) *Team {
    //...
}
```

The `GetNumberOfObjects` method returns the number of teams created.

```go
func (t *teamFlyweightFactory) GetNumberOfObjects() int {
    //...
}
```

## Usage

The Flyweight pattern is used when you need to create a large number of similar objects. In this case, it's used to manage `Team` objects in a football league. By using the Flyweight pattern, you can reduce memory usage by sharing common parts of the state between multiple objects instead of keeping all of the data in each object.
