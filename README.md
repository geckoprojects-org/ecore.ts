> [!CAUTION]
> **This repository is deprecated and archived.**
> It is no longer maintained.

# EcoreTS

A TypeScript implementation of EMF (Eclipse Modeling Framework) Ecore metamodel.

This project is a fork of [soft.ts](https://github.com/masagroup/soft.ts).

## Overview

TSEcore provides a complete TypeScript port of the Eclipse Modeling Framework's Ecore metamodel, enabling model-driven development and metamodeling in TypeScript/JavaScript environments.

## Features

- **Complete Ecore Metamodel**: Full implementation of ECore classes including EClass, EAttribute, EReference, EDataType, EEnum, and more
- **Model Management**: EPackage, EFactory, and EPackageRegistry for organizing and managing metamodels
- **Object Model**: EObject, EObjectImpl, and DynamicEObjectImpl for runtime model instances
- **Resource Management**: EResource, EResourceSet with URI handling and conversion
- **Serialization**: Multiple codec implementations:
  - XML/XMI serialization (XMLCodec, XMICodec)
  - JSON serialization 
  - Custom codec support via ECodecRegistry
- **Collections**: Specialized collection types (EList, EMap) with notification support
- **Notifications**: Observer pattern implementation for model change tracking
- **Content Adapters**: EContentAdapter for hierarchical model observation
- **Extended Metadata**: Support for extended metadata and annotations
- **Type System**: Generic types, type parameters, and operations
- **Utilities**: Tree iteration, deep copy, deep equality, and other utility functions


## Installation

```bash
npm install
```

## Build

```bash
npm run build
```

## Project Structure

```
src/
├── index.ts              # Main exports
├── internal.ts           # Internal exports
├── EObject.ts            # Base model object
├── EClass.ts             # Metaclass definition
├── EPackage.ts           # Package/namespace container
├── EResource.ts          # Resource management
├── EResourceSet.ts       # Resource set management
├── *Codec.ts             # Serialization codecs
├── msgpack/              # MessagePack utilities
└── *.test.ts             # Test files
```

## Core Concepts

### EObject
The base interface for all model objects. Provides reflective API for accessing features, containers, and cross-references.

### EClass
Represents a class in the metamodel, defining attributes, references, and operations.

### EPackage
Container for organizing related metamodel elements with namespace support.

### EResource
Container for model instances with serialization/deserialization capabilities.

### Adapters & Notifications
Observer pattern implementation allowing tracking of model changes at fine-grained levels.

## Usage Example

```typescript
import {
    getEcoreFactory,
    getEcorePackage,
    EClass,
    EAttribute
} from 'tsecore';

// Create a metamodel
const factory = getEcoreFactory();
const ecorePackage = getEcorePackage();

const personClass = factory.createEClass();
personClass.setName('Person');

const nameAttr = factory.createEAttribute();
nameAttr.setName('name');
nameAttr.setEType(ecorePackage.getEString());
personClass.getEStructuralFeatures().add(nameAttr);
```



## Planned Features

- **EMF Delegates**:
  - SettingDelegate for volatile/derived/transient attributes
  - InvocationDelegate for operation implementation via annotations
  - ValidationDelegate for custom validation logic

## Development

This project uses:
- TypeScript 5.5.3
- CommonJS modules
- Strict type checking enabled
