# Complete JXA (JavaScript for Automation) Guide for OmniFocus

This guide consolidates all JXA learnings and best practices for working with OmniFocus automation.

## Table of Contents
1. [Basic Concepts](#basic-concepts)
2. [Null and Missing Values](#null-and-missing-values)
3. [Whose Clauses and Limitations](#whose-clauses-and-limitations)
4. [Common Patterns](#common-patterns)
5. [Workarounds](#workarounds)
6. [API Reference](#api-reference)

## Basic Concepts

### Property Access
All properties in JXA must be accessed as method calls:
```javascript
// ❌ Wrong
const name = task.name;

// ✅ Correct
const name = task.name();
```

### Object References
JXA returns proxy objects, not plain JavaScript objects:
```javascript
const task = doc.flattenedTasks()[0];
// task is a JXA proxy object, not a plain object
```

## Null and Missing Values

### The Missing Value Problem
JXA represents missing/null values with a special "missing value" type:
```javascript
const dueDate = task.dueDate();
if (dueDate === null) // ❌ Won't work for missing values
if (dueDate.toString() === 'missing value') // ✅ Works
```

### Safe Access Pattern
```javascript
function safeGet(accessor, defaultValue = null) {
  try {
    const value = accessor();
    return (value && value.toString() !== 'missing value') ? value : defaultValue;
  } catch {
    return defaultValue;
  }
}
```

## Whose Clauses and Limitations

### Basic Syntax
```javascript
// Find tasks by property
doc.flattenedTasks.whose({ completed: false })
```

### String Operators (use underscore prefix)
- `_contains`: substring search
- `_beginsWith`: prefix matching  
- `_endsWith`: suffix matching

### Date Operators (use symbols, NOT underscores)
- `>`: greater than
- `<`: less than
- `>=`: greater than or equal
- `<=`: less than or equal

### Limitations
1. No "not null" queries: `{dueDate: {_not: null}}` ❌
2. No complex AND/OR combinations
3. Performance degrades with large datasets (2000+ items)
4. Some operators cause timeouts

## Common Patterns

### Task Lookup by ID
```javascript
const task = doc.flattenedTasks.whose({id: taskId})[0];
```

### Get Available Tasks
```javascript
const available = doc.flattenedTasks.whose({
  completed: false,
  effectivelyCompleted: false
});
```

### Project Tasks
```javascript
const project = doc.flattenedProjects.whose({id: projectId})[0];
const tasks = project.tasks();
```

## Workarounds

### For Complex Queries
Use post-filtering instead of whose clauses:
```javascript
const allTasks = doc.flattenedTasks();
const filtered = allTasks.filter(task => {
  // Complex logic here
  return task.completed() === false && 
         task.dueDate() && 
         task.dueDate().toString() !== 'missing value';
});
```

### For Performance
1. Limit result sets early
2. Cache frequently accessed data
3. Use pagination for large queries

## API Reference

### Key Objects
- `Application('OmniFocus')`: Main application object
- `doc.flattenedTasks`: All tasks array
- `doc.flattenedProjects`: All projects array  
- `doc.flattenedTags`: All tags array

### Common Properties
All accessed as methods: `name()`, `note()`, `completed()`, `flagged()`, etc.

### Date Handling
Dates are returned as Date objects or 'missing value':
```javascript
const date = task.dueDate();
if (date && date.toString() !== 'missing value') {
  // Valid date
}
```

---

*This guide consolidates learnings from extensive JXA exploration with OmniFocus 4.6+*
