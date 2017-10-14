# TypeScript

### Filip Štaffa

---

## Typescript

* Vytvořený v Microsoftu
* 5 let starý
* 3rd Most loved language on Stack Overflow (2017)
* 7th Most popular language on Stack Overflow (2017)
* 11th Most popular language on Github by pull requests (Octoverse 2017)

+++

## Typescript

* Staticky jazyk kompilovaný do JavaScriptu
* Superset JavaScriptu
* Rychlejší adopce nových featur

---

## Typy

* Volitelné
* Inferované


```typescript
	function caster(input: string) {
		const a = input as any
		const num = input as number // num je number
	}
```

+++

## Typy vs Netypy

```typescript
	function add(a: number, b: number) {
		return a + b // flow
	}

	function increment(a: number) {
		return add(a, {number: 1}) //typescript a flow s typy
	}

	function complex(a: number, b: number) {
		return add(a, increment(b)) //flow
	}

	should(complex(1, 2)).eql(4) // pouze testy, flow
```

+++

## Lepší tooling

* Statické typy
* Jazyková služba se základními refaktoringy

+++

## Strukturální typování

```typescript
	interface Book
	{
		name: string
	}
	interface Person
	{
		name: string
	}

	{ name: 'Filip' }
```
+++

## Union typy
```typescript
	type color = 'red' | 'green' | 'blue' // enum like

	interface Person {
		name: string,
		surname: string,
		middlename?: string // nullable, string nebo undefined
	}
```

+++

## Union typy
```typescript
	function padLeft(value: string, padding: string | number) {
		if (typeof padding === "number") {
			return Array(padding + 1).join(" ") + value;
		} else {
			return padding + value; // padding má typ string
		}
	}
```
+++

## keyof operátor

```typescript
	function getProperty<T, K extends keyof T>(obj: T, key: K) {
			return obj[key];  // Inferred type is T[K]
	}

	function setProperty<T, K extends keyof T>(obj: T, key: K, value: T[K]) {
			obj[key] = value;
	}

	let x = { foo: 10, bar: "hello!" };

	let foo = getProperty(x, "foo"); // number
	let bar = getProperty(x, "bar"); // string

	let oops = getProperty(x, "wargarbl"); // Error! "wargarbl" is not "foo" | "bar"

	setProperty(x, "foo", "string"); // Error!, string expected number
```

+++

### Type erasure

* Žádné námi definované typy v runtime
* Žádné námi definované typy v runtime

+++

## Typings
* .d.ts soubory
* Lze dodat externě
* De facto typový standard pro javascript
* Lze použít i JSDoc anotace

---

## Otázky
