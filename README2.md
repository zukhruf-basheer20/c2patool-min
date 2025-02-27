# c2patool CLI Signing Tool

c2patool is an open‑source command‑line tool for embedding C2PA metadata and digitally signing assets. This README describes how to clone the repository, build the tool from source, and run it on Windows, Linux, and macOS.

---

## Prerequisites

- **Git:** Make sure Git is installed on your system.
- **Rust & Cargo:** Install via [rustup](https://rustup.rs/).  

For MacOS 
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
___
Verify installation by running:
```bash
  rustc --version
  cargo --version
```

## Cloning the Repository
Open a terminal (or Command Prompt/PowerShell on Windows) and run:
```
git clone https://github.com/contentauth/c2patool.git
cd c2patool
```

---

## Building c2patool
### For MacOS/Linux 
1. Open a terminal in the cloned repository.
2. Build the project in release mode:
```
cargo build --release
```
3. The resulting binary will be located in the target/release directory.

### For Windows

1. Open Command Prompt or PowerShell in the cloned repository.
2. Build the project in release mode:
```
cargo build --release
```
3. The resulting binary (c2patool.exe) will be located in the target\release directory.

___

## Running c2patool

### Display Help Information

To view the help text, run the following command:

##### 1. Linux/macOS:
```
./target/release/c2patool --help
```
```
cargo run -- path/to/image --manifest path/to/maniest/schemas --output signed/image/name/png;
cargo run -- sample/image.jpg --manifest schemas/manifest-definition.json --output signed/image_signed.jpg;
```
##### 2. Windows:
```
.\target\release\c2patool.exe --help
```

___

### Signing an Asset

The CLI tool expects a command similar to the following:

###### phpTemplate 
```
c2patool sign --certificate <CERT_DATA> --private-key <PRIVATE_KEY_DATA> <input_file> <output_file>
```

Replace <CERT_DATA> and <PRIVATE_KEY_DATA> with your actual certificate and private key values, and specify your input and output file paths.

##### 1. Linux/macOS:
```
./target/release/c2patool sign --certificate "YOUR_CERT_DATA" --private-key "YOUR_PRIVATE_KEY_DATA" input.jpg output.jpg
```
##### 2. Windows:
```
.\target\release\c2patool.exe sign --certificate "YOUR_CERT_DATA" --private-key "YOUR_PRIVATE_KEY_DATA" input.jpg output.jpg
```
## Adding c2patool to Your PATH
### Linux and macOS

To run c2patool from any directory, copy the binary to a directory in your PATH (for example, ```/usr/local/bin```):

```
sudo cp target/release/c2patool /usr/local/bin/
```

### Windows 
You can either:

1. Copy c2patool.exe from the target\release folder to a folder already in your system PATH,
or
2. Add the target\release folder to your system PATH via the Environment Variables settings in Windows.

To test, open a new Command Prompt or PowerShell window and run:

```
c2patool --help
```