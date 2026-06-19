# Edge case: missing mark and empty student set

- Identified edge case: A student may be created without providing a `mark`, and the `/stats` endpoint may be called when there are no students in the database.
- Implementation:
	- `POST /students` defaults a missing `mark` to `0` and validates that any provided `mark` is an integer between `0` and `100`.
	- `GET /stats` returns `count: 0`, `average: 0`, `min: 0`, and `max: 0` when there are no students, avoiding a divide-by-zero or null response.