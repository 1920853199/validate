# CHANGE LOG

## V2 - TODO

- [ ] inner validators always use reflect.Value as param. 
  - `Enum(val, enum interface{})` -> `ReflectVEnum(val, enum interface{})`

- can register custom type
- use sync.Pool for optimize create Validation.

```go
// Validation definition
type Validation struct {
	// for optimize create instance. refer go-playground/validator
	v *Validation
	pool *sync.Pool
    
    // ...
}

	v.pool = &sync.Pool{
		New: func() interface{} {
			return &Validation{
				v: v,
			}
		},
	}
```

- all data operate move to DataSource

```go
type DataFace interface {
	BindStruct() error
	SafeVal(field string) interface{}

...
}

```