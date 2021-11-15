# Rust

[Retour à l'accueil](./../README.md)

- [Rust](#rust)
	- [Variables](#variables)
		- [Mutabilité](#mutabilité)
		- [Shadowing](#shadowing)
		- [Scalar types](#scalar-types)
		- [Compound types](#compound-types)


___
```bash
# Installation de Rust et de Rustup sur bash
$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
# désinstallation de Rust et de rustup
rustup self uninstall
```



**Rustc : compilateur Rust**
```bash
rustc --version

rustc fichier.rs # crée un exécutable 
./fichier # exécution
```




**Rustup : outil de versionnage pour Rust**
```bash
rustup --version
rustup update
rustup doc
```





**Cargo : gestionnaire de paquets Rust**
```bash
cargo --version
cargo new mon-projet # génère dossiers, main.rs et Cargo.toml
cargo build # compile le projet
cargo build --release # compile en optimisant
cargo run # compile puis exécute
cargo check # précise si le projet fonctionne
```





## Variables

### Mutabilité

Par défaut les variables ne sont pas mutables.
```rust
fn main() {
	let x = 5; //non mutable
	let mut y = x; //mutable
	y = 1;
	println!("x = {}, y = {}", x, y); // affiche 5 et 1
}
```
✍🏻 Une variable mutable ne peut pas changer de type.


### Shadowing

```rust
fn main() {
	let x = 5;
	let x = x + 1; // x est redéfinie
}
```

### Scalar types

```rust	
fn main() {
	let x: i32 = 5;
	let y: f64 = 5.0;
	let z: bool = true;
	let a: char = 'a';
	let b: String = String::from("Hello");
}
```

✍🏻  `char` s'écrit avec un apostrophe tandis que `String` s'écrit avec des guillemets.

### Compound types

```rust	
fn main() {
	//tuple
	let t: (i32, f64, u8) = (5, 6.0, 7);
	let (x, y, z) = t;

	//array
	let a: [i32; 5] = [1, 2, 3, 4, 5];
	let v = a[0];
}
```