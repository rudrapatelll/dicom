<p align="center">
  <img src="https://suyashkumar.com/assets/img/magnetic-resonance.png" width="125px"/>
  <h3 align="center">dicom</h3>
  <p align="center">High Performance Golang DICOM Medical Image Parser</p>
  <p align="center"> 
    <a href="https://github.com/suyashkumar/dicom/actions"><img src="https://github.com/suyashkumar/dicom/workflows/build/badge.svg" /></a> 
    <a href="https://godoc.org/github.com/suyashkumar/dicom"><img src="https://godoc.org/github.com/suyashkumar/dicom?status.svg" alt="" /></a>
    <a href="https://goreportcard.com/report/github.com/suyashkumar/dicom"><img src="https://goreportcard.com/badge/github.com/suyashkumar/dicom" alt=""></a> 
  </p>
</p>

v1.0 Release

This is a library and command-line tool to read, write, and generally work with DICOM medical image files in native Go. The goal is to provide a full-featured, high-performance, and readable DICOM parser for the Go community.

The v1.0 release of this library represents a significant evolution of the codebase, rewritten to be more canonical Go, better tested, and inclusive of new features and bugfixes.

Some notable features:
- Parse multi-frame DICOM imagery (both encapsulated and native pixel data)
- Channel-based streaming of Frames to a client as they are parsed out of the DICOM
- Cleaner Go Element and Dataset representations
- Better support for icon image sets in addition to primary image sets
- Write and encode Datasets back to DICOM files
- Enhanced testing and benchmarking support
- Modern, canonical Go implementation

## Usage
To use this in your Go project, import the dicom package. This repository supports Go modules and follows semantic versioning for releases. Typical usage is straightforward:

```go 
dataset, _ := dicom.ParseFile("testdata/1.dcm", nil) // See also: dicom.Parse which has a generic io.Reader API.

// Dataset will nicely print the DICOM dataset data out of the box.
fmt.Println(dataset)

// Dataset is also JSON serializable out of the box.
j, _ := json.Marshal(dataset)
fmt.Println(j)
```

More details about the package, additional examples, and APIs can be found in the documentation.

## CLI Tool
A CLI tool that uses this package to parse imagery and metadata out of DICOMs is provided in the cmd/dicomutil package. This tool can take in a DICOM and dump all the elements to STDOUT, in addition to writing out any imagery to the current working directory as PNGs or JPEGs (note: it does not perform automatic color rescaling by default).

### Installation
You can download the prebuilt binaries from the releases tab, or use the following command to download the binary at the command line:

```sh
wget -qO- "https://getbin.io/suyashkumar/dicom" | tar xvz
```

(This attempts to infer your OS and redirects wget to the latest release asset for your system).

### Usage
```
dicomutil -path myfile.dcm
```

Note: For some DICOMs with native pixel data, no automatic intensity scaling is applied yet. This can be applied in an external image viewer if needed.

### Build Manually
To build manually, ensure you have make and go installed. Clone this repo and run:

```sh
make
```

This will build the dicomutil binary and include it in a build/ folder in your current working directory.

You can also build it using Go directly:

```sh
go build -o dicomutil ./cmd/dicomutil
```

## History
This project has a rich history of development and community contribution.

### v0
The project began as a specialized fork of go-dicom to address maintenance needs and add several new capabilities, including multi-frame support, streaming parsing, updated APIs, and low-level parsing bug fixes.

### v1
For v1, the core library was redesigned and rewritten to improve efficiency and correctness. The architecture and APIs were updated to be more robust, with the majority of the rewrite focusing on performance and modern Go standards.

## Acknowledgements
* Segmed for their help with validation and other contributions to the library.
* Original go-dicom authors and contributors.
* Grailbio go-dicom - contributions from their fork have been integrated.
* GradientHealth for supporting early development work.
* Innolitics DICOM browser.
* DICOM Specification.
* Icons made by Freepik from www.flaticon.com, licensed by CC 3.0 BY.

## Maintainer
This project is maintained by Rudra Patel, an AI Automation Engineer with a focus on high-performance systems and medical imaging data.

* Name: Rudra Patel
* Email: patel.rudra@ufl.edu
* LinkedIn: https://www.linkedin.com/in/rudra-patel
* Professional Focus: AI Automation, Python, C++, and Scalable Engineering Solutions.