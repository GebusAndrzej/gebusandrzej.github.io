---
layout: post
title: TypeScript
categories: [content, typescript]
---

TypeScript things

### table of contents

- [Breadth-first search](#breadth-first-search)

---

# Breadth-first search

preOrderTraversal using generator

{% highlight js %}
function* preOrderTraversal(node: Node): IterableIterator<Node> {
    yield node;
    if (node.children.length) {
        for (const child of node.children) {
            yield* preOrderTraversal(child);
        }
    }
}

export function find(tree: Node, key: string): Node | undefined {
    for (const node of preOrderTraversal(tree)) {
        if (node.id === key) return node;
    }

    return undefined;
}

{% endhighlight %}

---

# Type Transformations

### Camel Case Object Keys
> NOTE: if u need this, something went wrong

{% highlight ts %}

type CamelCase<S extends string> = S extends `${infer P1}_${infer P2}${infer P3}`
    ? `${Lowercase<P1>}${Uppercase<P2>}${CamelCase<P3>}`
    : Lowercase<S>;

type SomeTypeCamelCased =
    { [key in keyof SomeType as CamelCase<key>]: SomeType[key] };

{% endhighlight %}
