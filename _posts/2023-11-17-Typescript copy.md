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

{% highlight %}
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
