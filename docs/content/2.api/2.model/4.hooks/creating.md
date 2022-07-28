---
title: 'creating()'
description: 'This hook is triggered when a record is creating'
---

## Usage

````js
class User extends Model {
  static entity = 'users'

  static fields () {
    return {
      userId: this.attr(null),
      published: this.attr(false)
    }
  }

  static creating (model) {
      // change values before saving
    model.published = true
    if (model.userId === 2) {
        // prevent model with userId 2 being saved in the store
        return false
    }
  }
}
````

## Typescript Declarations
````ts
export interface BeforeHook<M extends Model = Model> {
  (model: M): void | boolean
}

const creating: BeforeHook = () => {}
````